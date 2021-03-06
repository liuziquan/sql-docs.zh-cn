---
title: 第 6 步：断开与数据源的连接 |微软文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], disconnecting from data source
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
ms.assetid: 6ad759ba-4721-4d8f-9b26-de976d4fc1a0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df8cd94435d74bf813b0b64be0753a0beb44d354
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302788"
---
# <a name="step-6-disconnect-from-the-data-source"></a>步骤 6：从数据源断开连接
最后一步是断开与数据源的连接，如下图所示。 首先，应用程序通过调用**SQLFreeHandle**释放任何语句句柄。 有关详细信息，请参阅[释放语句句柄](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md)。  
  
 ![显示如何断开与数据源的连接](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 接下来，应用程序使用**SQLDisconnect**与数据源断开连接，并释放**SQLFreeHandle**的连接句柄。 有关详细信息，请参阅[断开与数据源或驱动程序](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md)的连接。  
  
 最后，应用程序使用**SQLFreeHandle**释放环境句柄并卸载驱动程序管理器。 有关详细信息，请参阅[分配环境句柄](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)。
