---
title: 通用数据链接 (UDL) 配置 | Microsoft Docs
description: 使用 Microsoft OLE DB Driver for SQL Server 的通用数据链接 (UDL) 配置
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
ms.author: v-beaziz
author: bazizi
ms.openlocfilehash: d92555fba1d9e0a380ffdc9051817ddfae9ca4b7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2020
ms.locfileid: "72381762"
---
# <a name="universal-data-link-udl-configuration"></a>通用数据链接 (UDL) 配置
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="connection-tab"></a>“连接”选项卡
使用“连接”选项卡，指定如何 Microsoft OLE DB Driver for SQL Server 连接到数据。

![OLE DB 数据链接页的屏幕截图 -“连接”选项卡](../media/data-link-pages-connection-tab.png)

该“连接”选项卡特定于提供程序并且只显示适用于 SQL Server 的 Microsoft OLE DB 驱动程序需要的连接属性。

|选项|说明|
|---   |---        |
|选择或输入服务器名称|从下拉列表中选择服务器名称，或者键入要访问的数据库所在的服务器的位置。 在服务器上选择数据库是一项单独的操作。 单击“刷新”可更新列表。
|输入登录服务器所需的信息|可以从此下拉列表选择以下身份验证选项： <ul><li>`Windows Authentication:` 使用当前登录用户的 Windows 帐户凭据对 SQL Server 进行身份验证。</li><li>`SQL Server Authentication:` 使用登录 ID 和密码进行身份验证。</li><li>`Active Directory - Integrated:` 使用 Azure Active Directory 标识进行集成身份验证。 此模式还可用于对 SQL Server 进行 Windows 身份验证。</li><li>`Active Directory - Password:` 使用 Azure Active Directory 标识进行用户 ID 和密码身份验证。</li><li>`Active Directory - Universal with MFA support:` 使用 Azure Active Directory 标识进行交互式身份验证。 此模式支持 Azure 多重身份验证 (MFA)。</li></ul>|
|服务器 SPN|如果您使用受信任连接，则可为服务器指定服务主体名称 (SPN)。|
|用户名|键入登录数据源时要用于身份验证的用户 ID。|
|密码|键入登录数据源时要用于身份验证的密码。|
|空密码|选中此选项后，则允许指定的提供程序在连接字符串中使用空密码。|
|允许保存密码|选中此选项后，允许将密码与连接字符串一起保存。 是否在连接字符串中包括密码取决于调用应用程序的功能。 <br/><br/>注意：  如果保存密码，则密码在返回和保存时是未屏蔽和未加密的。|
|对数据使用强加密|如果选中，将对通过连接传递的数据进行加密。|
|信任服务器证书|如果选中，将验证服务器证书。 服务器证书必须具有正确的服务器主机名，并由受信任的证书颁发机构颁发。|
|选择数据库|选择或键入要访问的数据库名称。|
|附加数据库文件作为数据库名称|指定可附加数据库的主文件的名称。 该数据库作为数据源的默认数据库附加和使用。 在此部分下的第一个文本框中，键入要用于附加数据库文件的数据库名称。<br/><br/>在标记为 `Using the filename` 的文本框中键入要附加的数据库文件的完整路径，或者单击 `...` 按钮以浏览数据库文件。|
|更改密码|显示“更改 SQL Server 密码”对话框。 |
|测试连接|单击此项将尝试连接到指定的数据源。 如果连接失败，请确保设置是正确的。 例如，拼写错误和大小写不同均可能导致连接失败。|

## <a name="advanced-tab"></a>高级选项卡
使用“高级”选项卡可以查看和设置其他初始化属性。

![OLE DB 数据链接页的屏幕截图 -“高级”选项卡](../media/data-link-pages-advanced-tab.png)

|选项|说明|
|---   |---        |
| 连接超时 | 指定 Microsoft OLE DB Driver for SQL Server 等待初始化完成所用的时间（以秒为单位）。 如果初始化超时，则返回一个错误并且不创建该连接。|


> [!NOTE]  
>  有关更多常规数据链接连接的信息，请参阅[数据链接 API 概述](https://go.microsoft.com/fwlink/?linkid=2067432)。

## <a name="next-steps"></a>后续步骤
- 使用 OLE DB 驱动程序[对 Azure Active Directory 进行身份验证](../features/using-azure-active-directory.md)。

- [提示用户使用 OLE DB 驱动程序提供身份验证凭据](../help-topics/sql-server-login-dialog.md)。