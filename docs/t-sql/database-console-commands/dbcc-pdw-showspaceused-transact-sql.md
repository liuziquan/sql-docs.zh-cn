---
title: DBCC PDW_SHOWSPACEUSED (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 73f598cf-b02a-4dba-8d89-9fc0b55a12b8
author: pmasl
ms.author: umajay
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: f8c5d7ac822546d8334f1a174684f35733d9571b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2020
ms.locfileid: "68116494"
---
# <a name="dbcc-pdw_showspaceused-transact-sql"></a>DBCC PDW_SHOWSPACEUSED (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

显示特定表或者 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 或 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] 数据库中所有表的行数、保留的磁盘空间和已使用的磁盘空间。
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定 (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```sql
-- Show the space used for all user tables and system tables in the current database  
DBCC PDW_SHOWSPACEUSED  
[;]  
  
-- Show the space used for a table  
DBCC PDW_SHOWSPACEUSED ( " [ database_name . [ schema_name ] . ] | [ schema_name .] table_name  " )  
[;]  
```  
  
## <a name="arguments"></a>参数  
 `[ database_name . [ schema_name ] . | schema_name . ] table_name`  
 要显示的表格的名称（具有一、二、三个部分）。 对于具有二或三个部分的名称，名称必须使用双引号 ("") 括起来。 可选择是否使用引号将具有一个部分的表格名称括起来。 未指定表名时，则显示当前数据库中的信息。  
  
## <a name="permissions"></a>权限  
需要 VIEW SERVER STATE 权限。
  
## <a name="result-sets"></a>结果集  
下面是针对所有表的结果集。
  
|列|数据类型|说明|  
|------------|---------------|-----------------|  
|reserved_space|bigint|用于数据库的总空间，单位为 KB。|  
|data_space|bigint|用于数据的空间，单位为 KB。|  
|index_space|bigint|用于索引的空间，单位为 KB。|  
|unused_space|bigint|保留空间中未使用的空间，单位为 KB。|  
|pdw_node_id|int|要用于数据的计算节点。|  
  
下面是一个表的结果集。
  
|列|数据类型|说明|范围|  
|------------|---------------|-----------------|-----------|  
|行|bigint|行数。||  
|reserved_space|bigint|为对象保留的总空间，单位为 KB。||  
|data_space|bigint|用于数据的空间，单位为 KB。||  
|index_space|bigint|用于索引的空间，单位为 KB。||  
|unused_space|bigint|保留空间中未使用的空间，单位为 KB。||  
|pdw_node_id|int|用于报告空间使用量的计算节点。||  
|distribution_id|int|用于报告空间使用量的分发。|复制的表的值为 -1。|  
  
## <a name="examples-sssdw-and-sspdw"></a>示例：[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdw_showspaceused-basic-syntax"></a>A. DBCC PDW_SHOWSPACEUSED 基本语法  
以下示例演示了多种方式来显示 [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] 数据库中 FactInternetSales 表的行数、保留的磁盘空间和已使用的磁盘空间。
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012.dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012..FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( FactInternetSales );  
```  
  
### <a name="b-show-the-disk-space-used-by-all-tables-in-the-current-database"></a>B. 显示当前数据库中所有表已使用的磁盘空间  
 以下示例演示 [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] 数据库中所有用户表和系统表保留和已使用的磁盘空间。  
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED;  
```  
 ## <a name="see-also"></a>另请参阅
[DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL)](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)](dbcc-pdw-showpartitionstats-transact-sql.md)

  
