---
title: bcp_bind |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_bind
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_bind function
ms.assetid: 6e335a5c-64b2-4bcf-a88f-35dc9393f329
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 711c82bb627ca9ad1620cf1e11fdbc9dfa5f4351
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "63140560"
---
# <a name="bcp_bind"></a>bcp_bind
  将程序变量中的数据绑定到表列，以便大容量复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
## <a name="syntax"></a>语法  
  
```  
  
RETCODE bcp_bind (  
HDBC   
hdbc  
,   
LPCBYTE   
pData  
,  
INT   
cbIndicator  
,  
DBINT   
cbData  
,  
LPCBYTE   
pTerm  
,  
INT   
cbTerm  
,  
INT   
eDataType  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>参数  
 *hdbc*  
 是启用大容量复制的 ODBC 连接句柄。  
  
 *pData*  
 指向已复制数据的指针。 如果*eDataType*为 SQLTEXT、SQLNTEXT、SQLXML、SQLUDT、SQLCHARACTER、SQLVARCHAR、SQLVARBINARY、SQLBINARY、SQLNCHAR 或 SQLIMAGE，则*PDATA*可以为 NULL。 空*pData*表示长数据值将使用[bcp_moretext](bcp-moretext.md)以区块形式[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]发送到。 如果与用户绑定字段相对应的列是一个 BLOB 列，则用户只应将*pData*设置为 NULL，否则**bcp_bind**将失败。  
  
 如果数据中存在指示符，这些指示符则在内存中直接显示在数据之前。 在这种情况下， *pData*参数指向指示器变量，并且大容量复制使用指示器的宽度（ *cbIndicator*参数）正确地处理用户数据。  
  
 *cbIndicator*  
 列数据的长度或 Null 指示符的长度（以字节为单位）。 有效指示器长度值是 0（不使用任何指示器时）、1、2、4 或 8。 指示符在内存中直接显示在任何数据之前。 例如，可以使用以下结构类型定义通过大容量复制将整数值插入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表：  
  
```  
typedef struct tagBCPBOUNDINT  
    {  
    int iIndicator;  
    int Value;  
    } BCPBOUNDINT;  
```  
  
 在本例中， *pData*参数将设置为结构的声明实例的地址，即 BCPBOUNDINT *iIndicator*结构成员的地址。 *CbIndicator*参数将设置为整数大小（sizeof （int））， *cbData*参数将再次设置为整数（sizeof （int））的大小。 若要向包含绑定列的 NULL 值的服务器大容量复制行，则应将实例的*iIndicator*成员的值设置为 SQL_NULL_DATA。  
  
 *cbData*  
 程序变量中数据的字节计数，不包括任何长度/Null 指示符或终止符的长度。  
  
 将*cbData*设置为 SQL_NULL_DATA 表示复制到服务器的所有行都包含该列的 NULL 值。  
  
 将*cbData*设置为 SQL_VARLEN_DATA 指示系统将使用字符串终止符或其他方法来确定复制的数据的长度。  
  
 对于固定长度的数据类型（如整数），该数据类型指示系统中的数据的长度。 因此，对于固定长度的数据类型， *cbData*可以安全地 SQL_VARLEN_DATA 或数据的长度。  
  
 对于[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]字符和二进制数据类型， *cbData*可以是 SQL_VARLEN_DATA、SQL_NULL_DATA、某些正值或0。 如果 SQL_VARLEN_DATA *cbData* ，则系统使用长度/空指示符（如果存在）或终止符序列来确定数据的长度。 如果同时提供指示符和终止符序列，系统则使用二者中可导致数据复制量最少的那一个。 如果*cbData* SQL_VARLEN_DATA，则列的数据类型为[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]字符或二进制类型，并且不指定长度指示符和终止符序列，系统将返回错误消息。  
  
 如果*cbData*为0或正值，则系统使用*cbData*作为数据长度。 但是，如果除正*cbData*值外，还提供了一个长度指示器或终止符序列，则系统将通过使用导致数据复制量最少的方法来确定数据长度。  
  
 *CbData*参数值表示数据的字节计数。 如果字符数据由 Unicode 宽字符表示，则正的*cbData*参数值表示字符数乘以每个字符的大小（以字节为单位）。  
  
 *pTerm*  
 指向标记该程序变量末尾的字节模式（如果有）的指针。 例如，ANSI 和 MBCS C 字符串通常采用 1 个字节的终止符 (\0)。  
  
 如果变量没有终止符，则将*pTerm*设置为 NULL。  
  
 您可以使用空字符串 ("") 将 C Null 终止符指定为程序变量终止符。 由于以 null 值结束的空字符串构成一个字节（终止符字节自身），因此请将*cbTerm*设置为1。 例如，若要指示*szName*中的字符串以 null 结尾并且应使用该终止符指示长度，请执行以下操作：  
  
```  
bcp_bind(hdbc, szName, 0,  
   SQL_VARLEN_DATA, "", 1,  
   SQLCHARACTER, 2)  
```  
  
 此示例的示例形式可能表示将15个字符从*szName*变量复制到绑定表的第二列：  
  
```  
bcp_bind(hdbc, szName, 0, 15,   
   NULL, 0, SQLCHARACTER, 2)  
```  
  
 大容量复制 API 根据需要执行 Unicode 到 MBCS 的字符转换。 确保终止符字节字符串和字节字符串的长度均已正确设置。 例如，若要指示*szName*中的字符串是 unicode 宽字符串，则由 unicode null 终止符值终止：  
  
```  
bcp_bind(hdbc, szName, 0,   
   SQL_VARLEN_DATA, L"",  
   sizeof(WCHAR), SQLNCHAR, 2)  
```  
  
 如果绑定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列是宽字符，则不会对[bcp_sendrow](bcp-sendrow.md)执行任何转换。 如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列为 MBCS 字符类型，将数据发送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时将执行从宽字符到多字节字符的转换。  
  
 *cbTerm*  
 存在于程序变量的终止符（如果有）中的字节计数。 如果变量没有终止符，则将*cbTerm*设置为0。  
  
 *eDataType*  
 程序变量的 C 数据类型。 程序变量中的数据转换为数据库列的类型。 如果该参数为 0，则不执行转换。  
  
 *EDataType*参数由 sqlncli.msi 中的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型标记进行枚举，而非 ODBC C 数据类型枚举器。 例如，您可以使用特定于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 SQLINT2 类型指定一个两个字节的整数：ODBC 类型的 SQL_C_SHORT。  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]在 deploymentdebugloglevel 中引入了*`eDataType`* 对 SQLXML 和 SQLUDT 数据类型标记的支持。  
  
 *idxServerCol*  
 数据复制的目标数据库表中的列的序号位置。 表中的第一列为列 1。 列的序号位置由[SQLColumns](../native-client-odbc-api/sqlcolumns.md)报告。  
  
## <a name="returns"></a>返回  
 SUCCEED 或 FAIL。  
  
## <a name="remarks"></a>备注  
 使用**bcp_bind**可以快速有效地将程序变量中的数据复制到中[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的表。  
  
 调用此或任何其他大容量复制函数之前调用[bcp_init](bcp-init.md) 。 调用**bcp_init**会设置[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]用于大容量复制的目标表。 在调用**bcp_init**以便与**bcp_bind**和[bcp_sendrow](bcp-sendrow.md)一起使用时，指示数据文件的**bcp_init** _szDataFile_参数设置为 NULL;**bcp_init**_eDirection_参数设置为 DB_IN。  
  
 为要复制**** 到的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]表中的每个列单独 bcp_bind 调用。 进行必要的**bcp_bind**调用后，调用**bcp_sendrow**将数据从程序变量发送到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 不支持重新绑定列。  
  
 每当你想[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]要提交已收到的行时，请调用[bcp_batch](bcp-batch.md)。 例如，对于每1000行或任何其他间隔，请调用一次**bcp_batch** 。  
  
 如果不再有要插入的行，请调用[bcp_done](bcp-done.md)。 如果没有这样做，会导致错误。  
  
 使用[bcp_control](bcp-control.md)指定的控件参数设置对**bcp_bind**行传输不起作用。  
  
 如果列的*pData*设置为 NULL，因为它的值将由对[bcp_moretext](bcp-moretext.md)的调用提供，则*EDATATYPE*设置为 SQLTEXT、SQLNTEXT、SQLXML、SQLUDT、SQLCHARACTER、SQLVARCHAR、SQLVARBINARY、SQLBINARY、SQLNCHAR 或 SQLIMAGE 的所有后续列也必须与*pData*设置为 NULL，并且它们的值还必须通过调用来`bcp_moretext`提供。  
  
 对于新的大值类型（如`varchar(max)`、 `varbinary(max)`或`nvarchar(max)`），可以在*SQLNCHAR*参数中使用 SQLCHARACTER、SQLVARCHAR、SQLVARBINARY、SQLBINARY 和 eDataType 作为类型指示符。  
  
 如果*cbTerm*不是0，则任何值（1、2、4或8）对于前缀（*cbIndicator*）都有效。 在这种情况[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]下，Native Client 将搜索终止符，计算与终止符（*i*）有关的数据长度，并将*cbData*设置为 "i" 的较小值和 "前缀" 的值。  
  
 如果*cbTerm*为0， *cbIndicator* （前缀）不为0，则*cbIndicator*必须是8。 此 8 个字节的前缀可以采用以下值：  
  
-   0xFFFFFFFFFFFFFFFF 表示字段为 Null 值。  
  
-   0xFFFFFFFFFFFFFFFE 被视为特殊前缀值，用于有效地向服务器成块发送数据。 带有此特殊前缀的数据的格式为：  
  
-   <SPECIAL_PREFIX> \<0 个或多个数据块> <ZERO_CHUNK> 位置：  
  
-   SPECIAL_PREFIX 为 0xFFFFFFFFFFFFFFFE  
  
-   DATA_CHUNK 是包含块区长度的 4 个字节的前缀，后跟在该 4 个字节的前缀中指定其长度的实际数据。  
  
-   ZERO_CHUNK 是全部由零组成的 4 个字节的值 (00000000)，指示数据结束。  
  
-   任何其他有效的 8 个字节的长度均被视为常规数据长度。  
  
 使用**bcp_bind**时调用[bcp_columns](bcp-columns.md)会导致错误。  
  
## <a name="bcp_bind-support-for-enhanced-date-and-time-features"></a>bcp_bind 对日期和时间增强功能的支持  
 有关用于日期/时间类型的*eDataType*参数所使用的类型的信息，请参阅[OLE DB 和 ODBC&#41;&#40;的增强日期和时间类型的大容量复制更改](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)。  
  
 有关详细信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。  
  
## <a name="example"></a>示例  
  
```  
#include sql.h  
#include sqlext.h  
#include odbcss.h  
// Variables like henv not specified.  
HDBC      hdbc;  
char         szCompanyName[MAXNAME];  
DBINT      idCompany;  
DBINT      nRowsProcessed;  
DBBOOL      bMoreData;  
char*      pTerm = "\t\t";  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source; return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bcp.   
if (bcp_init(hdbc, "comdb..accounts_info", NULL, NULL  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idCompany, 0, sizeof(DBINT), NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_bind(hdbc, (LPCBYTE) szCompanyName, 0, SQL_VARLEN_DATA,  
   (LPCBYTE) pTerm, strnlen(pTerm, sizeof(pTerm)), SQLCHARACTER, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
while (TRUE)  
   {  
   // Retrieve and process program data.   
   if ((bMoreData = getdata(&idCompany, szCompanyName)) == TRUE)  
      {  
      // Send the data.   
      if (bcp_sendrow(hdbc) == FAIL)  
         {  
         // Raise error and return.  
         return;  
         }  
      }  
   else  
      {  
      // Break out of loop.  
      break;  
      }  
   }  
  
// Terminate the bulk copy operation.  
if ((nRowsProcessed = bcp_done(hdbc)) == -1)  
   {  
   printf_s("Bulk-copy unsuccessful.\n");  
   return;  
   }  
  
printf_s("%ld rows copied.\n", nRowsProcessed);  
```  
  
## <a name="see-also"></a>另请参阅  
 [大容量复制函数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
