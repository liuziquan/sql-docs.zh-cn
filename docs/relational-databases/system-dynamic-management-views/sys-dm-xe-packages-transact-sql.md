---
title: sys. dm_xe_packages （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xe_packages_TSQL
- sys.dm_xe_packages_TSQL
- dm_xe_packages
- sys.dm_xe_packages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_packages dynamic management view
- extended events [SQL Server], views
ms.assetid: 2e5ecbe9-3ea8-45e6-a161-e31671a03e1d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 065625fdaca015de9c445e6e6f0e1ad0013f38e4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "68090261"
---
# <a name="sysdm_xe_packages-transact-sql"></a>sys.dm_xe_packages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  列出注册到扩展事件引擎的所有包。  
  
 
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|name|**nvarchar(256)**|包的名称。 包自身便可显示说明。 不可为 null。|  
|guid|**uniqueidentifier**|标识包的 GUID。 不可为 null。|  
|description|**nvarchar （3072）**|包说明。 包作者设置的 descriptionis 不能为 null。|  
|capabilities|**int**|说明此包的功能的位图。 可以为 Null。|  
|capabilities_desc|**nvarchar(256)**|此包可能具有的所有功能的列表。 可以为 Null。|  
|module_guid|**nvarchar （60）**|公开此包的模块的 GUID。 不可为 null。|  
|module_address|**varbinary(8)**|用于加载包含此包的模块的基址。 单个模块可以公开多个包。 不可为 null。|  
  
## <a name="permissions"></a>权限  
 要求具有服务器的 VIEW SERVER STATE 权限。  
  
## <a name="remarks"></a>备注  
 向扩展事件引擎注册的包可以公开事件、激发事件时可采取的操作以及事件数据的同步和异步处理目标。  
  
 这些包可以动态加载到进程地址空间中。 包在加载时将向扩展事件引擎注册其公开的所有对象。  
  
## <a name="relationship-cardinalities"></a>关系基数  
  
||||  
|-|-|-|  
|从|目标|关系|  
|sys.dm_xe_packages.module_address|sys.dm_os_loaded_modules.base_address|多对一|  
  
## <a name="see-also"></a>另请参阅  
 [动态管理视图和函数 (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

