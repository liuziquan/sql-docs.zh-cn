---
title: 安装类型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 0420c555-7a3b-42b9-8651-0b4f5bcb0008
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b8812bba6d87e29ed8a4533bb87e645f42120015
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "66094293"
---
# <a name="installation-type"></a>安装类型
  使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导的“安装类型”页可以指定是安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的新实例还是向现有实例中添加功能。  
  
## <a name="options"></a>选项  
 选择指示您所做选择的单选按钮：  
  
-   执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的全新安装  
  
-   向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的现有实例中添加功能  
  
     如果选择与向现有实例中添加功能相对应的选项，则使用下拉列表选择要更新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。  
  
 只能向的[!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]已准备映像添加 SysPrep 支持的[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]功能。 只有在已准备实例完成后，才能添加 SysPrep 不支持的其他功能。  
  
 **注意**安装故障转移群集实例后，不能将其添加到故障转移群集实例。 若要向现有故障转移群集中添加 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能，则必须执行全新安装才能安装单独的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。  
  
  
