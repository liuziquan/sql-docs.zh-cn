---
title: MSSQLSERVER_2546 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ca1a8af843d0183acd46a8b11e00427738d59d0e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "62868848"
---
# <a name="mssqlserver_2546"></a>MSSQLSERVER_2546
    
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|2546|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|DBCC_INDEX_MARKED_DISABLED|  
|消息正文|表 'OBJECT_NAME' 的索引 'INDEX_NAME' 已标记为禁用。 请重新生成该索引，以使之联机。|  
  
## <a name="explanation"></a>说明  
 指定的索引已标记为离线或禁用。 因此，不能检查该索引。  
  
## <a name="user-action"></a>用户操作  
 请使用 ALTER INDEX 重新生成索引。  
  
## <a name="see-also"></a>另请参阅  
 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)   
 [重新组织和重新生成索引](../indexes/indexes.md)  
  
  
