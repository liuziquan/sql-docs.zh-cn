---
title: SQLServerNClob 成员 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b063f191-175e-4430-aab7-d88907f4ebec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 80f495051aabf5ecf3d020fc749cfdb4ddfd4c5f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923539"
---
# <a name="sqlservernclob-members"></a>SQLServerNClob 成员
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  下表列出了由 [SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md) 类公开的成员。  
  
## <a name="constructors"></a>构造函数  
 无。  
  
## <a name="fields"></a>字段  
 无。  
  
## <a name="inherited-fields"></a>继承的字段  
 无。  
  
## <a name="methods"></a>方法  
  
|名称|说明|  
|----------|-----------------|  
|[free](../../../connect/jdbc/reference/free-method-sqlservernclob.md)|此方法释放 NCLOB  对象以及它所持有的资源。|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlservernclob.md)|检索由 java.sql.NClob  对象指定的 NCLOB  值作为 ASCII 流。|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)|检索由 java.sql.NClob  对象指定的 NCLOB  值。|  
|[getSubString](../../../connect/jdbc/reference/getsubstring-method-sqlservernclob.md)|在由 java.sql.NClob  对象指定的 NCLOB  值中检索指定子字符串的副本。|  
|[length](../../../connect/jdbc/reference/length-method-sqlservernclob.md)|在由 java.sql.NClob  对象指定的 NCLOB  值中检索字符数。|  
|[position](../../../connect/jdbc/reference/position-method-sqlservernclob.md)|根据指定的起始位置，检索指定 java.sql.NClob  对象的字符位置，或 java.sql.NClob  中的子字符串。|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlservernclob.md)|检索用于在指定起始位置将 ASCII 字符写入此 java.sql.NClob  对象表示的 NCLOB  值的流。|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlservernclob.md)|检索用于在指定起始位置将 Unicode 字符流写入此 java.sql.NClob  对象表示的 NCLOB  值的流。|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlservernclob.md)|将指定的 String  写入起始于指定位置的 NCLOB  。|  
|[truncate](../../../connect/jdbc/reference/truncate-method-sqlservernclob.md)|将 NCLOB  值截断为指定长度。|  
  
## <a name="inherited-methods"></a>继承的方法  
  
|类继承自|方法|  
|--------------------------|-------------|  
|java.lang.Object|clone、equals、finalize、getClass、hashCode、notify、notifyAll、toString、wait|  
|java.sql.Clob|free、getAsciiStream、getCharacterStream、getSubString、length、position、setAsciiStream、setCharacterStream、setString、truncate|  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerClob 类](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
