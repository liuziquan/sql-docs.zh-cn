---
title: ISO 选项的影响 |微软文档
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ISO options (ODBC)
- ODBC applications, ISO options
- ODBC applications, statements
- SQL Server Native Client ODBC driver, ISO options
- statements [ODBC], ISO options
ms.assetid: 813f1397-fa0b-45ec-a718-e13fe2fb88ac
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: adf37d03f5ea4f06be4d58e60deca68e10d45abb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297929"
---
# <a name="effects-of-iso-options"></a>ISO 选项的作用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC 标准与 ISO 标准十分相似，而且 ODBC 应用程序期望 ODBC 驱动程序能提供标准行为。 为了使其行为更符合 ODBC 标准中定义的规则，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]本机客户端 ODBC 驱动程序始终使用它所连接的 SQL Server 版本中提供的任何 ISO 选项。  
  
 当[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]本机客户端 ODBC 驱动程序连接到 的[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例时，服务器检测到客户端正在使用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]本机客户端 ODBC 驱动程序，并设置多个选项。  
  
 驱动程序将自己发出这些语句；ODBC 应用程序不会做任何工作以请求它们。 设置这些选项可提高使用驱动程序的 ODBC 应用程序的可移植性，因为服务器的行为将与 ISO 标准保持一致。  
  
 基于 DB-Library 的应用程序通常不会打开这些选项。 在运行同一 SQL 语句时，在运行同一 SQL 语句时观察 ODBC 或数据库库客户端之间[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]不同行为的站点不应假定这指向本机客户端 ODBC 驱动程序的问题。 它们应首先在数据库库环境中重新运行语句，其设置选项与[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]本机客户端 ODBC 驱动程序使用的选项相同。  
  
 由于用户和应用程序可能会随时打开和关闭 SET 选项，存储过程和触发器的开发人员还应分别在上面列出的 SET 选项处于打开和关闭状态的情况下对其存储过程和触发器进行认真测试。 这可以确保存储过程和触发器正常工作，而无论特定连接在调用过程和触发器时打开哪些选项。 如果存储过程或触发器需要对这些选项之一进行特殊设置，则应该在触发器或存储过程的开始处发出 SET 语句。 此 SET 语句仅在触发器或存储过程执行期间保持有效；过程或触发器结束后，即会还原原始设置。  
  
 在连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例时，还会打开第四个 SET 选项 (CONCAT_NULL_YIELDS_NULL)。 如果[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]在数据源或[SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)上指定了 AnsiNPW_NO，则本机客户端 ODBC 驱动程序不会设置这些选项[。](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)  
  
 与前面提到的 ISO 选项一[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]样，如果在数据源或**SQLDriverConnect**上指定了引号 ID_NO，则本机客户端 ODBC 驱动程序不会打开QUOTED_IDENTIFIER**选项。**  
  
 若要使驱动程序能够了解 SET 选项的当前状态，ODBC 应用程序不应使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET 语句设置这些选项。 它们只应使用数据源或连接选项设置这些选项。 如果应用程序发出 SET 语句，则驱动程序可能会生成错误的 SQL 语句。  
  
## <a name="see-also"></a>另请参阅  
 [执行声明&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)   
 [SQLDriver连接](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)   
 [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)  
  
  
