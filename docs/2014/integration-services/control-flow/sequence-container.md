---
title: 序列容器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sequencecontainer.f1
helpviewer_keywords:
- Sequence container
- grouping control flows
- containers [Integration Services], Sequence
- subset control flow [Integration Services]
ms.assetid: 7731f91e-b8b3-4d96-a0d9-73f568547cb3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ec92f58f4dcd44fc39bfc34968a7883cb9c4cb4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "62830113"
---
# <a name="sequence-container"></a>序列容器
  序列容器可定义作为包控制流子集的控制流。 序列容器将包分组到多个单独的控制流中，每个控制流包含一个或多个在整体包控制流中运行的任务和容器。  
  
 除包含其他容器外，序列容器还可以包含多个任务。 将任务和容器添加到序列容器的过程与将它们添加到包的过程相似，唯一不同是把任务和容器拖动到序列容器，而不是拖动到包容器。 如果序列容器包含多个任务或容器，可以使用优先约束连接它们，如同在包中的操作一样。 有关详细信息，请参阅 [优先约束](precedence-constraints.md)。  
  
 使用序列容器有许多好处：  
  
-   禁用任务组，以便将包调试主要放在包控制流的一个子集上执行。  
  
-   通过设置序列容器而不是各个任务的属性来管理一个位置中多个任务的属性。  
  
     例如，可以将序列容器的 `Disable` 属性设置为 `True`，以禁用序列容器中的所有任务和容器。  
  
-   提供一组相关任务和容器所用变量的范围。  
  
-   对许多任务进行分组，以便您可以通过展开和折叠序列容器，更轻松地管理这些任务。  
  
     也可以创建任务组，这些任务组用 **“分组”** 框展开和折叠。 但是，“分组”  框是设计时功能，没有属性或运行时行为。 有关详细信息，请参阅 [对组件分组或取消分组](../group-or-ungroup-components.md)  
  
-   在序列容器上设置事务属性，以便为包控制流的子集定义事务。 采用这种方法，可以更详细地管理事务。  
  
     例如，如果序列容器包含两个相关任务（一个任务删除表中的数据，另一个将数据插入到表中），则可配置事务以确保插入操作失败时回滚删除操作。 有关详细信息，请参阅 [Integration Services 事务](../integration-services-transactions.md)。  
  
## <a name="configuration-of-the-sequence-container"></a>序列容器的配置  
 序列容器没有自定义用户界面，您只能通过 **中的** “属性” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 窗口对其进行配置，或以编程方式配置。  
  
 有关以编程方式设置这些属性的详细信息，请参阅开发人员指南中针对 **T:Microsoft.SqlServer.Dts.Runtime.Sequence** 类的文档。  
  
## <a name="related-tasks"></a>Related Tasks  
 有关如何在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中设置组件属性的信息，请参阅 [设置任务或容器的属性](../set-the-properties-of-a-task-or-container.md)。  
  
## <a name="see-also"></a>另请参阅  
 [在控制流中添加或删除任务或容器](add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [使用默认优先约束来连接任务和容器](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [Integration Services 容器](integration-services-containers.md)  
  
  
