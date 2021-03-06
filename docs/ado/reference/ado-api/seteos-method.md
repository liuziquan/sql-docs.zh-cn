---
title: SetEOS 方法 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SetEOS
- _Stream::SetEOS
helpviewer_keywords:
- SetEOS method [ADO]
ms.assetid: 707c18ca-6a56-4970-bbd6-ae1fb86a0b8a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 357778765f0c7ac59d924518340ca34226853fc0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67916935"
---
# <a name="seteos-method"></a>SetEOS 方法
设置流的结束位置。  
  
## <a name="syntax"></a>语法  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>备注  
 **SetEOS**通过[使当前位置成为流末尾，来](../../../ado/reference/ado-api/position-property-ado.md)更新[EOS](../../../ado/reference/ado-api/eos-property.md)属性的值。 位于当前位置后面的任何字节或字符都将被截断。  
  
 由于[Write](../../../ado/reference/ado-api/write-method.md)、 [WriteText](../../../ado/reference/ado-api/writetext-method.md)和[CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md)不会截断现有**流**对象中的任何额外值，因此可以通过使用**SetEOS**设置新的流末尾位置来截断这些字节或字符。  
  
> [!CAUTION]
>  如果将**EOS**设置为流的实际末尾之前的位置，则会丢失新的**EOS**位置之后的所有数据。  
  
## <a name="applies-to"></a>应用于  
 [流对象 (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
