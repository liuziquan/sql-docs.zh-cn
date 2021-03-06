---
title: 适用于 OLE DB 的 Microsoft 游标服务（ADO 服务组件） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], cursor service for OLE DB
- cursor service for OLE DB [ADO]
ms.assetid: 420d0989-7cfb-4c66-a7b5-f4199d13165d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e7e5b9a973e5ccf04f92a2162d88ee25b7fa5242
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926796"
---
# <a name="microsoft-cursor-service-for-ole-db-overview"></a>OLE DB 的 Microsoft 游标服务概述
适用于 OLE DB 的 Microsoft 游标服务对数据提供程序的游标支持函数进行了补充。 因此，用户从所有数据访问接口体验的功能相对比较统一。

 游标服务使动态属性可用，并增强某些方法的行为。 例如，通过 "[优化](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)动态属性"，可以创建临时索引以简化特定操作，例如[Find](../../../ado/reference/ado-api/find-method-ado.md)方法。

 在所有情况下，游标服务都支持批处理更新。 当数据访问接口只能提供不太好的游标（如静态游标）时，它还会模拟更有功能的游标类型（如动态游标）。

## <a name="keyword"></a>关键字
 若要调用此服务组件，请将[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)或[连接](../../../ado/reference/ado-api/connection-object-ado.md)对象的[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)属性设置为**adUseClient**。

```vb
connection.CursorLocation=adUseClient
recordset.CursorLocation=adUseClient
```

## <a name="dynamic-properties"></a>动态属性
 调用 OLE DB 的游标服务时，会将以下动态属性添加到**Recordset**对象的[properties](../../../ado/reference/ado-api/properties-collection-ado.md)集合。 [ADO 动态属性索引](../../../ado/reference/ado-api/ado-dynamic-property-index.md)中列出了**连接**和**记录集**对象的完整列表。 关联的 OLE DB 属性名称（在适当的情况下）包含在 ADO 属性名称后的括号中。

 调用游标服务后，对某些动态属性所做的更改对基础数据源不可见。 例如，在基础数据访问接口中，对**记录集**设置*命令*"超时" 属性将不可见。

```vb

Recordset1.CursorLocation = adUseClient     'invokes cursor service
Recordset1.Open "authors", _
    "Provider=SQLOLEDB;Data Source=DBServer;User Id=MyUserID;" & _
    "Password=MyPassword;Initial Catalog=pubs;",,adCmdTable
Recordset1.Properties.Item("Command Time out") = 50
' 'Command Time out' property on DBServer is still default (30).

```

 如果你的应用程序需要游标服务，但你需要在基础提供程序上设置动态属性，请在调用游标服务之前设置属性。 命令对象属性设置始终传递到基础数据提供程序，而不考虑游标位置。 因此，你也可以随时使用命令对象来设置属性。

> [!NOTE]
>  游标服务不支持动态属性 DBPROP_SERVERDATAONINSERT，即使基础数据提供程序支持该属性。

|属性名称|说明|
|-------------------|-----------------|
|自动重新计算（DBPROP_ADC_AUTORECALC）|对于用数据定形服务创建的记录集，此值指示计算计算列和聚合列计算的频率。 每当数据定形服务确定值已更改时，默认值（值 = 1）就会重新计算。 如果该值为0，则仅在首次生成层次结构时计算计算列或聚合列。|
|批大小（DBPROP_ADC_BATCHSIZE）|指示在发送到数据存储之前可以批处理的 update 语句的数目。 批处理中的语句越多，数据存储的往返次数就越少。|
|缓存子行（DBPROP_ADC_CACHECHILDROWS）|对于使用数据定形服务创建的记录集，此值指示子记录集是否存储在缓存中供以后使用。|
|游标引擎版本（DBPROP_ADC_CEVER）|指示所使用的游标服务的版本。|
|维护更改状态（DBPROP_ADC_MAINTAINCHANGESTATUS）|指示用于在多表联接中重新同步一个或多个行的命令文本。|
|[平台](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|指示是否应创建索引。 如果设置为**True**，则会授权创建索引的临时创建，以改进特定操作的执行。|
|[调整名称](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|指示**记录集**的名称。 可在当前的或后续的数据定形命令内引用。|
|[重新同步命令](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|指示当[Unique Table](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)属性有效时， [Resync](../../../ado/reference/ado-api/resync-method.md)方法使用的自定义命令字符串。|
|[唯一目录](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|指示包含**唯一表**属性中引用的表的数据库的名称。|
|[唯一架构](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|指示**Unique 表**属性中引用的表的所有者的名称。|
|[唯一表](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|指示**记录集中**从可以通过插入、更新或删除操作修改的多个表创建的一个表的名称。|
|更新条件（DBPROP_ADC_UPDATECRITERIA）|指示使用**WHERE**子句中的哪些字段来处理更新期间发生的冲突。|
|[更新重新同步](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)（DBPROP_ADC_UPDATERESYNC）|指示当**Unique Table**属性有效时是否隐式调用**Resync** [方法（](../../../ado/reference/ado-api/updatebatch-method.md)及其行为）。|

 还可以通过将动态属性的名称指定为**Properties**集合的索引来设置或检索该属性。 例如，获取并打印[优化](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)动态属性的当前值，然后设置新值，如下所示：

```vb
Debug.Print rs.Properties("Optimize")
rs.Properties("Optimize") = True
```

## <a name="built-in-property-behavior"></a>内置属性行为
 OLE DB 的游标服务还会影响某些内置属性的行为。

|属性名称|说明|
|-------------------|-----------------|
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|对可用于**记录集**的游标类型进行补充。|
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|对**记录集**的可用锁类型进行补充。 启用批更新。|
|[排序](../../../ado/reference/ado-api/sort-property.md)|指定**记录集**的一个或多个字段名称，以及是否按升序或降序对每个字段进行排序。|

## <a name="method-behavior"></a>方法行为
 OLE DB 的游标服务可以启用或影响[Field](../../../ado/reference/ado-api/field-object.md)对象[Append](../../../ado/reference/ado-api/append-method-ado.md)方法的行为;和**Recordset**对象的[Open](../../../ado/reference/ado-api/open-method-ado-recordset.md)、 [Resync](../../../ado/reference/ado-api/resync-method.md)、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)和[Save](../../../ado/reference/ado-api/save-method.md)方法。
