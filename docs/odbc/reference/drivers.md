---
title: 驱动程序 |微软文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC]
- drivers [ODBC], about drivers
ms.assetid: d6795d92-877e-44e1-b7d5-2ff2fd3989bd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c8b40641be3db34fc6929edecdd5dd923700957
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294180"
---
# <a name="drivers"></a>驱动程序
*驱动程序*是在 ODBC API 中实现函数的库。 每个都特定于特定的 DBMS;例如，Oracle 的驱动程序不能直接访问 Informix DBMS 中的数据。 驱动程序公开底层 DBMS 的功能;它们不需要实现 DBMS 不支持的功能。 例如，如果基础 DBMS 不支持外部联接，则驱动程序也不应支持外部联接。 唯一的主要例外是，没有独立数据库引擎（如 Xbase）的 DBMS 的驱动程序必须实现至少支持最少数量的 SQL 的数据库引擎。  
  
 本部分包含以下主题。  
  
-   [驱动程序任务](../../odbc/reference/driver-tasks.md)  
  
-   [驱动程序体系结构](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft 提供的 ODBC 驱动程序](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
