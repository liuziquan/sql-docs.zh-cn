---
title: 筛选表中的数据（SSAS 表格） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.customfilterdb.f1
- sql12.asvs.bidtoolset.autofiltermenu.f1
- sql12.asvs.bidtoolset.notallitemsshowing.f1
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 869185e56db9a4ffb07282d3ce51ced191a6bac8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "66067131"
---
# <a name="filter-data-in-a-table-ssas-tabular"></a>筛选表中的数据（SSAS 表格）
  您可以在导入数据时应用筛选器，以便控制加载到表中的行。 在导入数据后，不能删除单独的行。 不过，您可以应用自定义筛选器，以便控制显示行的方式。 不符合筛选条件的行会被隐藏。 您可以基于一列或多列进行筛选。 筛选器是累加式的，这意味着每个附加的筛选器都基于当前筛选器，从而进一步减少数据子集。  
  
> [!NOTE]  
>  筛选器预览窗口限制了显示的不同值的数量。 如果超出限制，则将显示一条消息。  
  
### <a name="to-filter-data-based-on-column-values"></a>基于列值筛选数据  
  
1.  在模型设计器中，选择一个表，然后单击您要基于其进行筛选的列标题中的箭头。  
  
2.  在“自动筛选”菜单中，执行以下操作之一：  
  
    -   在列值的列表中，选择或清除一个或多个要按其进行筛选的值，然后单击 **"确定"**。  
  
         如果值的数目极多，则可能无法在列表中显示各个项。 此时您将看到消息“项过多，无法显示。”  
  
    -   单击 "**数字筛选器**" 或 "**文本筛选器**" （具体取决于列的类型），然后单击比较运算符命令（如**Equals**），或单击 "**自定义筛选器**"。 在 **“自定义筛选器”** 对话框中，创建筛选器，然后单击 **“确定”**。  
  
### <a name="to-clear-a-filter-for-a-column"></a>清除列筛选器  
  
1.  单击您要清除其筛选器的列的标题中的箭头。  
  
2.  单击 "**从列名\<中清除筛选器">**。  
  
### <a name="to-clear-all-filters-for-a-table"></a>清除表的所有筛选器  
  
1.  在模型设计器中，选择您要为其清除筛选器的表。  
  
2.  单击 **“列”** 菜单，然后单击 **“清除所有筛选器”**。  
  
## <a name="see-also"></a>另请参阅  
 [&#40;SSAS 表格中对数据进行筛选和排序&#41;](../filter-and-sort-data-ssas-tabular.md)   
 [SSAS 表格&#41;&#40;透视](perspectives-ssas-tabular.md)   
 [&#40;SSAS 表格&#41;的角色](roles-ssas-tabular.md)  
  
  
