---
title: 管理 CLR 集成程序集 |微软文档
description: 您可以在 SQL Server 中托管托管 DLL 程序集。  您可以注册、更改和删除程序集，还可以管理关联的文件和权限。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
author: rothja
ms.author: jroth
ms.openlocfilehash: 19b90d7994aa4b75a294f24345d43333d13a22df
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484726"
---
# <a name="managing-clr-integration-assemblies"></a>管理 CLR 集成程序集
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  托管代码在被编译后部署在称作程序集的单元中。 程序集将打包为 DLL 或可执行 (.exe) 文件。 尽管可执行文件可以自动运行，但 DLL 必须在现有应用程序中承载。 托管 DLL 程序集可以加载到 中[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]并由 承载。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 要求首先使用 CREATE ASSEMBLY 语句在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库中注册该程序集，然后才能将其加载到进程中并使用它。 还可以使用 ALTER ASSEMBLY 语句从更新的版本更新程序集，或者使用 DROP ASSEMBLY 语句从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中删除程序集。  
  
 程序集信息存储在已安装程序集的数据库中的**sys.assembly_files**表中。 **sys.assembly_files**表包含以下列。  
  
|列|说明|  
|------------|-----------------|  
|assembly_id|为程序集定义的标识符。 此编号分配到与同一程序集相关的所有对象。|  
|name|对象的名称。|  
|file_id|标识每个对象的数字，第一个与给定**assembly_id**关联的对象被给定值为 1。 如果多个对象与同一**个assembly_id**相关联，则每个后续**file_id**值将递增 1。|  
|content|程序集或文件的十六进制表示形式。|  
  
## <a name="in-this-section"></a>本节内容  
 [创建程序集](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
 介绍如何在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中创建 SAFE、EXTERNAL_ACCESS 和 UNSAFE CLR 程序集。  
  
 [改变程序集](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)  
 介绍如何在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中更新 CLR 程序集。  
  
 [删除程序集](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)  
 介绍如何从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中删除 CLR 程序集。  
  
## <a name="see-also"></a>另请参阅  
 [CLR 集成安全性](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [CLR 集成代码访问安全性](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)  
  
  
