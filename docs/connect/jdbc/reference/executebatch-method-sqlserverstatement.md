---
title: executeBatch 方法 (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.executeBatch
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fb034f63-2532-4da8-a1b0-bc125734585a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 46b738dfe180b6d137b47042a9b9db517cb3b93c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922047"
---
# <a name="executebatch-method-sqlserverstatement"></a>executeBatch 方法 (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  向数据库提交要运行的命令批。 如果所有命令都成功运行，则返回一个更新计数数组。  
  
## <a name="syntax"></a>语法  
  
```  
  
public int[] executeBatch()  
```  
  
## <a name="return-value"></a>返回值  
 一个包含更新计数的 int 数组。   
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
 java.sql.BatchUpdateException  
  
## <a name="remarks"></a>备注  
 此 executeBatch 方法是由 java.sql.Statement 接口中的 executeBatch 方法指定的。  
  
 向数据库提交命令后，此方法将清除批中的所有命令。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerStatement 成员](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 类](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
