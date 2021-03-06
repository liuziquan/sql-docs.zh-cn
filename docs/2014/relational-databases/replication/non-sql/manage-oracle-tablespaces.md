---
title: 管理 Oracle 表空间 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9a6bf22c7649646506b65628f556b52fead23375
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "63022300"
---
# <a name="manage-oracle-tablespaces"></a>管理 Oracle 表空间
  表空间是一个数据库存储单元，它大致等同于中[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的文件组。 表空间允许存储和管理各个组内的数据库对象。 有关详细信息，请参阅 Oracle 文档。  
  
 如果将表配置为 Oracle 发布的一部分，则可以选择指定在存储复制记录信息时使用现有的 Oracle 表空间。 如果未指定，则复制对象的表空间就是与配置发布服务器时配置的复制管理用户架构相关联的默认表空间。  
  
 **为项目日志记录表指定表空间**：  
  
-   在 **“项目属性”** 对话框中指定表空间。 有关访问此对话框的详细信息，请参阅 [View and Modify Publication Properties](../publish/view-and-modify-publication-properties.md)。  
  
-   使用 [sp_changearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)。 若要使用 **sp_changearticle**，请指定下列内容：  
  
    -   参数**@publisher**的 Oracle 发布服务器的名称。  
  
    -   参数**@publication**的 Oracle 发布的名称。  
  
    -   参数**@article**的项目名称。  
  
    -   参数**@property**的 "表空间" 的值。  
  
    -   参数**@value**表空间的名称。  
  
## <a name="see-also"></a>另请参阅  
 [配置 Oracle 发布服务器](configure-an-oracle-publisher.md)   
 [在 Oracle 发布服务器上创建的对象](objects-created-on-the-oracle-publisher.md)  
  
  
