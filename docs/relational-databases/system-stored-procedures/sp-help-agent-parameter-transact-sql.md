---
title: sp_help_agent_parameter （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_help_agent_parameter
- sp_help_agent_parameter_TSQL
helpviewer_keywords:
- sp_help_agent_parameter
ms.assetid: 8fb4a9c3-19af-4a34-8004-572729ba3d15
author: stevestein
ms.author: sstein
ms.openlocfilehash: 398e1eebbb269fa1f1507725fefff820c5174f58
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771513"
---
# <a name="sp_help_agent_parameter-transact-sql"></a>sp_help_agent_parameter (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  返回[MSagent_parameters &#40;transact-sql&#41;](../../relational-databases/system-tables/msagent-parameters-transact-sql.md)系统表中配置文件的所有参数。 此存储过程可在运行代理的分发服务器的任意数据库中执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_help_agent_parameter [ [ @profile_id = ] profile_id ]  
```  
  
## <a name="arguments"></a>参数  
`[ @profile_id = ] profile_id`[MSagent_parameters &#40;transact-sql&#41;](../../relational-databases/system-tables/msagent-parameters-transact-sql.md)表中的配置文件的 ID。 *profile_id*为**int**，默认值为 **-1**，表示返回所有参数。  
  
## <a name="result-sets"></a>结果集  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|代理配置文件的 ID。|  
|**parameter_name**|**sysname**|参数的名称。|  
|**负值**|**nvarchar(255)**|参数的值。|  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功）或**1** （失败）  
  
## <a name="remarks"></a>备注  
 **sp_help_agent_parameter**在所有类型的复制中使用。  
  
## <a name="permissions"></a>权限  
 只有**sysadmin**固定服务器角色的成员或**replmonitor**固定数据库角色的成员才能**sp_help_agent_parameter**执行。  
  
## <a name="see-also"></a>另请参阅  
 [使用复制代理配置文件](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [sp_add_agent_parameter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
