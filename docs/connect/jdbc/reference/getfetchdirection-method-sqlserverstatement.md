---
title: getFetchDirection 方法 (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ceb4ae68-decc-46d3-83f1-0bbd23aaf58c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 231811818c5a733f0224465e93739f7fee96f9de
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924823"
---
# <a name="getfetchdirection-method-sqlserverstatement"></a>getFetchDirection 方法 (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索从数据库表中提取行的方向，这是通过此 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 对象生成的结果集的默认方向。  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 目前未实现此方法。 因此，它将始终返回 FETCH_UNKNOWN。  
  
## <a name="syntax"></a>语法  
  
```  
  
public final int getFetchDirection()  
```  
  
## <a name="return-value"></a>返回值  
 指示由 [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md) 方法指定的提取方向的 int  值。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 getFetchDirection 方法是由 java.sql.Statement 接口中的 getFetchDirection 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerStatement 成员](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 类](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
