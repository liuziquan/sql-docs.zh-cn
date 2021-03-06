---
title: MSlogreader_history （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSlogreader_history_TSQL
- MSlogreader_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSlogreader_history system table
ms.assetid: 2e399fa1-3591-4c1c-96b7-7964fe82c7c4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9fbd2240bdeba50d8ae41bce8d3a8d58b28de036
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67907297"
---
# <a name="mslogreader_history-transact-sql"></a>MSlogreader_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSlogreader_history**表包含与本地分发服务器关联的日志读取器代理的历史记录行。 此表存储在分发数据库中。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|日志读取器代理的 ID。|  
|**runstatus**|**int**|运行状态：<br /><br /> 1 = 开始。<br /><br /> 2 = 成功。<br /><br /> 3 = 正在进行。<br /><br /> 4 = 空闲。<br /><br /> 5 = 重试。<br /><br /> 6 = 失败。|  
|**start_time**|**datetime**|开始执行作业的时间。|  
|**time**|**datetime**|记录消息的时间。|  
|**持续时间**|**int**|消息会话的持续时间（秒）。|  
|**提出**|**nvarchar(255)**|消息文本。|  
|**xact_seqno**|**varbinary （16）**|上次处理的事务序列号。|  
|**delivery_time**|**int**|传递第一个事务的时间。|  
|**delivered_transactions**|**int**|会话中传递的事务总数。|  
|**delivered_commands**|**int**|会话中传递的命令总数。|  
|**average_commands**|**int**|会话中传递的平均命令数。|  
|**delivery_rate**|**float**|平均每秒传递的命令数。|  
|**delivery_latency**|**int**|命令从进入发布数据库到进入分发数据库之间的滞后时间。 以毫秒为单位。|  
|**error_id**|**int**|**MSrepl_error**系统表中的错误的 ID。|  
|**标志**|**标志**|该表的时间戳列。|  
|**updateable_row**|**bit**|如果可以覆盖历史记录行，则设置为**1** 。|  
  
## <a name="see-also"></a>另请参阅  
 [Transact-sql&#41;&#40;复制表](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图 (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
