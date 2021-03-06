---
title: 安装和配置广域进口商示例数据库
description: 按照这些说明使用 SQL Server 管理工作室下载、安装和配置 WideWorld 导入器示例数据库。
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 355eaa254fcc7bb6cd4aa9a39c2cbcb269d88396
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487066"
---
# <a name="installation-and-configuration"></a>安装和配置
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
全球进口商 OLTP 数据库安装和配置说明。

## <a name="prerequisites"></a>先决条件

- [SQL 服务器 2016（](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)或更高）或[Azure SQL 数据库](https://azure.microsoft.com/services/sql-database/)。 对于示例的完整版本，请使用 SQL 服务器评估/开发人员/企业版。
- [SQL 服务器管理工作室](../ssms/download-sql-server-management-studio-ssms.md)。 为获得最佳效果，请使用 2016 年 6 月版本或更高版本。

## <a name="download"></a>下载

示例的最新版本：

[全球进口商发布](https://go.microsoft.com/fwlink/?LinkID=800630)

下载与 SQL Server 或 Azure SQL 数据库版本对应的示例 WideWorld 导入者数据库备份/bacpac。

要重新创建示例数据库的源代码可从以下位置获得。 请注意，重新创建示例将导致数据略有不同，因为数据生成中有一个随机因素：

[广泛的世界进口商](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/sample-scripts)

## <a name="install"></a>安装


### <a name="sql-server"></a>SQL Server

要将备份还原到 SQL Server 实例，可以使用管理工作室。

1. 打开 SQL 服务器管理工作室并连接到目标 SQL Server 实例。
2. 右键单击**数据库**节点，然后选择 **"还原数据库**"。
3. 选择**设备**并单击按钮 **...**
4. 在对话框中选择**备份设备**，单击"**添加**"，导航到服务器文件系统中的数据库备份，然后选择备份。 单击“确定”。 
5. 如果需要，请更改"**文件"** 窗格中数据和日志文件的目标位置。 请注意，最佳做法是将数据和日志文件放在不同的驱动器上。
6. 单击“确定”。  这将启动数据库还原。 完成后，您将在 SQL Server 实例上安装数据库 WideWorld 导入器。

### <a name="azure-sql-database"></a>Azure SQL Database

要将百家乐导入新的 SQL 数据库，可以使用管理工作室。

1. （可选）如果 Azure 中尚未有 SQL 服务器，请导航到[Azure 门户](https://portal.azure.com/)并创建新的 SQL 数据库。 在创建数据库的过程中，您将创建一个服务器。 记下服务器。
   - 请参阅[本教程](https://azure.microsoft.com/documentation/articles/sql-database-get-started/)，在几分钟内创建数据库
2. 打开 SQL 服务器管理工作室并连接到 Azure 中的服务器。
3. 右键单击**数据库**节点，然后选择**导入数据层应用程序**。
4. 在"**导入设置"** 中选择 **"从本地磁盘导入**"，然后从文件系统中选择示例数据库的百科。
5. 在 **"数据库设置"** 下，将数据库名称更改为*WideWorld 导入器*，并选择要使用的目标版本和服务目标。
6. 单击"**下一步**"并**完成**以启动部署。 在 P1 上完成需要几分钟时间。 如果需要较低的定价层，建议将其导入到新的 P1 数据库中，然后将定价层更改为所需的级别。

## <a name="configuration"></a>配置

### <a name="full-text-indexing"></a>全文索引

示例数据库可以使用全文索引。 但是，默认情况下，该功能不会与 SQL Server 一起安装 - 您需要在 SQL Server 设置期间选择它（默认情况下在 Azure SQL DB 中启用此功能）。 因此，需要安装后步骤。

1. 在 SQL 服务器管理工作室中，连接到宽世界导入器数据库并打开新的查询窗口。
2. 运行以下 T-SQL 命令，以便在数据库中使用全文索引：`EXECUTE Application.Configuration_ApplyFullTextIndexing`


### <a name="sql-server-audit"></a>SQL Server 审核

适用范围：SQL Server

在 SQL Server 中启用审核需要服务器配置。 要为 WideWorld 导入器示例启用 SQL Server 审核，在数据库中运行以下语句：

    EXECUTE [Application].[Configuration_ApplyAuditing]

在 Azure SQL 数据库中，审核通过[Azure 门户](https://portal.azure.com/)进行配置。

### <a name="row-level-security"></a>行级安全性

应用于：Azure SQL 数据库

默认情况下，在宽世界进口商的 bacpac 下载中，不会启用行级安全性。 要在数据库中启用行级安全性，请运行以下存储过程：

    EXECUTE [Application].[Configuration_ApplyRowLevelSecurity]

