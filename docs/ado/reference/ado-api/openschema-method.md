---
title: OpenSchema 方法 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::OpenSchema
- Connection15::raw_OpenSchema
helpviewer_keywords:
- OpenSchema method [ADO]
ms.assetid: 850cf3ce-f18f-4e7c-8597-96c1dc504866
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b2080145e00c658288f9d34e3fa42ed335e0c1d9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931864"
---
# <a name="openschema-method"></a>OpenSchema 方法
从提供程序中获取数据库架构信息。  
  
## <a name="syntax"></a>语法  
  
```  
  
Set recordset = connection.OpenSchema(QueryType, Criteria, SchemaID)  
```  
  
## <a name="return-value"></a>返回值  
 返回一个包含架构信息的[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)对象。 **记录集**将作为只读静态游标打开。 *QueryType*确定在**记录集中**显示的列。  
  
#### <a name="parameters"></a>parameters  
 *QueryType*  
 表示要运行的架构查询类型的任何[SchemaEnum](../../../ado/reference/ado-api/schemaenum.md)值。  
  
 *条件*  
 可选。 每个*QueryType*选项的查询约束数组，如[SchemaEnum](../../../ado/reference/ado-api/schemaenum.md)中所列。  
  
 *SchemaID*  
 OLE DB 规范未定义的提供程序架构查询的 GUID。 如果将*QueryType*设置为**adSchemaProviderSpecific**，则此参数是必需的。否则，不使用此方法。  
  
## <a name="remarks"></a>备注  
 **OpenSchema**方法返回有关数据源的自定义信息，如数据源中的表、表中的列以及支持的数据类型。  
  
 *QueryType*参数是一个 GUID，它指示返回的列（架构）。 OLE DB 规范包含架构的完整列表。  
  
 *Criteria*参数限制架构查询的结果。 *条件*指定值的数组，这些值必须出现在生成的**记录集中**的列的相应子集（称为约束列）中。  
  
 如果提供程序定义了其自己的非标准架构查询（在前面列出）之外，则常量**adSchemaProviderSpecific**用于*QueryType*参数。 使用此常量时，需要使用*SchemaID*参数来传递要执行的架构查询的 GUID。 如果*QueryType*设置为**adSchemaProviderSpecific** ，但未提供*SchemaID* ，则会产生错误。  
  
 提供程序不需要支持所有 OLE DB 标准架构查询。 具体而言，OLE DB 规范只需要**adSchemaTables**、 **adSchemaColumns**和**adSchemaProviderTypes** 。 但是，提供程序不需要支持前面列出的那些架构查询的*条件*约束。  
  
> [!NOTE]
>  **远程数据服务使用情况****OpenSchema**方法在客户端[连接](../../../ado/reference/ado-api/connection-object-ado.md)对象上不可用。  
  
> [!NOTE]
>  在 Visual Basic 中，在**连接**对象上从**OpenSchema**方法返回的**记录集中**具有四字节无符号整数（DBTYPE UI4）的列不能与其他变量进行比较。 有关 OLE DB 数据类型的详细信息，请参阅[OLE DB 中的数据类型（OLE DB）](https://msdn.microsoft.com/6039292f-74e0-49b2-b133-17bc117ebf6a)和[附录 A：](https://msdn.microsoft.com/e3a0533a-2196-4eb0-a31e-92fe9556ada6) Microsoft OLE DB 程序员参考中的数据类型。  
  
> [!NOTE]
>  **Visual c/c + + 用户**在不使用客户端游标的情况下，在 ADO 中检索列架构的 "ORDINAL_POSITION" 将返回 MDAC 2.7、MDAC 2.8 和 Windows 数据访问组件（Windows DAC） 6.0 VT_R8 类型的变体，而在 MDAC 2.6 中使用的类型是 VT_I4 的。 对于 MDAC 2.6 编写的程序，仅查找类型为 VT_I4 返回的变量，如果在不进行修改的情况下，将在 MDAC 2.7、MDAC 2.8 和 Windows DAC 6.0 下运行。 此更改是因为 OLE DB 返回的数据类型是 DBTYPE_UI4 的，而在已签名的 VT_I4 类型中没有足够的空间来包含所有可能的值，而不会发生截断，从而导致数据丢失。  
  
## <a name="applies-to"></a>应用于  
 [连接对象 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>另请参阅  
 [OpenSchema 方法示例（VB）](../../../ado/reference/ado-api/openschema-method-example-vb.md)   
 [OpenSchema 方法示例（VC + +）](../../../ado/reference/ado-api/openschema-method-example-vc.md)   
 [Open 方法（ADO 连接）](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open 方法（ADO 记录）](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open 方法（ADO 记录集）](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open 方法（ADO 流）](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [附录 A：提供程序](../../../ado/guide/appendixes/appendix-a-providers.md)
