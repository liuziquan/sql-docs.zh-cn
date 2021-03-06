---
title: ODBC 更改处理字符转换
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 682a232a-bf89-4849-88a1-95b2fbac1467
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 82e9e3b1ed8487e864e91edfd3067f9fb97bbb71
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303828"
---
# <a name="odbc-driver-behavior-change-when-handling-character-conversions"></a>处理字符转换时 ODBC 驱动程序行为的变化
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]本机客户端 ODBC 驱动程序 （SQLNCLI11.dll） 更改了SQL_WCHAR* （NCHAR/NVARCHAR/NVARCHAR（MAX））和\*SQL_CHAR （CHAR/VARCHAR/NARCHAR（MAX）） 转换的方式。 使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client ODBC 驱动程序时，ODBC 函数（如 SQLGetData、SQLBindCol、SQLBindParameter）返回 (-4) SQL_NO_TOTAL 作为长度/指示符参数。 以前版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序返回的长度值可能不正确。  
  
## <a name="sqlgetdata-behavior"></a>SQLGetData 行为  
 许多 Windows 函数允许指定缓冲区大小为 0，且返回的长度为返回的数据大小。 以下模式对于 Windows 程序员很常见：  
  
```  
int iSize = 0;  
BYTE * pBuffer = NULL;  
GetMyFavoriteAPI(pBuffer, &iSize);   // Returns needed size in iSize  
pBuffer = new BYTE[iSize];   // Allocate buffer   
GetMyFavoriteAPI(pBuffer, &iSize);   // Retrieve actual data  
```  
  
 但是，不应在此方案中使用**SQLGetData。** 不应使用以下模式：  
  
```  
// bad  
int iSize = 0;  
WCHAR * pBuffer = NULL;  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)0x1, 0, &iSize);   // Get storage size needed  
pBuffer = new WCHAR[(iSize/sizeof(WCHAR)) + 1];   // Allocate buffer  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)pBuffer, iSize, &iSize);   // Retrieve data  
```  
  
 只能调用**SQLGetData**来检索实际数据块。 不受支持使用**SQLGetData**获取数据大小。  
  
 下面说明当您使用不正确的模式时驱动程序变化的影响。 此应用程序查询**varchar**列，并将绑定为 Unicode（SQL_UNICODE/SQL_WCHAR）：  
  
 查询：`select convert(varchar(36), '123')`  
  
```  
SQLGetData(hstmt, SQL_WCHAR, ....., (SQLPOINTER*) 0x1, 0 , &iSize);   // Attempting to determine storage size needed  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序版本|长度或指示符的结果|描述|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client 或更早版本|6|驱动程序错误地假定将 CHAR 转换为 WCHAR 可以通过长度 * 2 来实现。|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client（版本 11.0.2100.60）或更高版本|-4 (SQL_NO_TOTAL)|驱动程序不再假定从 CHAR 转换为 WCHAR 或 WCHAR 转换为 CHAR 是（\*乘法）2 或（除分）/2 操作。<br /><br /> 调用**SQLGetData**不再返回预期转换的长度。 驱动程序检测 CHAR 和 WCHAR 之间的转换并返回 (-4) SQL_NO_TOTAL 替代可能不正确的 *2 或 /2 行为。|  
  
 使用**SQLGetData**检索数据块。 （所示的伪代码：）  
  
```  
while( (SQL_SUCCESS or SQL_SUCCESS_WITH_INFO) == SQLFetch(...) ) {  
   SQLNumCols(...iTotalCols...)  
   for(int iCol = 1; iCol < iTotalCols; iCol++) {  
      WCHAR* pBufOrig, pBuffer = new WCHAR[100];  
      SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get original chunk  
      while(NOT ALL DATA RETREIVED (SQL_NO_TOTAL, ...) ) {  
         pBuffer += 50;   // Advance buffer for data retrieved  
         // May need to realloc the buffer when you reach current size  
         SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get next chunk  
      }  
   }  
}  
```  
  
## <a name="sqlbindcol-behavior"></a>SQLBindCol 行为  
 查询：`select convert(varchar(36), '1234567890')`  
  
```  
SQLBindCol(... SQL_W_CHAR, ...)   // Only bound a buffer of WCHAR[4] - Expecting String Data Right Truncation behavior  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序版本|长度或指示符的结果|描述|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client 或更早版本|20|**SQLFetch**报告数据右侧存在截断。<br /><br /> 长度为返回的数据长度而非存储的数据长度（假定 *2 CHAR 到 WCHAR 的转换对于符号可能不正确）。<br /><br /> 存储在缓冲区中的数据为 123\0。 缓冲区被保证为以 NULL 结束。|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client（版本 11.0.2100.60）或更高版本|-4 (SQL_NO_TOTAL)|**SQLFetch**报告数据右侧存在截断。<br /><br /> 长度指示 -4 (SQL_NO_TOTAL)，因为数据的其余部分未转换。<br /><br /> 缓冲区中存储的数据为 123\0。 - 缓冲区被保证为以 NULL 结束。|  
  
## <a name="sqlbindparameter-output-parameter-behavior"></a>SQLBindParameter（OUTPUT 参数行为）  
 查询：`create procedure spTest @p1 varchar(max) OUTPUT`  
  
 `select @p1 = replicate('B', 1234)`  
  
```  
SQLBindParameter(... SQL_W_CHAR, ...)   // Only bind up to first 64 characters  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序版本|长度或指示符的结果|描述|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client 或更早版本|2468|**SQLFetch**返回没有更多的可用数据。<br /><br /> **SQLMore 结果**不再返回可用的数据。<br /><br /> 长度指示从服务器返回的数据大小而非缓冲区中存储的数据大小。<br /><br /> 原始缓冲区包含 63 个字节和 NULL 结束符。 缓冲区被保证为以 NULL 结束。|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client（版本 11.0.2100.60）或更高版本|-4 (SQL_NO_TOTAL)|**SQLFetch**返回没有更多的可用数据。<br /><br /> **SQLMore 结果**不再返回可用的数据。<br /><br /> 长度指示 (-4) SQL_NO_TOTAL，因为数据的其余部分未转换。<br /><br /> 原始缓冲区包含 63 个字节和 NULL 结束符。 缓冲区被保证为以 NULL 结束。|  
  
## <a name="performing-char-and-wchar-conversions"></a>执行 CHAR 和 WCHAR 转换  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client ODBC 驱动程序提供几种执行 CHAR 和 WCHAR 转换的方式。 逻辑类似于操作 blob（瓦尔恰斯（最大）、nvarchar（max）、...）：  
  
-   当与**SQLBindCol**或**SQLBind参数**绑定时，数据将保存或截断到指定的缓冲区中。  
  
-   如果不绑定，可以使用**SQLGetData**和**SQLParamData**检索块中的数据。  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server Native Client 功能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
