---
title: SQLSetDescField 和 SQLSetDescRec（光标库） |微软文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetDescField function [ODBC], Cursor Library
- SQLSetDescRec function [ODBC], Cursor Library
ms.assetid: 4ccff067-85cd-4bfa-a6cd-7f28051fb5b9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b85eb84cdf48a1c2a441b8994076a9023d254f2d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300547"
---
# <a name="sqlsetdescfield-and-sqlsetdescrec-cursor-library"></a>SQLSetDescField 和 SQLSetDescRec（游标库）
> [!IMPORTANT]  
>  此功能将在将来版本的 Windows 中删除。 避免在新的开发工作中使用此功能，并计划修改当前使用此功能的应用程序。 Microsoft 建议使用驱动程序的光标功能。  
  
 本主题讨论在游标库中使用**SQLSetDescField**和**SQLSetDescRec**函数。 有关这些函数的一般信息，请参阅[SQLSetDescField 函数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)和[SQLSetDescRec 函数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)。  
  
 在调用游标库以返回为书签列设置的字段的值时，游标库将执行**SQLSetDescField：**  
  
 SQL_DESC_DATA_PTR  
  
 SQL_DESC_INDICATOR_PTR  
  
 SQL_DESC_OCTET_LENGTH_PTR  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_DATETIME_INTERVAL_CODE  
  
 SQL_DESC_SCALE  
  
 SQL_DESC_PRECISION  
  
 SQL_DESC_TYPE  
  
 SQL_DESC_NAME  
  
 SQL_DESC_UNNAMED  
  
 SQL_DESC_NULLABLE  
  
 游标库执行对**SQLSetDesccRec**的书签列的调用。  
  
 使用 ODBC *2.x*驱动程序时，当调用**SQLSetDescField**或**SQLSetDescRec**将 ARD 书签记录的SQL_DESC_OCTET_LENGTH字段设置为不等于 4 的值时，光标库将返回 SQLSTATE HY090（无效字符串或缓冲区长度）。 使用 ODBC *3.x*驱动程序时，光标库允许缓冲区具有任何大小。  
  
 在调用游标库以返回SQL_DESC_BIND_OFFSET_PTR、SQL_DESC_BIND_TYPE、SQL_DESC_ROW_ARRAY_SIZE或SQL_DESC_ROW_STATUS_PTR字段的值时，游标库将执行**SQLSetDescField。** 可以为任何行返回这些字段，而不仅仅是书签行。  
  
 游标库不执行**SQLSetDescField**来更改除前面提到的字段之外的任何描述符字段。 如果应用程序调用**SQLSetDescField**在加载游标库时设置任何其他字段，则调用将传递到驱动程序。  
  
 游标库支持动态更改应用程序行描述符的任何行SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR和SQL_DESC_OCTET_LENGTH_PTR字段（在调用**SQL 扩展获取****、SQLFetch**或**SQLFetchScroll**之后）。 SQL_DESC_OCTET_LENGTH_PTR字段只能更改为空指针，以取消绑定列的长度缓冲区。  
  
 游标库不支持在打开游标时更改 APD 或 ARD 中的SQL_DESC_BIND_TYPE字段。 只有在关闭游标后和打开新游标之前，才能更改SQL_DESC_BIND_TYPE字段。 游标库在打开游标时支持更改的唯一描述符字段是SQL_DESC_ARRAY_STATUS_PTR、SQL_DESC_BIND_OFFSET_PTR、SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、SQL_DESC_OCTET_LENGTH_PTR和SQL_DESC_ROWS_PROCESSED_PTR。  
  
 在调用**SQL 延长获取**或**SQLFetchScroll**后以及游标关闭之前，游标库不支持修改 ARD 的SQL_DESC_COUNT字段。
