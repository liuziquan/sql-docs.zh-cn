---
title: Update 方法 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Update
helpviewer_keywords:
- Update method [ADO]
ms.assetid: 6b2a9c31-1a7e-40db-8a53-30720d0f6cc1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6ce247905afd6ed34366424f5f905d57b42d988f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938843"
---
# <a name="update-method"></a>Update 方法
保存对记录[集](../../../ado/reference/ado-api/recordset-object-ado.md)对象的当前行所做的任何更改，或[记录](../../../ado/reference/ado-api/record-object-ado.md)对象的[字段](../../../ado/reference/ado-api/fields-collection-ado.md)集合。  
  
## <a name="syntax"></a>语法  
  
```  
  
recordset.Update Fields, Values  
record.Fields.Update  
```  
  
#### <a name="parameters"></a>parameters  
 *Fields*  
 可选。 表示单个名称的**变量**，或表示要修改的一个或多个字段的名称或序号位置的**variant**数组。  
  
 *值*  
 可选。 一个表示单个值的**变量**，或一个表示新记录中的一个或多个字段的值的**变体**数组。  
  
## <a name="remarks"></a>备注  
  
## <a name="recordset"></a>记录集  
 使用**Update**方法保存对**记录集**对象的当前记录所做的任何更改，因为调用了[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)方法或更改了现有记录中的任何字段值。 **Recordset**对象必须支持更新。  
  
 若要设置字段值，请执行以下操作之一：  
  
-   为[字段](../../../ado/reference/ado-api/field-object.md)对象的[Value](../../../ado/reference/ado-api/value-property-ado.md)属性赋值，并调用**Update**方法。  
  
-   使用**更新**调用作为参数传递字段名称和值。  
  
-   使用**更新**调用传递字段名称和值数组的数组。  
  
 使用字段和值的数组时，两个数组中的元素数必须相等。 并且字段名称的顺序必须与字段值的顺序匹配。 如果字段和值的数量和顺序不匹配，将发生错误。  
  
 如果**Recordset**对象支持批处理更新，则可以在调用[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)方法之前，将多个更改缓存到本地一个或多个记录。 如果在调用**UpdateBatch**方法时编辑当前记录或添加新记录，ADO 将自动调用**Update**方法，以便在将批处理更改传输到提供程序之前保存当前记录的所有挂起的更改。  
  
 如果在调用**update**方法之前从要添加或编辑的记录中移动，ADO 将自动调用**update**以保存更改。 如果要取消对当前记录所做的任何更改，或者放弃新添加的记录，则必须调用[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)方法。  
  
 在调用**Update**方法之后，当前记录保持为最新。  
  
## <a name="record"></a>Record  
 **Update**方法完成对**Record**对象的[fields](../../../ado/reference/ado-api/fields-collection-ado.md)集合中的字段的添加、删除和更新。  
  
 例如，**删除方法删除的字段**会立即标记为删除，但仍保留在集合中。 若要实际从提供程序的集合中删除这些字段，必须调用**Update**方法。  
  
## <a name="applies-to"></a>应用于  
  
|||  
|-|-|  
|[字段集合 (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>另请参阅  
 [Update 和 CancelUpdate 方法示例（VB）](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vb.md)   
 [Update 和 CancelUpdate 方法示例（VC + +）](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vc.md)   
 [AddNew 方法（ADO）](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [CancelUpdate 方法（ADO）](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [EditMode 属性](../../../ado/reference/ado-api/editmode-property.md)   
 [UpdateBatch 方法](../../../ado/reference/ado-api/updatebatch-method.md)
