---
title: 直接执行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, statements
- direct execution [ODBC]
- SQLExecDirect function
- statements [ODBC], direct execution
ms.assetid: fa36e1af-ed98-4abc-97c1-c4cc5d227b29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4e912ac2dd63fa63ce57647f0c4e95e6702a22ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68207067"
---
# <a name="direct-execution"></a>直接执行
  直接执行是最基本的语句执行方式。 应用程序将生成一个包含[!INCLUDE[tsql](../../../includes/tsql-md.md)]语句的字符串，然后使用**SQLExecDirect**函数提交它以执行执行。 当该语句到达服务器时，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将其编译为执行计划，然后立即运行该执行计划。  
  
 直接执行是在运行时生成和执行语句的应用程序的常用执行方式，它也是只需执行一次的语句的最有效方法。 对于许多数据库而言，它的缺点就是每次执行 SQL 语句都必须对该语句进行分析和编译，如果该语句多次执行，就会增加开销。  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 显著提高了在多用户环境中直接执行通常执行的语句的性能；如果将 SQLExecDirect 与参数标记配合用于通常执行的 SQL 语句，其效率可接近准备好的执行。  
  
 当连接到实例[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]时， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序使用[sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql)传输**SQLExecDirect**上指定的 SQL 语句或批处理。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]具有逻辑来快速确定使用**sp_executesql**执行的 SQL 语句或批处理是否与生成执行计划（已存在于内存中）的语句或批处理相匹配。 如果匹配，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 只需重用现有计划，而无需编译新计划。 这意味着，在包含多个用户的系统中，使用**SQLExecDirect**执行的常见 SQL 语句将受益于较早版本的[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中的存储过程所使用的许多计划重用权益。  
  
 仅当多个用户执行同一 SQL 语句或批处理时，才会从重用执行计划中受益。 请遵照以下编码约定，提高不同客户端执行的 SQL 语句的相似性，以便能够重用执行计划：  
  
-   不要在 SQL 语句中包括数据常量；改用绑定到程序变量的参数标记。 有关详细信息，请参阅[Using 语句参数](../using-statement-parameters.md)。  
  
-   使用完全限定对象名。 如果未限定对象名，则不重用执行计划。  
  
-   令应用程序连接尽量使用常用的一组连接和语句选项。 从具有某一组选项（如 ANSI_NULLS）的连接生成的执行计划不会重复用于具有另一组选项的连接。 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口的这些选项都具有相同的默认设置。  
  
 如果使用这些约定对使用**SQLExecDirect**执行的所有语句进行[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]编码，则可能会在出现机会时重新使用执行计划。  
  
## <a name="see-also"></a>另请参阅  
 [&#40;ODBC&#41;执行语句](executing-statements-odbc.md)  
  
  
