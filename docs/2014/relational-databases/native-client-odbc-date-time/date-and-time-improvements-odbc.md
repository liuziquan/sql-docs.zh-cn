---
title: 日期和时间改进（ODBC） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d56689bb045a6540bfdfbb9c7147dc34db110bde
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "63207003"
---
# <a name="date-and-time-improvements-odbc"></a>日期和时间改进 (ODBC)
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]引入了新的日期和时间数据类型。 本部分介绍如何将这些新类型作为本机客户端[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的扩展公开。 有关对新日期[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]和时间数据类型的 Native Client 支持的概述，请参阅[日期和时间改进](../native-client/features/date-and-time-improvements.md)。 有关演示 ODBC 日期/时间支持的示例，请参阅[使用日期和时间类型](../native-client-odbc-how-to/use-date-and-time-types.md)。  
  
 有关日期和时间数据类型的更多常规信息，请参阅[datetime &#40;transact-sql&#41;](/sql/t-sql/data-types/datetime-transact-sql)。  
  
## <a name="in-this-section"></a>本节内容  
 [针对 ODBC 日期/时间改进的数据类型支持](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 提供有关支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期和时间数据类型的 ODBC 类型的信息。  
  
 [Metadata &#40;ODBC&#41;](../../database-engine/dev-guide/metadata-odbc.md)  
 描述在实现参数描述符 (IPD) 和实现行描述符 (IRD) 字段中返回的信息，以及由 `SQLColumns` 和 `SQLProcedureColumns` 返回的列元数据。 还描述了由 `SQLGetTypeInfo` 返回的数据类型元数据。  
  
 [datetime 数据类型转换 &#40;ODBC&#41;](datetime-data-type-conversions-odbc.md)  
 描述如何在 datetime 值和 datetimeoffset 值之间进行转换。  
  
 [sql_variant 对日期和时间类型的支持](sql-variant-support-for-date-and-time-types.md)  
 描述用于获得增强的日期和时间功能的 SQL_VARIANT 函数支持。  
  
 [&#40;OLE DB 和 ODBC 的增强日期和时间类型的大容量复制&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 描述支持大容量复制操作的日期/时间增强功能。  
  
 [早期 SQL Server 版本的增强日期和时间类型行为 &#40;ODBC&#41;](enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 描述使用日期和时间增强功能的客户端应用程序与早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通信时的预期行为，以及使用早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 编译的客户端向支持日期和时间增强功能的服务器发送命令时的预期行为。  
  
 [ODBC API 对日期和时间增强功能的支持](odbc-api-support-for-enhanced-date-and-time-features.md)  
 列出了支持日期和时间增强功能的 ODBC 函数。  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
