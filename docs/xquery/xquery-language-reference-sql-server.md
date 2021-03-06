---
title: XQuery 语言参考 （SQL 服务器） |微软文档
description: 了解 SQL Server 的 XQuery 语言并查看完整的语言参考。
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
helpviewer_keywords:
- XQuery
- XQuery, about XQuery
- xml data type [SQL Server], XQuery
- XML [SQL Server], XQuery
- queries [XML in SQL Server], XQuery
ms.assetid: 8a69344f-2990-4357-8160-cb26aac95b91
author: rothja
ms.author: jroth
ms.openlocfilehash: 35a1418e416e32ab5b8dc9647c4a9aa24700b624
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388616"
---
# <a name="xquery-language-reference-sql-server"></a>Xquery 语言参考 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[tsql](../includes/tsql-md.md)]支持用于查询**xml**数据类型的 XQuery 语言的子集。 此 XQuery 实现符合 2004 年 7 月的 XQuery 工作草案。 该语言正在由 World Wide Web 联合会 (W3C) 开发，所有主要数据库供应商和 Microsoft 也参与此开发。 由于 W3C 规范在成为 W3C 建议之前还可能进行修订，因此此实现可能与最终的建议有所不同。 本主题概要介绍了 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中所支持的 XQuery 子集的语义和语法。  
  
 有关详细信息，请参阅[W3C XQuery 1.0 语言规范](https://go.microsoft.com/fwlink/?LinkId=48846)。  
  
 XQuery 是一种可以查询结构化或半结构化 XML 数据的语言。 使用**xml**中[!INCLUDE[ssDE](../includes/ssde-md.md)]提供的 xml 数据类型支持，文档可以存储在数据库中，然后使用 XQuery 进行查询。  
  
 XQuery 基于现有的 XPath 查询语言，并支持更好的迭代、更好的排序结果以及构造必需的 XML 的功能。 XQuery 在 XQuery 数据模型上运行。 此模型是 XML 文档以及可能为类型化也可能为非类型化的 XQuery 结果的抽象概念。 类型信息基于 W3C XML 架构语言所提供的类型。 如果没有可用的类型化信息，XQuery 将按照非类型化处理数据。 这与 XPath 1.0 版处理 XML 的方式相似。  
  
 要查询存储在**xml**类型的变量或列中的 XML 实例，请使用[xml 数据类型方法](../t-sql/xml/xml-data-type-methods.md)。 例如，可以使用**xml**数据类型的**query（）** 方法声明**xml**类型的变量并查询它。  
  
```sql
DECLARE @x xml  
SET @x = '<ROOT><a>111</a></ROOT>'  
SELECT @x.query('/ROOT/a')  
```  
  
 在下面的示例中，根据 AdventureWorks 数据库中产品模型表中的**xml**类型的指令列指定查询。  
  
```sql
SELECT Instructions.query('declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";           
    /AWMI:root/AWMI:Location[@LocationID=10]  
') as Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 XQuery 包括命名空间声明`declare namespace``AWMI=...`和 查询表达式 。 `/AWMI:root/AWMI:Location[@LocationID=10]`  
  
 请注意，XQuery 是针对**xml**类型的指令列指定的。 xml 数据类型的[查询（） 方法](../t-sql/xml/query-method-xml-data-type.md)用于指定 XQuery。  
  
 下表列出了有助于理解如何在 [!INCLUDE[ssDE](../includes/ssde-md.md)]中实现 XQuery 的相关主题。  
  
|主题|说明|  
|-----------|-----------------|  
|[XML 数据 (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)|解释 对 xml**数据类型的支持**[!INCLUDE[ssDE](../includes/ssde-md.md)]以及可针对此数据类型使用的方法。 **xml**数据类型形成执行 XQuery 表达式的输入 XQuery 数据模型。|  
|[XML 架构集合 (SQL Server)](../relational-databases/xml/xml-schema-collections-sql-server.md)|说明如何类型化数据库中存储的 XML 实例。 这意味着您可以将 XML 架构集合与**xml**类型列相关联。 列中存储的所有实例根据集合中的架构进行验证和类型化，并为 XQuery 提供类型信息。|  
|||  
  
> [!NOTE]  
>  本部分的组织结构基于 World Wide Web 联合会 (W3C) XQuery 工作草案规范。 本部分中的某些关系图是从该规范得到的。 本部分将 Microsoft XQuery 实现与 W3C 规范进行比较，介绍 Microsoft XQuery 与 W3C 的不同之处并指明不支持的 W3C 功能。 W3C 规格可在 。 [http://www.w3.org/TR/2004/WD-xquery-20040723](https://go.microsoft.com/fwlink/?LinkId=48846)  
  
## <a name="in-this-section"></a>本节内容  
  
|主题|说明|  
|-----------|-----------------|  
|[XQuery 基础知识](../xquery/xquery-basics.md)|简要介绍了 XQuery 概念，以及表达式计算（静态和动态上下文）、原子化、有效的布尔值、XQuery 类型系统、序列类型匹配和错误处理。|  
|[XQuery 表达式](../xquery/xquery-expressions.md)|介绍 XQuery 主表达式、路径表达式、序列表达式、算术比较和逻辑表达式、XQuery 构造、FLWOR 表达式、条件和定量表达式以及序列类型的各种表达式。|  
|[模块和 Prologs &#40;XQuery&#41;](../xquery/modules-and-prologs-xquery.md)|介绍 XQuery prolog。|  
|[针对 xml 数据类型的 XQuery 函数](../xquery/xquery-functions-against-the-xml-data-type.md)|介绍支持的一系列 XQuery 函数。|  
|[针对 xml 数据类型的 XQuery 运算符](../xquery/xquery-operators-against-the-xml-data-type.md)|介绍支持的 XQuery 运算符。|  
|[针对 xml 数据类型的其他示例 XQuery](../xquery/additional-sample-xqueries-against-the-xml-data-type.md)|提供附加的 XQuery 示例。|  
  
## <a name="see-also"></a>另请参阅  
 [XML 数据&#40;SQL 服务器&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [&#40;SQL Server&#41;的 XML 架构集合](../relational-databases/xml/xml-schema-collections-sql-server.md)   
 [批量导入和导出 XML 文档的示例 (SQL Server)](../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
  
