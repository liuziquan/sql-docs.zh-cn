---
title: MSSQLSERVER_21892 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21892 (Database Engine error)
ms.assetid: 199818e8-28f4-440e-ad85-7bea88f51153
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4ca49ebb4a7481fc7fd23e916d10a185632280cd
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2020
ms.locfileid: "68056651"
---
# <a name="mssqlserver_21892"></a>MSSQLSERVER_21892
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|21892|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|SQLErrorNum21892|  
|消息正文|无法在与虚拟网络名称“%s”相关联的可用性组主副本上查询 sys.availability_replicas 以获取成员副本的服务器名称：错误 = %d，错误消息 = %s。|  
  
## <a name="explanation"></a>说明  
**sp_validate_replica_hosts_as_publishers** 查询与重定向的发布服务器相关联的可用性组的当前主副本，以确定承载成员副本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。  当查询失败时，将返回错误 21892。  
  
首次使用临时链接服务器时，**sp_validate_replica_hosts_as_publishers** 通常为启用状态，因此，如果存在连接问题，这些问题可能首先与 **sp_validate_replica_hosts_as_publishers** 一起显示。 与 **sp_validate_redirected_publisher** 不同，在连接到任意可用性组副本主机时，**sp_validate_replica_hosts_as_publishers** 使用的链接服务器始终使用调用方的凭据。  
  
## <a name="user-action"></a>用户操作  
在运行该存储过程时，请确保以对所有副本均有效的登录名运行。 该登录名将要求足够的授权以查询可用性组元数据表，以及查询发布服务器数据库副本中的订阅元数据表。  
  
请检查原始引用的错误，以确定失败的原因和适当的更正措施。  
  
