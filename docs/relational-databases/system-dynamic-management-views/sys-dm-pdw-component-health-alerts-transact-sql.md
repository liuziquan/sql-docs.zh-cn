---
title: sys. dm_pdw_component_health_alerts （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 88f05392-1e97-4693-ba60-a4910af3c000
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 770ddc4d1e182360b13d4f9e27d9e0bbf80cceee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899576"
---
# <a name="sysdm_pdw_component_health_alerts-transact-sql"></a>sys. dm_pdw_component_health_alerts （Transact-sql）
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  在设备组件上存储以前发出的警报。  
  
|列名|数据类型|说明|范围|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]节点的唯一标识符。<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id 和 alert_instance_id 构成此视图的键。|NOT NULL|  
|component_id|**int**|组件的 ID。 请参阅[sys.databases &#40;transact-sql&#41;pdw_health_components ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)。<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id 和 alert_instance_id 构成此视图的键。|NOT NULL|  
|component_instance_id|**nvarchar(255)**|pdw_node_id、component_id、component_instance_id、alert_id 和 alert_instance_id 构成此视图的键。|NOT NULL|  
|alert_id|**int**|警报类型的 ID。 请参阅[sys.databases &#40;transact-sql&#41;pdw_health_alerts ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md)。<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id 和 alert_instance_id 构成此视图的键。|NOT NULL|  
|alert_instance_id|**nvarchar （36）**|标识给定警报的实例。<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id 和 alert_instance_id 构成此视图的键。|NOT NULL|  
|previous_value|**nvarchar(255)**|当警报的类型为 StatusChange 时使用。 这是之前的组件状态。 对于阈值类型的警报，值为 NULL。 有关警报类型的列表，请参阅[&#40;transact-sql&#41;pdw_health_alerts](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) 。|Null|  
|current_value|**nvarchar(255)**|当警报的类型为 StatusChange 时使用。 这是当前的组件状态。 对于阈值类型的警报，值为 NULL。 有关警报类型的列表，请参阅[&#40;transact-sql&#41;pdw_health_alerts](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) 。|Null|  
|create_time|**datetime**|生成警报的时间和日期。|NOT NULL|  
  
## <a name="see-also"></a>另请参阅  
 [SQL 数据仓库和并行数据仓库动态管理视图 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
