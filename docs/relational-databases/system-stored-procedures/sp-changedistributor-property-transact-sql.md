---
title: sp_changedistributor_property （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changedistributor_property_TSQL
- sp_changedistributor_property
helpviewer_keywords:
- sp_changedistributor_property
ms.assetid: 04f503a1-307c-4de0-bac6-e6e97d5b6940
author: stevestein
ms.author: sstein
ms.openlocfilehash: 18921fa57cfa203b0d8e5274caeb1e17c385405c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771303"
---
# <a name="sp_changedistributor_property-transact-sql"></a>sp_changedistributor_property (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  更改分发服务器的属性。 此存储过程在分发服务器上的任何数据库中执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_changedistributor_property [ [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>参数  
`[ @property = ] 'property'`给定分发服务器的属性。 *属性*为**sysname**，可以是下列值之一。  
  
|值|说明|  
|-----------|-----------------|  
|**heartbeat_interval**|在不记录进度消息的情况下代理可以运行的最大分钟数。|  
|NULL（默认值）|将打印所有可用的*属性*值。|  
  
`[ @value = ] 'value'`给定分发服务器属性的值。 *值*为**varchar （255）**，默认值为 NULL。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功）或**1** （失败）  
  
## <a name="remarks"></a>备注  
 **sp_changedistributor_property**在所有类型的复制中使用。  
  
## <a name="example"></a>示例  
 [!code-sql[HowTo#sp_changedistributor_property](../../relational-databases/replication/codesnippet/tsql/sp-changedistributor-pro_1.sql)]  
  
## <a name="permissions"></a>权限  
 只有**sysadmin**固定服务器角色的成员才能**sp_changedistributor_property**执行。  
  
## <a name="see-also"></a>另请参阅  
 [查看和修改分发服务器和发布服务器属性](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistributor &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md)   
 [sp_dropdistributor &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [复制存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
