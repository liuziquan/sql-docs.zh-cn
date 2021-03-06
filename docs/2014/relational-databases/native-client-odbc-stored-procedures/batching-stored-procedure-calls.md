---
title: 批处理存储过程调用 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b50350006abba5085b11010f26aa88a89b07393f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68205492"
---
# <a name="batching-stored-procedure-calls"></a>批处理存储过程调用
  在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]适当时，NATIVE Client ODBC 驱动程序会自动将存储过程调用分批批处理到服务器。 只有在使用 ODBC CALL 转义序列时驱动程序才执行此操作；它并不为 [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE 语句执行此操作。 批处理存储过程调用可以减少到服务器的往返数目，因此可以显著提高性能。  
  
 在执行包含多个 ODBC CALL 转义序列的批处理时，驱动程序批处理对服务器的过程调用。 它还在绑定参数数组用于 ODBC CALL 转义序列时批处理过程调用。 例如，如果你使用按行或按列的参数绑定将包含五个元素的数组绑定到 ODBC CALL SQL 语句的参数，则在调用**SQLExecute**或**SQLExecDirect**时，驱动程序会向服务器发送包含五个过程调用的单个批处理。  
  
## <a name="see-also"></a>另请参阅  
 [运行存储过程](running-stored-procedures.md)  
  
  
