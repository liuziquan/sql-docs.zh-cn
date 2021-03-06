---
title: 使用连接字符串 |微软文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection strings [ODBC]
- connecting to data source [ODBC], Visual FoxPro
- Visual FoxPro data source [ODBC], connecting
ms.assetid: 57634960-47e9-49bf-95c1-6e3702ac8166
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9083414503606720a40d372ed883a140953dc415
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307588"
---
# <a name="using-connection-strings"></a>使用连接字符串
您可以使用连接字符串连接到 Visual FoxPro 数据源。  
  
 例如，要连接到 TasTrade 数据源并覆盖与数据源关联的独占独占的当前设置，请使用字符串：  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 有关可以在连接字符串中包含的属性关键字和值的列表，请参阅[SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)。  
  
 有关连接字符串语法的完整说明，请参阅*ODBC 程序员参考*中的[SQLBrowseConnect。](../../odbc/reference/syntax/sqlbrowseconnect-function.md)
