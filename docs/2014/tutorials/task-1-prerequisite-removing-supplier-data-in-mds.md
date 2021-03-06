---
title: 任务 1（先决条件）：删除 MDS 中的供应商数据 |微软文档
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6f0a4287-7fd4-4f18-b7e4-a5191a9d4a3c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 0290f033be47bec61e9ccce8465892d8cc98608c
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484627"
---
# <a name="task-1-prerequisite-removing-supplier-data-in-mds"></a>任务 1（先决条件）：删除 MDS 中的供应商数据
  在本任务中，您将删除在 MDS 中存储的供应商数据。 在上一课中，您使用**MDS Excel 外接程序**手动上载数据。 您在本课中创建的 SSIS 包将自动为您将数据上载到 MDS。 因此，在测试该 SSIS 包之前，您需要从 MDS 删除供应商数据，删除派生的层次结构，删除供应商和状态实体，并且创建不含数据的供应商实体。  
  
1.  通过导航到`http://localhost/MDS`配置 MDS 时指定的网站和应用程序来启动**主数据管理器**。 如果保持**主数据管理器**打开，请单击顶部的**SQL Server 2012 主数据服务**以切换到**主页**。  
  
2.  单击 **"管理任务**"部分中的 **"系统管理**"。  
  
3.  将鼠标悬停在菜单上**的管理**上，然后单击 **"派生层次结构**"。 在删除**供应商**模型中的实体之前，您需要删除派生层次结构 **"供应商InState"。**  
  
4.  从**派生层次结构**列表中选择 **"供应商 InState"，** 然后单击工具栏上的**X（删除）** 按钮。  
  
5.  单击 **"确定"** 以确认删除。  
  
6.  将鼠标悬停在菜单上**的"管理**"上，然后单击"**实体**"。  
  
7.  单击 **"供应商**"，然后单击工具栏上的 **"删除 （X）"** 按钮以删除实体。 单击消息框上的 **"确定**"。  
  
8.  重复上一步删除**状态**实体。  
  
9. 不要关闭**主数据管理器**。  
  
10. 切换到已**打开"已清除和匹配供应商.xls"** 文件的 Excel 窗口。 切换到底部的**Sheet1**选项卡。  
  
11. 仅选择**具有标头的第一行**。 不要选择任何其他行。 您希望基于 Excel 列创建实体，但不希望上载任何数据。 因此，您仅选择第一行和标题。  
  
12. 单击菜单栏上的 **"主数据**"。  
  
13. 单击从功能区**创建实体**。  
  
14. 在 **"管理连接"** 对话框中，如果在**现有连接**下看不到与**本地 MDS 服务器**的连接，则执行以下操作：  
  
    1.  选择 **"创建新连接**"，然后单击 **"新建"** 按钮。  
  
    2.  在"添加新连接"对话框中，键入 **"本地 MDS 服务器****说明"** 和 **"http：/\/本地主机/MDS MDS**用于**MDS 服务器地址**"，然后单击"**确定"** 以关闭该对话框。  
  
15. 在 **"管理连接"** 对话框中，选择 **"本地 MDS 服务器**" （）`http://localhost/MDS`"，单击 **"测试**"以测试连接。 单击消息框上的 **"确定**"。  
  
16. 单击"**连接**"以连接到 MDS 服务器。  
  
17. 在 **"创建实体"** 对话框中，执行以下操作：  
  
    1.  确认**范围**设置为 **$1：$1**。  
  
    2.  为**模型**选择**供应商**。  
  
    3.  选择**版本****VERSION_1。**  
  
    4.  键入 **"新实体名称****的供应商**"。  
  
    5.  为**代码**选择**供应商 ID。**  
  
    6.  为**名称**选择**供应商名称**。  
  
    7.  单击"**确定"** 以创建实体并关闭对话框。  
  
18. 关闭**Excel，****不要保存**该文件。  
  
19. 在**主数据管理器**中，刷新互联网浏览器并确认**供应商**实体显示在列表中。  
  
20. 单击顶部的**SQL Server 2012 主数据服务**，切换到**主页**。  
  
21. 确认为 **"模型**"选择了**供应商**模型，并为**版本**选择了**VERSION_1。**  
  
22. 单击 **“资源管理器”**。 请注意，具有所有属性的**供应商**实体是在**没有值时**创建的。  
  
## <a name="next-step"></a>下一步  
 [任务 2 &#40;可选&#41;：使用主数据管理器创建 MDS 订阅视图](../../2014/tutorials/task-2-optional-creating-a-mds-subscription-view-using-master-data-manager.md)  
  
  
