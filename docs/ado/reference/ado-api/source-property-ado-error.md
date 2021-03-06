---
title: Source 属性（ADO 错误） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::get_Source
- Error::Source
- Error::GetSource
helpviewer_keywords:
- Source property [ADO Error]
ms.assetid: 4044ba15-f013-4c4c-9fe1-b4410fe9a778
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6b55ebbe5a167b7d70cf606fc4e37e7ede36b486
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67916906"
---
# <a name="source-property-ado-error"></a>Source 属性（ADO 错误）
指示最初生成错误的对象或应用程序的名称。  
  
## <a name="return-value"></a>返回值  
 返回一个**字符串**值，该值指示对象或应用程序的名称。  
  
## <a name="remarks"></a>备注  
 使用[错误](../../../ado/reference/ado-api/error-object.md)对象上的**Source**属性来确定最初生成错误的对象或应用程序的名称。 这可能是对象的类名或编程 ID。 对于 ADO 中的错误，属性值将为**adodb.recordset。**_Objectname_，其中*objectname*是触发错误的对象的名称。 对于 ADOX 和 ADO MD，该值将为**adox。**_ObjectName_和**ADOMD。**_ObjectName_。  
  
 根据**错误**对象的 "**源**"、"[编号](../../../ado/reference/ado-api/number-property-ado.md)" 和 "[说明](../../../ado/reference/ado-api/description-property.md)" 属性中的错误文档，您可以编写将相应处理错误的代码。  
  
 对于**Error**对象， **Source**属性是只读的。  
  
## <a name="applies-to"></a>应用于  
 [错误对象](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>另请参阅  
 [Description、HelpContext、帮助，NativeError、Number、Source 和 SQLState 属性示例（VB）](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description、HelpContext、帮助，NativeError、Number、Source 和 SQLState 属性示例（VC + +）](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description 属性](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext，帮助的属性](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Number 属性（ADO）](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source 属性（ADO 记录）](../../../ado/reference/ado-api/source-property-ado-record.md)   
 [Source 属性（ADO 记录集）](../../../ado/reference/ado-api/source-property-ado-recordset.md)
