---
title: 间隔转义序列 |微软文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9fe7f6941e9ec9fba8b6698faaa18a678732dd6f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304952"
---
# <a name="interval-escape-sequences"></a>间隔转义序列
ODBC 使用转义序列进行间隔文本。 此转义序列的语法如下：  
  
 [*间隔文本*]  
  
 有关*间隔文本*的 BNF 语法，请参阅本附录后面的[间隔文本语法](../../../odbc/reference/appendixes/interval-literal-syntax.md)部分。  
  
 如果数据源支持间隔数据类型，则支持间隔文本转义序列。 应用程序应调用**SQLGetTypeInfo**以确定是否支持这些数据类型。
