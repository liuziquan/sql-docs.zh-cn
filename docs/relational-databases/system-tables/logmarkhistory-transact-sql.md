---
title: logmarkhistory （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- logmarkhistory
- logmarkhistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- logmarkhistory system table
ms.assetid: 5c1becc5-f34e-4869-bf69-dfafab684540
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0674bf993087b349d4e8b6f9947c65167e94df8e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68001801"
---
# <a name="logmarkhistory-transact-sql"></a>logmarkhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  每个已提交的标记事务在表中占一行。 该表存储在**msdb**数据库中。  
  

|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|标记事务出现的本地数据库。|  
|**mark_name**|**nvarchar(128)**|用户提供的标记事务名。|  
|**2008**|**nvarchar(255)**|用户提供的标记事务说明。 可以为 NULL。|  
|**user_name**|**nvarchar(128)**|执行标记事务的数据库用户名。 可以为 NULL。|  
|**lsn**|**数值（25，0）**|出现标记的事务记录的日志序列号。|  
|**mark_time**|**datetime**|提交标记事务的时间（本地时间）。|  
  
## <a name="see-also"></a>另请参阅  
 [将数据库还原到标记的事务 &#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)   
 [使用标记的事务一致地恢复相关的数据库的事务（完全恢复模式）](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)   
 [系统表 (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
