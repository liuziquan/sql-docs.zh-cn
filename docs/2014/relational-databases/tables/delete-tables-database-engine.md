---
title: 删除表（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table deletions [SQL Server]
- deleting tables
- removing tables
- dropping tables
ms.assetid: ca6aa3e9-9885-44c3-bafc-aec441fd97ec
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f040c9907574bba718827999bb9c0fbb432a0bd0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "62761436"
---
# <a name="delete-tables-database-engine"></a>删除表（数据库引擎）
  您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中从您的数据库中删除表。  
  
> [!CAUTION]  
>  删除表之前一定要慎重考虑。 如果现有查询、视图、用户定义函数、存储过程或程序引用该表，删除操作将使这些对象无效。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [限制和局限](#Restrictions)  
  
     [安全性](#Security)  
  
-   **使用以下工具删除表：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Restrictions"></a> 限制和局限  
  
-   不能删除被 FOREIGN KEY 约束引用的表。 必须先删除引用 FOREIGN KEY 约束或引用表。 如果要在同一个 DROP TABLE 语句中删除引用表以及包含主键的表，则必须先列出引用表。  
  
-   删除表时，表的规则或默认值将被解除绑定，与该表关联的任何约束或触发器将被自动删除。 如果要重新创建表，则必须重新绑定相应的规则和默认值，重新创建某些触发器，并添加所有必需的约束。  
  
-   如果删除的表包含带有 FILESTREAM 属性的 `varbinary (max)` 列，则不会删除在文件系统中存储的任何数据。  
  
-   不应在同一个批处理中对同一个表执行 DROP TABLE 和 CREATE TABLE。 否则，可能出现意外错误。  
  
-   任何引用已删除表的视图或存储过程都必须显式删除或修改，以便删除对该表的引用。  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> 权限  
 需要拥有该表所属架构的 ALTER 权限、该表的 CONTROL 权限或 **db_ddladmin** 固定数据库角色中的成员身份。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-delete-a-table-from-the-database"></a>从数据库中删除表  
  
1.  在对象资源管理器中选择要删除的表。  
  
2.  右键单击该表，再从快捷菜单中选择“删除”  。  
  
3.  此时，将显示一个消息框，提示您确认删除。 单击 **“是”** 。  
  
    > [!NOTE]  
    >  删除一个表将自动移除与该表之间的所有关系。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-delete-a-table-in-query-editor"></a>在查询编辑器中删除表  
  
1.  在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。  
  
2.  在标准菜单栏上，单击 **“新建查询”** 。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。  
  
    ```  
    DROP TABLE dbo.PurchaseOrderDetail;  
  
    ```  
  
 有关详细信息，请参阅 [DROP TABLE (Transact-SQL)](/sql/t-sql/statements/drop-table-transact-sql)。  
  
  
