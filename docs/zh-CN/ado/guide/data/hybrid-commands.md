---
title: 混合命令 |Microsoft 文档
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- hybrid commands [ADO]
- data shaping [ADO], hybrid commands
ms.assetid: e8ca40e8-459c-40e2-8dd3-3ec6d5ee7b51
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 93991daa418ea94654c2f75c62a0f2f69aeab932
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="hybrid-commands"></a>混合命令
混合命令是部分参数化的命令。 例如：  
  
```  
SHAPE {select * from plants}   
   APPEND( {select * from customers where country = ?}   
           RELATE PlantCountry TO PARAMETER 0,   
             PlantRegion TO CustomerRegion )   
```  
  
 混合命令的缓存行为是相同的正则参数化命令。  
  
## <a name="see-also"></a>另请参阅  
 [调整示例数据](../../../ado/guide/data/data-shaping-example.md)   
 [正式形状语法](../../../ado/guide/data/formal-shape-grammar.md)   
 [常用 Shape 命令](../../../ado/guide/data/shape-commands-in-general.md)