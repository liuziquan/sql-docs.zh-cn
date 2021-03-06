---
title: sp_fulltext_database （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_database_TSQL
- sp_fulltext_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_database
ms.assetid: eeb1e151-eb00-484c-8fd1-5641e621ffc6
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0c27f2efcfc15cc1ff9d53f735c08fad922f9466
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124280"
---
# <a name="sp_fulltext_database-transact-sql"></a>sp_fulltext_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  对 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更高版本中的全文目录没有影响，支持它只是为了向后兼容。 **sp_fulltext_database**不会对给定数据库禁用全文引擎。 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，所有用户创建的数据库始终启用全文索引。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 改为使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_fulltext_database [@action=] 'action'  
```  
  
## <a name="arguments"></a>参数  
`[ @action = ] 'action'`要执行的操作。 **操作**为**varchar （20）**，可以是下列值之一。  
  
|值|说明|  
|-----------|-----------------|  
|**可**|支持它仅仅是为了保持向后兼容。 在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 及更高版本中对全文目录无效。|  
|**禁用**|支持它仅仅是为了保持向后兼容。 在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 及更高版本中对全文目录无效。|  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="result-sets"></a>结果集  
 无  
  
## <a name="remarks"></a>备注  
 在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 及更高版本中，无法禁用全文索引。 禁用全文索引不会删除**sysfulltextcatalogs**中的行，并且不会指示已启用全文的表不再标记为要进行全文索引。 所有的全文元数据定义仍然在系统表中。  
  
## <a name="permissions"></a>权限  
 只有**sysadmin**固定服务器角色的成员和**db_owner**固定数据库角色的成员才能执行**sp_fulltext_database**。  
  
## <a name="see-also"></a>另请参阅  
 [DATABASEPROPERTYEX &#40;Transact-sql&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [FULLTEXTSERVICEPROPERTY &#40;Transact-sql&#41;](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
