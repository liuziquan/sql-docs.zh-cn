---
title: 创建事务数据的 InfoSource | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ab5f23e2-cd4e-4507-83d9-ac5ef721c171
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c18c6edb21effe53c31e7885ec25025c94c4f1d2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37162728"
---
# <a name="create-infosource-for-transaction-data"></a>创建事务数据的 InfoSource
  使用 **“创建事务数据的 InfoSource”** 对话框为 SAP Netweaver BW 系统中的事务数据创建一个新的 InfoSource。  
  
 从 **“SAP BW 目标编辑器”** 的 **“连接管理器”** 页可以打开 **“创建事务数据的 InfoSource”** 对话框。 若要了解有关 SAP BW 目标的详细信息，请参阅 [SAP BW Destination](sap-bw-destination.md)。  
  
> [!IMPORTANT]  
>  针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。 有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。  
  
 **打开“创建事务数据的 InfoSource”对话框**  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 目标的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。  
  
2.  在“数据流”选项卡上，双击 SAP BW 目标。  
  
3.  在 **“SAP BW 目标编辑器”** 中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。  
  
4.  在 **“连接管理器”** 页的 **“创建 SAP BW 对象”** 组框中，选择 **“InfoSource”**，然后单击 **“创建”**。  
  
5.  在 **“创建 InfoSource”** 对话框中，选择 **“事务数据”**，然后单击 **“确定”**。  
  
## <a name="general-options"></a>常规选项  
 **InfoSource 名称**  
 输入新 InfoSource 的名称。  
  
 **简短说明**  
 输入新 InfoSource 的简短说明。  
  
 **详细说明**  
 输入新 InfoSource 的详细说明。  
  
 **源系统**  
 选择与 InfoSource 相关联的源系统。  
  
 **保存并激活**  
 保存并激活该新 InfoSource。  
  
## <a name="infosource-transfer-structure-options"></a>InfoSource 传输结构选项  
 InfoSource 传输结构可供您将数据流列与 InfoSource 关联。  
  
 **PipelineElement**  
 显示数据流输出中与 SAP BW 目标连接的列。  
  
 **PipelineDataType**  
 显示数据流列的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型。  
  
 **Iobject - 搜索**  
 将现有的 InfoObject 与当前行中的数据流列关联。 要进行此关联，请单击 **“搜索”**，然后使用 **“查找 InfoObject”** 对话框选择现有的 InfoObject。 有关此对话框的详细信息，请参阅 [Look Up InfoObject](look-up-infoobject.md)。  
  
 选择现有的 InfoObject 后，组件会将选定的值填充在 **“InfoObject”** 和 **“类型”** 列中。  
  
 **Iobject - 新建**  
 创建一个新的 InfoObject 并将该新 InfoObject 与当前行中的数据流列关联。 要创建新的 InfoObject，请单击 **“新建”**，然后使用 **“新建 InfoObject”** 对话框创建 InfoObject。 有关此对话框的详细信息，请参阅 [Create New InfoObject](create-new-infoobject.md)。  
  
 创建新 InfoObject 后，组件会将新值填充在 **“InfoObject”** 和 **“类型”** 列中。  
  
 **Iobject - 删除**  
 删除 InfoObject 与当前行的数据流列之间的关联。 若要删除此关联，请单击 **“删除”**。  
  
 **InfoObject**  
 显示与数据流列相关联的 InfoObject 的名称。  
  
 **“类型”**  
 显示与数据流列相关联的 InfoObject 的类型。 下表列出了该类型的可能值。  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|CHA|特征|  
|UNI|单位|  
|KYF|关键数字|  
|TIM|时间特征|  
  
 **单位字段**  
 指定 InfoObject 将使用的单位。  
  
## <a name="see-also"></a>请参阅  
 [创建 InfoSource](create-infosource.md)   
 [Microsoft Connector 1.1 for SAP BW 的 F1 帮助](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  