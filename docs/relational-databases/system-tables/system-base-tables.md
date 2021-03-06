---
title: 系统基表 |微软文档
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system base tables [SQL Server]
- hobt [SQL Server]
- base tables
ms.assetid: 31f2df90-651f-4699-8067-19f59b60904f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ac374b9222f9bd592312f79173859691b495276
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2020
ms.locfileid: "80531194"
---
# <a name="system-base-tables"></a>系统基表
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  系统基表是基础表，用于实际存储特定数据库的元数据。 **主**数据库在这方面是特殊的，因为它包含任何其他数据库中找不到的一些其他表。 这些表包含服务器范围内的持久化元数据。  
  
> [!IMPORTANT]  
>  系统基表仅在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]内使用，并且不能用于一般客户。 随时可能对其进行更改，不保证兼容性。  
  
## <a name="system-base-table-metadata"></a>系统基表元数据  
 在数据库上具有控制、ALTER 或 VIEW 定义权限的受让人可以在**sys.objects**目录视图中看到系统基表元数据。 受赠方还可以使用内置函数（如[OBJECT_NAME](../../t-sql/functions/object-name-transact-sql.md)和[OBJECT_ID）](../../t-sql/functions/object-id-transact-sql.md)解析系统基表的名称和对象 I。  
  
 若要绑定到系统基表，用户必须通过使用专用管理员连接 (DAC) 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。 如果在没有使用 DAC 进行连接的情况下尝试从系统基表执行 SELECT 查询，则会引发错误。  
  
> [!IMPORTANT]  
>  通过使用 DAC 访问系统基表的功能是专门为 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 人员设计的，它不是支持的客户方案。  
  
## <a name="system-base-tables"></a>系统基表  
 下表列出并描述了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的每个系统基表。  
  
|基表|说明|  
|----------------|-----------------|  
|**sys.sysschobjs**|存在于每个数据库中。 每一行表示数据库中的一个对象。|  
|**sys.sysbinobjs**|存在于每个数据库中。 数据库中的每个 Service Broker 实体都存在对应的一行。 Service Broker 实体包括以下内容：<br /><br /> 消息类型<br /><br /> 服务约定<br /><br /> 服务<br /><br /> 名称和类型使用固定的二进制排序规则。|  
|**sys.sysclsobjs**|存在于每个数据库中。 共享相同通用属性的每个分类实体均存在对应的一行，这些属性包括以下内容：<br /><br /> Assembly<br /><br /> 备份设备<br /><br /> 全文目录<br /><br /> 分区函数<br /><br /> 分区方案<br /><br /> 文件组<br /><br /> 模糊处理键|  
|**sys.sysnsobjs**|存在于每个数据库中。 每个命名空间范围内的实体均存在对应的一行。 此表用于存储 XML 集合实体。|  
|**sys.syscolpars**|存在于每个数据库中。 表、视图或表值函数的每个列均存在对应的一行。 过程或函数的每个参数也存在对应的行。|  
|**sys.systypedsubobjs**|存在于每个数据库中。 每个类型化的子实体均存在对应的一行。 只有分区函数的参数属于此类别。|  
|**sys.sysidxstats**|存在于每个数据库中。 表和索引视图的每个索引或统计信息均存在对应的一行<br /><br /> 注意：每个索引（堆除外）都与与索引同名的统计信息相关联。|  
|**sys.sysiscols**|存在于每个数据库中。 每个持久化索引和统计信息列均存在对应的一行。|  
|**sys.sysscalartypes**|存在于每个数据库中。 每个用户定义类型或系统类型均存在对应的一行。|  
|**sys.sysdbreg**|仅存在于**主**数据库中。 每个注册数据库均存在对应的一行。|  
|**sys.sysxsrvs**|仅存在于**主**数据库中。 每个本地服务器、链接服务器或远程服务器均存在对应的一行。|  
|**sys.sysrmtlgns**|此系统基表仅存在于**主**数据库中。 每个远程登录映射均存在对应的一行。 这用于将声明来自对应服务器的传入登录映射到实际本地登录。|  
|**sys.syslnklgns**|仅存在于**主**数据库中。 每个链接登录映射均存在对应的一行。 链接登录映射由远程过程调用和分布式查询使用，从本地服务器发出到对应的链接服务器。|  
|**sys.sysxlgns**|仅存在于**主**数据库中。 每个服务器主体均存在对应的一行。|  
|**sys.sysdbfiles**|存在于每个数据库中。 如果列**dBID**为零，则该行表示属于此数据库的文件。 在**主**数据库中，列**dbid**可以是非零。 如果是这样，该行表示主文件。|  
|**sys.sysusermsg**|仅存在于**主**数据库中。 每一行表示用户定义的错误消息。|  
|**sys.sysprivs**|存在于每个数据库中。 每个数据库或服务器级权限均存在对应的一行。<br /><br /> 注意：服务器级权限存储在**主**数据库中。|  
|**sys.sysowners**|存在于每个数据库中。 每一行表示一个数据库主体。|  
|**sys.sysobjkeycrypts**|存在于每个数据库中。 每个与对象关联的对称密钥、加密或加密属性均存在对应的一行。|  
|**sys.syscerts**|存在于每个数据库中。 数据库中的每个证书均存在对应的一行。|  
|**sys.sysasymkeys**|存在于每个数据库中。 每一行表示一个非对称密钥。|  
|**sys.ftinds**|存在于每个数据库中。 数据库中的每个全文索引均存在对应的一行。|  
|**sys.sysxprops**|存在于每个数据库中。 每个扩展属性均存在对应的一行。|  
|**sys.sysallocunits**|存在于每个数据库中。 每个存储分配单元均存在对应的一行。|  
|**sys.sysrowsets**|存在于每个数据库中。 索引或堆的每个分区行集均存在对应的一行。|  
|**sys.sysrowsetrefs**|存在于每个数据库中。 行集引用的每个索引均存在对应的一行。|  
|**sys.syslogshippers**|仅存在于**主**数据库中。 每个数据库镜像见证服务器均存在对应的一行。|  
|**sys.sysremsvcbinds**|存在于每个数据库中。 每个远程服务绑定均存在对应的一行。|  
|**sys.sysconvgroup**|存在于每个数据库中。 Service Broker 中的每个服务实例均存在对应的一行。|  
|**sys.sysxmitqueue**|存在于每个数据库中。 每个 Service Broker 传输队列均存在对应的一行。|  
|**sys.sysdesend**|存在于每个数据库中。 Service Broker 会话的每个发送端点均存在对应的一行。|  
|**sys.sysdercv**|存在于每个数据库中。 Service Broker 会话的每个接收端点均存在对应的一行。|  
|**sys.sysendpts**|仅存在于**主**数据库中。 服务器中创建的每个端点均存在对应的一行。|  
|**sys.syswebmethods**|仅存在于**主**数据库中。 对服务器中创建的启用 SOAP 的 HTTP 端点定义的每个 SOAP 方法均存在对应的一行。|  
|**sys.sysqnames**|存在于每个数据库中。 4 字节 ID 标记的每个命名空间或限定名均存在对应的一行。|  
|**sys.sysxmlcomponent**|存在于每个数据库中。 每一行表示一个 XML 架构组件。|  
|**sys.sysxmlfacet**|存在于每个数据库中。 具有 XML 类型定义的每个 XML 方面（限制）均存在对应的一行。|  
|**sys.sysxmlplacement**|存在于每个数据库中。 XML 组件的每个 XML 位置均存在对应的一行。|  
|**sys.syssingleobjrefs**|存在于每个数据库中。 每个常规 N 到 1 引用均存在对应的一行。|  
|**sys.sysmultiobjrefs**|存在于每个数据库中。 每个常规 N 到 N 引用均存在对应的一行。|  
|**sys.sysobjvalues**|存在于每个数据库中。 实体的每个常规值属性均存在对应的一行。|  
|**sys.sysguidrefs**|存在于每个数据库中。 每个 GUID 分类 ID 引用均存在对应的一行。|  
  
## <a name="updating-system-base-tables"></a>更新系统基本表    
您可以通过系统目录视图查看系统表中的数据。 要更新系统基表中的元数据，请使用适当的 TSQL 接口（例如，DDL 语句）。 无法手动更新系统表。 当您对系统表执行直接更新时，SQL Server 会报告以下消息。

### <a name="a-system-table-is-manually-updated"></a>手动更新系统表
Msg 17659：警告：系统表<id>ID 已在数据库 ID<id>中直接更新，并且缓存一致性可能未维护。 应重新启动 SQL Server。

### <a name="starting-a-database-with-a-system-table-that-was-manually-updated"></a>使用手动更新的系统表启动数据库
Msg 3859：警告：系统目录直接在数据库 ID 17 中更新，最近更新于 date_time。

### <a name="executing-the-dbcc_checkdb-command-after-a-system-table-is-manually-updated"></a>手动更新系统表后执行DBCC_CHECKDB命令
Msg 3859：警告：系统目录直接在数据库 ID 17 中更新，最近更新于 date_time。

如果对系统表执行手动更新并遇到问题，系统可能会要求您从备份还原数据或将数据从受影响的数据库复制到新数据库。 了解有关[用户操作错误消息的详细信息](https://docs.microsoft.com/sql/relational-databases/errors-events/mssqlserver-8992-database-engine-error?view=sql-server-ver15#user-action)。
