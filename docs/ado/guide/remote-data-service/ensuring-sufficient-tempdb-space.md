---
title: 确保 TempDB 空间充足 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- TempDB space in RDS [ADO]
ms.assetid: 09130db1-6248-4234-a1e5-a9c8e1622c06
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fe377cd15f2b95577a561e6784f78113b2843d07
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922650"
---
# <a name="ensuring-sufficient-tempdb-space"></a>确保足够的 TempDB 空间
如果处理需要在 Microsoft SQL Server 6.5 上处理空间的[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)对象时出现错误，则可能需要增加 TempDB 的大小。 （某些查询需要临时处理空间; 例如，使用 ORDER BY 子句的查询需要对**记录集**进行排序，这需要一些临时空间。）  
  
> [!IMPORTANT]
>  从 Windows 8 和 Windows Server 2012 开始，Windows 操作系统中不再包含 RDS 服务器组件（有关详细信息，请参阅 Windows 8 和[Windows Server 2012 兼容性指南](https://www.microsoft.com/download/details.aspx?id=27416)）。 在 Windows 的未来版本中将删除 RDS 客户端组件。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 使用 RDS 的应用程序应迁移到[WCF 数据服务](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
> [!IMPORTANT]
>  请在执行操作之前通读此过程，因为扩展设备后，不能轻松地对其进行收缩。  
  
> [!NOTE]
>  默认情况下，inMicrosoft SQL Server 7.0 及更高版本，TempDB 设置为根据需要自动增长。 因此，只有运行版本低于7.0 的服务器才需要执行此过程。  
  
### <a name="to-increase-the-tempdb-space-on-sql-server-65"></a>增加 SQL Server 6.5 上的 TempDB 空间  
  
1.  启动 Microsoft SQL Server Enterprise 管理器 "，打开服务器树，然后打开" 数据库设备 "树。  
  
2.  选择要展开的（物理）设备（例如 Master），然后双击设备以打开 "**编辑数据库设备**" 对话框。  
  
     此对话框显示当前数据库正在使用的空间量。  
  
3.  在 "**大小**" 框中，将设备提高到所需的容量（例如，50 mb 的硬盘空间）。  
  
4.  单击 "**立即更改**" 以增加（逻辑） TempDB 可扩展到的空间量。  
  
5.  打开服务器上的 "数据库" 树，然后双击 " **TempDB** " 以打开 "**编辑数据库**" 对话框。 "**数据库**" 选项卡列出当前分配给 TempDB 的空间量（**数据大小**）。 默认情况下，此值为 2 MB。  
  
6.  在 "**大小**" 组下，单击 "**展开**"。 此图显示了每个物理设备上可用和已分配的空间。 褐紫红色颜色栏表示可用空间。  
  
7.  选择要在 "**大小（MB）** " 框中显示可用大小的**日志设备**，如 "Master"。  
  
8.  单击 "**立即扩展**" 可将该空间分配给 TempDB 数据库。  
  
     "**编辑数据库**" 对话框显示 TempDB 的新分配大小。  
  
 有关此主题的详细信息，请在 Microsoft SQL Server Enterprise 管理器帮助文件中搜索 "展开数据库对话框"。  
  
## <a name="see-also"></a>另请参阅  
 [RDS 基础知识](../../../ado/guide/remote-data-service/rds-fundamentals.md)


