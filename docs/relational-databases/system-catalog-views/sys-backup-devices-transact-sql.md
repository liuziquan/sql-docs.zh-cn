---
title: sys. backup_devices （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- backup_devices_TSQL
- backup_devices
- sys.backup_devices
- sys.backup_devices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup devices [SQL Server], viewing information
- sys.backup_devices catalog view
ms.assetid: 457edaa4-aca1-4bd3-bf8d-734490b80fcd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b70d87a6f1a72662c1ca466a532d3050b4fe58ab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67942581"
---
# <a name="sysbackup_devices-transact-sql"></a>sys.backup_devices (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  使用**sp_addumpdevice**注册或在中[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]创建的每个备份设备都包含一行。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**路径名**|**sysname**|备份设备的名称。 在集中是唯一的。|  
|type |**tinyint**|备份设备的类型：<br /><br /> 2 = 磁盘<br /><br /> 3 = 软盘（已过时）<br /><br /> 5 = 磁带<br /><br /> 6 = 管道（已过时）<br /><br /> 7 = 虚拟设备（供第三方备份供应商选择使用）<br /><br /> 通常情况下，只使用磁盘 (2) 和磁带 (5)。|  
|**type_desc**|**nvarchar （60）**|备份设备类型的说明：<br /><br /> DISK<br /><br /> DISKETTE（已过时）<br /><br /> TAPE<br /><br /> PIPE（已过时）<br /><br /> VIRTUAL_DEVICE（供第三方备份供应商选择使用）<br /><br /> 通常情况下，只使用磁盘和磁带。|  
|**physical_name**|**nvarchar(260)**|备份设备的物理文件名或路径。|  
  
## <a name="permissions"></a>权限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另请参阅  
 [目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [备份设备 (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [sp_addumpdevice (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [数据库和文件目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [查询 SQL Server 系统目录常见问题](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
