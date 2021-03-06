---
title: SQLSet连接选项（dBASE 驱动程序） |微软文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLSetConnectOption
- SQLSetConnectOption function [ODBC], dBASE Driver
ms.assetid: b1924c33-6820-4566-b716-6897807edd0f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 32bfb4755d308706372c0d863f8246631c122f21
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301518"
---
# <a name="sqlsetconnectoption-dbase-driver"></a>SQLSetConnectOption（dBASE 驱动程序）
> [!NOTE]  
>  本主题提供特定于 dBASE 驱动程序的信息。 有关此功能的一般信息，请参阅[ODBC API 参考](../../odbc/reference/syntax/odbc-api-reference.md)下的相应主题。  
  
|fOption|注释|  
|-------------|-------------|  
|SQL_ACCESS_MODE|SQL_ACCESS_MODE fOption 可以设置为SQL_MODE_READ_ONLY或SQL_MODE_READ_WRITE。 但是，如果SQL_ACCESS_MODE设置为SQL_MODE_READ_ONLY，则驱动程序不会阻止更新。|  
|SQL_AUTOCOMMIT|dBASE 驱动程序仅支持SQL_AUTOCOMMIT设置为 ON（默认状态），因为它不支持事务。|  
|SQL_CURRENT_QUALIFIER|支持。|  
|SQL_LOGIN_TIMEOUT|不支持。|  
|SQL_OPT_TRACE|支持。|  
|SQL_OPT_TRACEFILE|支持。|  
|SQL_PACKET_SIZE|不支持。|  
|SQL_QUIET_MODE|不支持。|  
|SQL_TRANSLATE_DLL|不支持。|  
|SQL_TRANSLATION_OPTION|不支持。|  
|SQL_TXN_ISOLATION|不支持。|
