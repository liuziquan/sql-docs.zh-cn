---
title: CreateObject 方法（RDS） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- CreateObject method [ADO]
ms.assetid: dec96be6-0b31-4953-9c9a-e962b5afcd18
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c6b50714cdff536418e759828d972c16abd7d7a0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964548"
---
# <a name="createobject-method-rds"></a>CreateObject 方法 (RDS)
为目标业务对象创建代理并返回指向它的指针。 代理会将数据打包并封送到服务器端存根，以便与业务对象通信，以便通过 Internet 发送请求和数据。 对于进程内组件对象，不使用代理，只提供指向对象的指针。  
  
> [!IMPORTANT]
>  从 Windows 8 和 Windows Server 2012 开始，Windows 操作系统中不再包含 RDS 服务器组件（有关详细信息，请参阅 Windows 8 和[Windows Server 2012 兼容性指南](https://www.microsoft.com/download/details.aspx?id=27416)）。 在 Windows 的未来版本中将删除 RDS 客户端组件。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 使用 RDS 的应用程序应迁移到[WCF 数据服务](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="syntax"></a>语法  
 远程数据服务支持以下协议： HTTP、HTTPS （安全套接字层上的 HTTP）、DCOM 和进程内。  
  
|协议|语法|  
|--------------|------------|  
|HTTP|Set object = CreateObject （"ProgId"，"https\://awebsrvr"）|  
|HTTPS|Set object = CreateObject （"ProgId"，"https\://awebsrvr"）|  
|DCOM|Set object = DataSpace.CreateObject("ProgId", "computername")|  
|进程内|Set object = DataSpace.CreateObject("ProgId", "")|  
  
## <a name="parameters"></a>parameters  
 *Object*  
 一个对象变量，其计算结果为作为*ProgID*中指定的类型的对象。  
  
 *空间*  
 表示 RDS 的对象变量[。](../../../ado/reference/rds-api/dataspace-object-rds.md)用于创建新对象的实例的空间对象。  
  
 *ProgID*  
 一个**字符串**值，该值包含编程标识符，该标识符指定实现应用程序业务规则的服务器端业务对象。  
  
 *awebsrvr*或*computername*  
 一个**字符串**值，表示用于标识在其中创建服务器业务对象实例的 INTERNET INFORMATION SERVICES （IIS） Web 服务器的 URL。  
  
## <a name="remarks"></a>备注  
 *HTTP 协议*是标准 Web 协议;*HTTPS*是一种安全的 Web 协议。 在不使用 HTTP 的情况下运行局域网时使用*DCOM 协议*。 *进程内*协议为本地动态链接库（DLL）;它不使用网络。  
  
## <a name="applies-to"></a>应用于  
 [DataSpace 对象 (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)  
  
## <a name="see-also"></a>另请参阅  
 [DataFactory 对象、查询方法和 CreateObject 方法示例（VBScript）](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)   
 [空间对象和 CreateObject 方法示例（VBScript）](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)   
 [CreateRecordset 方法 (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)


