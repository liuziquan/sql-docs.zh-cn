---
title: STGeomCollFromText（geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeomCollFromText_TSQL
- STGeomCollFromText (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeomCollFromText (geometry Data Type)
ms.assetid: 19e757b3-cb2e-4852-87b9-40a815ab707e
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 7b4398107b11ff0bb1764dc70e4af24af082aeb4
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2020
ms.locfileid: "68107707"
---
# <a name="stgeomcollfromtext-geometry-data-type"></a>STGeomCollFromText（geometry 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

从开放地理空间信息联盟 (OGC) 熟知文本 (WKT) 表示形式返回 geometry 实例，增加了该实例传递的任何 Z（标高）和 M（度量）值  。
  
## <a name="syntax"></a>语法  
  
```  
  
STGeomCollFromText ( 'geometrycollection_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>参数  
 geometrycollection_tagged_text   
 希望返回的 **geometry** 实例的 WKT 表示形式。 geometry_tagged_text 是一个 nvarchar(max) 表达式   。  
  
 SRID   
 一个 int 表达式，表示希望返回的 geometry 实例的空间引用 ID (SRID)   。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：geometry   
  
 CLR 返回类型：SqlGeometry   
  
## <a name="remarks"></a>备注  
 **返回的**geometry`STGeomCollFromText()` 实例的 OGC 类型设置为相应的 WKT 输入。  
  
 如果输入无效，此方法将引发异常。  
  
## <a name="examples"></a>示例  
 下面的示例使用 `STGeomCollFromText()` 创建几何图形实例。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION ( POLYGON((5 5, 10 5, 10 10, 5 5)), POINT(10 10) )', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>另请参阅  
 [OGC 静态几何图形方法](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

