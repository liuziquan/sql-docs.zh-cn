---
title: sys. availability_group_listener_ip_addresses （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- availability_group_listener_ip_addresses
- sys.availability_group_listener_ip_addresses
- availability_group_listener_ip_addresses_TSQL
- sys.availability_group_listener_ip_addresses_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], listeners
- sys.availability_group_listener_ip_addresses catalog view
ms.assetid: e515fa6b-1354-4110-9b70-ab2e6164c992
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a9c66e12ec326ba5021de0829b0d7cc479f858c1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67997584"
---
# <a name="sysavailability_group_listener_ip_addresses-transact-sql"></a>sys.availability_group_listener_ip_addresses (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  为 Windows Server 故障转移群集 (WSFC) 中任何 AlwaysOn 可用性组侦听程序的每个关联 IP 地址都返回一行。  
  
 主键： **listener_id** + **ip_address** + **ip_sub_mask**  
  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**listener_id**|**nvarchar （36）**|来自 Windows Server 故障转移群集 (WSFC) 群集的资源 GUID。|  
|**ip_address**|**nvarchar （48）**|可用性组侦听器的已配置虚拟 IP 地址。 返回一个 IPv4 或 IPv6 地址。|  
|**ip_subnet_mask**|**nvarchar （15）**|为可用性组侦听器配置的 IPv4 地址的已配置 IP 子网掩码（如果有）。<br /><br /> NULL = IPv6 子网|  
|**is_dhcp**|**bit**|IP 地址是否由 DHCP 配置，可为下列值之一：<br /><br /> 0 = IP 地址不由 DHCP 配置。<br /><br /> 1 = IP 地址由 DHCP 配置。|  
|**network_subnet_ip**|**nvarchar （48）**|指定 IP 地址所属子网的网络子网 IP 地址。|  
|**network_subnet_prefix_length**|**int**|IP 地址所属子网的网络子网前缀长度。|  
|**network_subnet_ipv4_mask**|**nvarchar （45）**|IP 地址所属子网的网络子网掩码。 **network_subnet_ipv4_mask**在[CREATE availability group](../../t-sql/statements/create-availability-group-transact-sql.md)或[ALTER availability group](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]语句的 WITH DHCP 子句中指定 DHCP <network_subnet_option> 选项。<br /><br /> NULL = IPv6 子网|  
|**状态**|**tinyint**|WSFC 群集中 IP 资源的“联机”/“脱机”状态，可为下列值之一：<br /><br /> 1 = 联机。 IP 资源处于联机状态。<br /><br /> 0 = 脱机。 IP 资源处于脱机状态。<br /><br /> 2 = 联机挂起。 IP 资源处于脱机状态，但正在联机。<br /><br /> 3 = 失败。 IP 资源尝试重新联机，但失败。|  
|**state_desc**|**nvarchar （60）**|**状态**说明，其中之一：<br /><br /> ONLINE<br /><br /> OFFLINE<br /><br /> ONLINE_PENDING<br /><br /> FAILED|  
  
## <a name="security"></a>安全性  
  
### <a name="permissions"></a>权限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另请参阅  
 [查询 SQL Server 系统目录常见问题](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
