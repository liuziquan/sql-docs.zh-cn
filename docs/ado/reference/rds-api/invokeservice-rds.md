---
title: InvokeService （RDS） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- InvokeService [RDS]
ms.assetid: ad45c676-ec7e-4a3a-9a6b-a54f75eb3012
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 86ebb27ebdc5de5a045304afe45cd8653e491827
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963865"
---
# <a name="invokeservice-rds"></a>InvokeService (RDS)
返回一个指针，该指针指向对象的更好的版本上所请求的接口。  
  
> [!IMPORTANT]
>  从 Windows 8 和 Windows Server 2012 开始，Windows 操作系统中不再包含 RDS 服务器组件（有关详细信息，请参阅 Windows 8 和[Windows Server 2012 兼容性指南](https://www.microsoft.com/download/details.aspx?id=27416)）。 在 Windows 的未来版本中将删除 RDS 客户端组件。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 使用 RDS 的应用程序应迁移到[WCF 数据服务](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="syntax"></a>语法  
  
```  
  
object.InvokeService(REFID riid, IUknown* punkNotSoFunctionalInterface, IUknown** ppunkMoreFunctionalInterface) As HRESULT  
```  
  
#### <a name="parameters"></a>parameters  
 *riid*  
  
 中所请求的接口的标识符。  
  
 *punkNotSoFunctionalInterface*  
  
 中功能更少的源对象。  
  
 *ppunkMoreFunctionalInterface*  
  
 弄指针变量的地址，该变量接收在*riid*中请求的接口指针。 成功返回后， *ppunkMoreFunctionalInterface*参数包含指向对象的请求的接口指针。 如果对象不支持*riid*中指定的接口，则将*PPUNKMOREFUNCTIONALINTERFACE*设置为 NULL。  
  
## <a name="return-value"></a>返回值  
 一个 HRESULT 值，该值指示是否成功调用了**InvokeService**方法。  
  
## <a name="remarks"></a>备注  
 **InvokeService**的 RDS 游标引擎实现采用输入行集（或多个结果对象），在输入行集中填充游标引擎，然后在其自身上返回一个指针。  
  
## <a name="applies-to"></a>应用于  
 [IRDSService 接口 (RDS)](../../../ado/reference/rds-api/irdsservice-interface-rds.md)  
  
## <a name="see-also"></a>另请参阅  
 [RDS 方法](../../../ado/reference/rds-api/rds-methods.md)


