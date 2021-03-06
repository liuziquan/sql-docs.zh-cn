---
title: 查找转换编辑器（"高级" 页） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.advanced.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: f3395c65-0320-47f9-8d83-daaa082d8713
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f78c568d467601b2f23ae8952036764ea2b464d8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057882"
---
# <a name="lookup-transformation-editor-advanced-page"></a>查找转换编辑器（“高级”页）
  可以使用 **“查找转换编辑器”** 对话框的 **“高级”** 页，配置部分缓存以及修改查找转换的 SQL 语句。  
  
 若要了解有关查找转换的详细信息，请参阅 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)。  
  
## <a name="options"></a>选项  
 **缓存大小（32位）**  
 调整 32 位计算机的缓存大小 (MB)。 默认值为 5 MB。  
  
 **缓存大小（64位）**  
 调整 64 位计算机的缓存大小 (MB)。 默认值为 5 MB。  
  
 **为没有匹配项的行启用缓存**  
 缓存在引用数据集内没有匹配项的行。  
  
 **从缓存分配**  
 指定要针对在引用数据集内没有匹配项的行分配的缓存所占的百分比。  
  
 **修改 SQL 语句**  
 修改用来生成引用数据集的 SQL 语句。  
  
> [!NOTE]  
>  在此页上指定的可选 SQL 语句将覆盖并替换在 **“查找转换编辑器”** 的 **“高级”** 页上指定的表名。 有关详细信息，请参阅 [查找转换编辑器（“连接”页）](../../2014/integration-services/lookup-transformation-editor-connection-page.md)。  
  
 **设置参数**  
 使用“设置查询参数”**** 对话框将输入列映射到参数。  
  
## <a name="external-resources"></a>外部资源  
 blogs.msdn.com 上的博客文章： [查找缓存模式](https://go.microsoft.com/fwlink/?LinkId=219518)  
  
## <a name="see-also"></a>另请参阅  
 [查找转换编辑器 &#40;常规页&#41;](general-page-of-integration-services-designers-options.md)   
 [查找转换编辑器 &#40;连接页&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)   
 [查找转换编辑器（“列”页）](../../2014/integration-services/lookup-transformation-editor-columns-page.md)   
 [查找转换编辑器 &#40;错误输出页&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)   
 [Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [模糊查找转换](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
