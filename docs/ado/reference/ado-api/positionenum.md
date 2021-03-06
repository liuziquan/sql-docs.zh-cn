---
title: PositionEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PositionEnum
helpviewer_keywords:
- PositionEnum enumeration
ms.assetid: e69af0a5-3405-4b72-9c6e-6b188ff746fd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d5f7ca47177a953313ff983bb25f9178b73b4930
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917607"
---
# <a name="positionenum"></a>PositionEnum
指定记录指针在[记录集中](../../../ado/reference/ado-api/recordset-object-ado.md)的当前位置。  
  
|一直|值|说明|  
|--------------|-----------|-----------------|  
|**adPosBOF**|-2|指示当前记录指针处于 BOF （即[bof](../../../ado/reference/ado-api/bof-eof-properties-ado.md)属性为**True**）。|  
|**adPosEOF**|-3|指示当前记录指针位于 EOF （即[eof](../../../ado/reference/ado-api/bof-eof-properties-ado.md)属性为**True**）。|  
|**adPosUnknown**|-1|指示**记录集**为空，当前位置未知，或者提供程序不支持[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)或[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)属性。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 等效项  
 Package： **.com. 数据**  
  
|一直|  
|--------------|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums。未知|  
  
## <a name="applies-to"></a>应用于  
  
|||  
|-|-|  
|[AbsolutePage 属性 (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)|[AbsolutePosition 属性 (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|
