---
title: SQL Server 浏览器属性（“登录”选项卡）
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: e1457374ca9e7ba7a0504e7c025333d3bcd48c20
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307101"
---
# <a name="sql-server-browser-properties-log-on-tab"></a>SQL Server 浏览器属性（“登录”选项卡）
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浏览器程序以服务的形式在服务器上运行。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浏览器侦听对 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源的传入请求，并提供计算机上安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的相关信息。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浏览器使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 解析协议 (SSRP) 侦听 UDP 端口，并接受未经身份验证的请求。  
  
 对帐户密码的更改立即生效，无需重新启动服务。  
  
## <a name="options"></a>选项  
 **本地系统帐户**  
 在本地系统帐户的安全上下文中运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。 请尽可能使用低权限帐户。  
  
 **本帐户**  
 指定一个使用 Windows 身份验证的本地用户帐户或域用户帐户。 建议使用具有最低服务权限的域用户帐户。 有关选择帐户的信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“设置 Windows 服务帐户”。  
  
 **“浏览”**  
 浏览用户或内置安全主体。  
  
> [!IMPORTANT]  
>  使用低权限帐户。 有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务所需权限的信息，请参阅 [SQL Server Browser 服务](../../tools/configuration-manager/sql-server-browser-service.md)中的“安全性”部分。  
  
 **密码**  
 输入安全主体的密码。  
  
 **确认密码**  
 确认安全主体的密码。  
  
 **服务状态**  
 指示此服务是正在运行、已停止还是已禁用。 “...  ”指明状态更改是挂起的。  
  
 **启动**  
 启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。  
  
 **Stop**  
 停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。  
  
 **暂停**  
 暂停 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。  
  
 **恢复**  
 恢复暂停的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server Browser 服务](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
