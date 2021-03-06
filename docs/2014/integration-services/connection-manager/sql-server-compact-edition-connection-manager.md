---
title: SQL Server Compact Edition 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Compact, connection manager
- connections [Integration Services], SQL Server Compact
- connection managers [Integration Services], SQL Server Compact
ms.assetid: ba627d4d-41f4-49fc-a921-f534cde67770
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 752c825cb34fbf2afe5d2306afbd562a49f74b7f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "62833142"
---
# <a name="sql-server-compact-edition-connection-manager"></a>SQL Server Compact Edition 连接管理器
  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 连接管理器使包能够连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 数据库。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]包含[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的 Compact 目标[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用此连接管理器将数据加载到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 数据库的表中。  
  
> [!NOTE]  
>  在 64 位计算机上，必须以 32 位模式运行连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 数据源的包。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用于连接到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Compact 数据源的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact Provider 只在 32 位版本中提供。  
  
## <a name="configuration-the-sql-server-compact-edition-connection-manager"></a>SQL Server Compact Edition 连接管理器的配置  
 将[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 连接管理器添加到包时， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]会创建将在运行时解析为[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 连接的连接管理器，设置该连接管理器的属性，并将该连接管理器`Connections`添加到包上的集合。  
  
 该连接管理器的 `ConnectionManagerType` 属性设置为 `SQLMOBILE`。  
  
 可以通过以下方式配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 连接管理器：  
  
-   提供指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 数据库位置的连接字符串。  
  
-   为受密码保护的数据库提供密码。  
  
-   指定存储数据库的服务器。  
  
-   指示是否在运行时保留从连接管理器中创建的连接。  
  
 可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。  
  
 有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：  
  
-   [SQL Server Compact Edition 连接管理器编辑器 &#40;连接页&#41;](../sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
-   [SQL Server Compact Edition 连接管理器编辑器 &#40;所有页面&#41;](../sql-server-compact-edition-connection-manager-editor-all-page.md)  
  
 有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。  
  
  
