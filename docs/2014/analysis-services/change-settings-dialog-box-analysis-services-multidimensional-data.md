---
title: "\"更改设置\" 对话框（Analysis Services 多维数据） |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.batchsettingsdialog.f1
ms.assetid: 0041e042-d7ce-48f9-a690-a6dc65471ff3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 43dfc1dca2e60fe2f5e467556ee36c3add1a9da3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "66088253"
---
# <a name="change-settings-dialog-box-analysis-services---multidimensional-data"></a>“更改设置”对话框（Analysis Services - 多维数据）
  使用 **和** 中的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] “更改设置” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 对话框，可以更改对 **“处理”** 对话框中所列对象的处理进行控制的设置。 单击 **“处理”** 对话框中的 **“更改设置”** ，将显示 **“更改设置”** 对话框。  
  
> [!NOTE]  
>  此对话框中指定的设置将覆盖从 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库继承的“处理”**** 对话框中所列对象的默认设置。  
  
## <a name="options"></a>选项  
 **处理选项**  
 使用此选项卡可以修改与处理顺序、写回表和受处理操作影响的对象相关的设置。 该选项卡包含下列选项：  
  
 **Parallel**  
 单击此项可并行处理对象。  
  
 **最大并行任务数**  
 选择处理操作并行执行的最大任务数，或选择“让服务器决定”**** 以允许 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 选择并行任务的最佳数量。  
  
 **顺序**  
 单击此项可按顺序处理对象。  
  
 **事务模式**  
 选择用于按顺序处理对象时使用的事务模式：  
  
-   **一个事务**处理同一事务中的所有对象。  
  
-   **单独的事务**在单独的事务中处理所有对象（包括依赖对象）。  
  
> [!NOTE]  
>  只有在选择了“按顺序”**** 时，才会启用此选项。  
  
 **写回表选项**  
 选择用于管理写回表的选项：  
  
-   **Create**创建写回表（如果不存在）。 如果写回表已存在，则会出现错误。  
  
-   **Create 始终**创建写回表（如果不存在），或者覆盖现有写回表（如果存在）。  
  
-   **使用现有**的写回表（如果存在）。 如果写回表不存在，则会出现错误。  
  
 **处理受影响的对象**  
 选择此选项可以包括并处理特定的对象，这些对象依赖于处理操作中所包括的对象。  
  
 **维度键错误**  
 使用此选项卡可以修改与处理操作的错误配置相关的设置。 该选项卡包含下列选项：  
  
 **使用默认错误配置**  
 选择此选项可以在处理操作中使用对象的默认错误配置。  
  
 **使用自定义错误配置**  
 选择此选项可以为处理操作中的对象定义错误配置。  
  
 **键错误操作**  
 选择以下操作之一，以便在处理过程中遇到找不到的新键时执行：  
  
-   "**转换为未知" 将**记录的信息聚合到未知成员中。  
  
-   "**放弃记录**" 将排除记录的信息与对象一起处理。  
  
 **忽略错误计数**  
 单击此项可忽略处理过程中发生的任何错误。  
  
 **出错时停止**  
 单击此项可在出错时停止处理。 此选项将启用 **“错误数”** 和 **“出错时要执行的操作”** 选项。  
  
 **错误数**  
 键入处理停止前忽略的错误数。  
  
 **出错时操作**  
 选择以下操作之一，以便在错误数超出“错误数”**** 中的值时执行该操作：  
  
-   **停止处理**将结束处理操作。  
  
-   **停止日志记录**将停止记录错误，但继续处理操作。  
  
 **找不到键**  
 指定以下操作之一，以便在处理对象的过程中找不到键时执行该操作：  
  
-   **忽略错误**将忽略错误。  
  
-   "**报告并继续**" 将报告错误并继续处理操作。  
  
-   **报告并停止**报告错误并停止处理操作。  
  
 **重复键**  
 指定以下操作之一，以便在处理对象的过程中发现重复键时执行该操作：  
  
-   **忽略错误**将忽略错误。  
  
-   "**报告并继续**" 将报告错误并继续处理操作。  
  
-   **报告并停止**报告错误并停止处理操作。  
  
 **空键转换为未知键**  
 指定以下操作之一，以便在处理对象过程中向未知成员添加了空成员键时将执行该操作：  
  
-   **忽略错误**将忽略错误。  
  
-   "**报告并继续**" 将报告错误并继续处理操作。  
  
-   **报告并停止**报告错误并停止处理操作。  
  
 **不允许空键**  
 指定以下操作之一，以便在处理对象过程中发现了不允许的空键时将执行该操作：  
  
-   **忽略错误**将忽略错误。  
  
-   "**报告并继续**" 将报告错误并继续处理操作。  
  
-   **报告并停止**报告错误并停止处理操作。  
  
 **错误日志路径**  
 键入错误日志文件的完整路径和文件名。  
  
 **“浏览”**  
 单击此项以打开“打开”**** 对话框，然后选择错误日志文件的完整路径和文件名。  
  
 **处理受影响的对象**  
 单击此项可处理与“处理”**** 对话框中的所选对象存在依赖关系的对象。  
  
## <a name="see-also"></a>另请参阅  
 [&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 ["处理" 对话框 &#40;Analysis Services 多维数据&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
