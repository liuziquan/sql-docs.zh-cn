---
title: 更改装配体 |微软文档
description: 使用 ALTER ASSEMBLY 更新在 SQL 服务器中注册的程序集。 您还可以更改权限集并为程序集添加源代码或其他文件。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], modifying
- permissions [CLR integration]
- altering assemblies
- ALTER ASSEMBLY statement
ms.assetid: 9e765fbd-f339-473c-8537-22f478e79696
author: rothja
ms.author: jroth
ms.openlocfilehash: 07fd94c855a81a8d58ac1ed4b578edf478dc77aa
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2020
ms.locfileid: "81486830"
---
# <a name="altering-an-assembly"></a>改变程序集
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  可以使用 ALTER ASSEMBLY 语句从较新版本更新已在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中注册的程序集。 若要更新程序集，可按照如下语法使用 ALTER ASSEMBLY 语句：  
  
```  
ALTER ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
```  
  
 ALTER ASSEMBLY 不中断当前正在运行且正在使用此程序集的进程；这些进程使用未经更改的程序集继续执行。 ALTER ASSEMBLY 不能用于更改公共语言运行时 (CLR) 函数、聚合函数、存储过程和触发器的签名。 只要未更改签名或属性，就可以向程序集添加新的公共方法，以任何方式修改专用方法以及修改公共方法。 不能使用 ALTER ASSEMBLY 更改本机序列化用户定义类型（包含数据成员或基类）内包含的字段。 不支持所有其他更改。 有关详细信息，请参阅[&#40;交易-SQL&#41;](../../../t-sql/statements/alter-assembly-transact-sql.md)的 ALTER ASSEMBLY。  
  
## <a name="changing-the-permission-set-of-an-assembly"></a>更改程序集的权限集  
 还可以使用 ALTER ASSEMBLY 语句更改程序集的权限集。 以下语句将 SQLCLRTest 程序集的权限集更改为**EXTERNAL_ACCESS**。  
  
```  
ALTER ASSEMBLY SQLCLRTest  
WITH PERMISSION_SET = EXTERNAL_ACCESS   
```  
  
 如果程序集的权限集从**SAFE**更改为**EXTERNAL_ACCESS**或**UNSAFE，** 则必须首先创建具有**外部 ACCESS ASSEMBLY**权限或**程序集的不安全程序集**权限的不对称密钥和相应的登录。 有关详细信息，请参阅 [Creating an Assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)。  
  
## <a name="adding-the-source-code-of-an-assembly"></a>添加程序集的源代码  
 CREATE ASSEMBLY 中不存在 ALTER ASSEMBLY 语法中的 ADD FILE 子句。 您可以使用该子句来添加源代码或与程序集关联的任何其他文件。 这些文件将从其原始位置复制并存储到数据库的系统表中。 如果您需要重新创建或记录 UDT 的当前版本，这样可确保源代码或其他文件随时备用。  
  
 以下语句添加 Point UDT 的 Point.cs 类源代码。 这会复制 Point.cs 文件中包含的文本并用名称“PointSource”将其存储在数据库中。  
  
 `ALTER ASSEMBLY Point`  
  
 `ADD FILE FROM 'C:\Projects\Point\Point.cs' AS PointSource`  
  
## <a name="see-also"></a>另请参阅  
 [管理 CLR 集成程序集](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [创建程序集](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [删除程序集](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [ALTER ASSEMBLY (Transact-SQL)](../../../t-sql/statements/alter-assembly-transact-sql.md)  
  
  
