---
title: SQL Server 登录对话框 (OLE DB) | Microsoft Docs
description: 使用 SQL Server 登录对话框
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
ms.author: v-beaziz
author: bazizi
ms.openlocfilehash: d35c339798b4385cb903d8a4a83f13184bbf4db3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2020
ms.locfileid: "72381745"
---
# <a name="sql-server-login-dialog-box"></a>SQL Server 登录对话框
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

如果尝试在未指定足够信息的情况下进行连接，则 OLE DB 驱动程序会显示“SQL Server 登录”  对话框。

> [!NOTE]  
> SQL Server 登录对话框提示行为由 `DBPROP_INIT_PROMPT` 初始化属性控制。 有关详细信息，请参阅：
> - [初始化和授权属性](../ole-db-data-source-objects/initialization-and-authorization-properties.md)
> - [OLE DB 程序员指南](https://go.microsoft.com/fwlink/?linkid=2067702)

![SQL Server 登录对话框屏幕截图](../media/sql-server-login-dialog.png)

## <a name="options"></a>选项
|选项|说明|
|---   |---        |
|服务器|网络上的 SQL Server 实例的名称。 从列表中选择一个服务器\实例名，或在“服务器”  框中键入服务器\实例名。 或者，可以在客户端计算机上使用“SQL Server 配置管理器”  创建服务器别名，并在“服务器”  框中键入该名称。 <br/><br/>当使用与 SQL Server 相同的计算机时可以输入“(local)”。 即使正在运行非联网版的 SQL Server，也可以连接到 SQL Server 的本地实例。<br/><br/>有关不同网络类型的服务器名称的详细信息，请参阅 [SQL Server 安装](https://go.microsoft.com/fwlink/?linkid=2067541)。|
|身份验证模式|可以从下拉列表选择以下身份验证选项：<br/><ul><li>`Windows Authentication:` 使用当前登录用户的 Windows 帐户凭据对 SQL Server 进行身份验证。</li><li>`SQL Server Authentication:` 使用登录 ID 和密码进行身份验证。</li><li>`Active Directory - Integrated:` 使用 Azure Active Directory 标识进行集成身份验证。 此模式还可用于对 SQL Server 进行 Windows 身份验证。</li><li>`Active Directory - Password:` 使用 Azure Active Directory 标识进行用户 ID 和密码身份验证。</li><li>`Active Directory - Universal with MFA support:` 使用 Azure Active Directory 标识进行交互式身份验证。 此模式支持 Azure 多重身份验证 (MFA)。</li></ul>|
|服务器 SPN|如果您使用受信任连接，则可为服务器指定服务主体名称 (SPN)。|
|登录 ID|指定用于连接的登录 ID。 仅当 `Authentication Mode` 设置为 `SQL Server Authentication`、`Active Directory - Password` 或 `Active Directory - Universal with MFA support` 时，才启用“登录 ID”文本框。|
|密码|指定用于连接的密码。 仅当 `Authentication Mode` 设置为 `SQL Server Authentication` 或 `Active Directory - Password` 时，才启用“密码”文本框。|
|选项|显示或隐藏“选项”  组。 如果“服务器”具有值，则启用“选项”   按钮。|
|更改密码|选中后，将启用“新密码”  和“确认新密码”  文本框。|
|新密码|指定新密码。|
|确认新密码|再次指定新密码以便确认。|
|数据库|选择或键入将用于该连接的默认数据库。 此设置将覆盖为该服务器上的登录名指定的默认数据库。 如果未指定数据库，连接将使用为该服务器上的登录名指定的默认数据库。|
|镜像服务器|指定要镜像的数据库的故障转移伙伴的名称。|
|镜像 SPN|您还可以指定镜像服务器的 SPN。 镜像服务器的 SPN 用于在客户端和服务器之间相互进行身份验证。|
|语言|指定用于 SQL Server 系统消息的国家/地区语言。 运行 SQL Server 的计算机必须安装该语言。 此设置将覆盖为该服务器上的登录名指定的默认语言。 如果未指定语言，连接将使用为该服务器上的登录名指定的默认语言。|
|应用程序名称|指定将要存储在 sys.sysprocesses  中该连接所在行的 program_name  列中的应用程序名称。|
|工作站 ID|指定将要存储在 sys.sysprocesses  中该连接所在行的 hostname  列中的工作站 ID。|
|对数据使用强加密|如果选中，将对通过连接传递的数据进行加密。|
|信任服务器证书|如果选中，将验证服务器证书。 服务器证书必须具有正确的服务器主机名，并由受信任的证书颁发机构颁发。|

> [!NOTE]  
> 当使用 `Windows Authentication` 或 `SQL Server Authentication` 模式时，仅当启用“对数据使用强加密”  选项时，才考虑“信任服务器证书”  。

## <a name="next-steps"></a>后续步骤
- 使用 OLE DB 驱动程序[对 Azure Active Directory 进行身份验证](../features/using-azure-active-directory.md)。
- 使用[通用数据链接 (UDL)](data-link-pages.md) 设置连接信息。