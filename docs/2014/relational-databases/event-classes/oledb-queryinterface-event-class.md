---
title: OLEDB QueryInterface 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- OLEDB QueryInterface event class
ms.assetid: f54c9ef9-3add-497c-a09b-42c4ce3c623d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b420e0b4b9c9531209f3d3227f534116e26dd206
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "63032428"
---
# <a name="oledb-queryinterface-event-class"></a>OLEDB QueryInterface 事件类
  **发出 OLE DB** QueryInterface [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 来调用分布式查询和远程存储过程时，会发生 **OLEDB QueryInterface** 事件类。 包括跟踪（这些跟踪监视与分布式查询和远程存储过程相关的问题）中的事件类。  
  
 如果包括 **OLEDB QueryInterface** 事件类，开销量将变高。 如果此类事件频繁发生，则跟踪可能会显著地降低性能。 若要最大限度地降低引起的开销，请仅将此事件类用于在短时间段内监视特定问题的跟踪操作。  
  
## <a name="oledb-queryinterface-event-class-data-columns"></a>OLEDB QueryInterface 事件类的数据列  
  
|数据列名称|数据类型|说明|列 ID|可筛选|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|客户端应用程序的名称，该客户端应用程序创建了指向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的连接。 此列由应用程序传递的值填充，而不是由所显示的程序名填充。|10|是|  
|ClientProcessID|`int`|主机为运行该客户端应用程序的进程分配的 ID。 如果客户端提供了客户端进程 ID，则填充此数据列。|9|是|  
|DatabaseID|`int`|由 USE *database* 语句指定的数据库的 ID；如果未对给定实例发出 USE *database* 语句，则为默认数据库的 ID。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]如果在跟踪中捕获到**ServerName**数据列并且服务器可用，则将显示数据库的名称。 可使用 DB_ID 函数来确定数据库的值。|3|是|  
|DatabaseName|`nvarchar`|正在其中运行用户语句的数据库的名称。|35|是|  
|Duration|`bigint`|完成 OLE DB QueryInterface 事件所需的时间。|13|否|  
|EndTime|`datetime`|事件结束的时间。|15|是|  
|错误|`int`|给定事件的错误号。 通常，这是存储在**sys.databases**目录视图中的错误号。|31|是|  
|EventClass|`int`|事件类型 = 120。|27|否|  
|EventSequence|`int`|OLE DB 事件类在批处理中的顺序。|51|否|  
|EventSubClass|`int`|0 = 正在启动<br /><br /> 1 = 已完成|21|否|  
|GroupID|`int`|在其中激发 SQL 跟踪事件的工作负荷组的 ID。|66|是|  
|HostName|`nvarchar`|正在运行客户端的计算机的名称。 如果客户端提供了主机名，则填充此数据列。 若要确定主机名，请使用 HOST_NAME 函数。|8|是|  
|IsSystem|`int`|指示事件是发生在系统进程中还是发生在用户进程中。 1 = 系统，0 = 用户。|60|是|  
|LinkedServerName|`nvarchar`|链接服务器的名称。|45|是|  
|LoginName|`nvarchar`|用户的登录名（ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全登录名或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 登录凭据，格式为“DOMAIN\username”）。|11|是|  
|LoginSid|`image`|已登录的用户的安全标识符 (SID)。 您可以在 sys.server_principals 目录视图中找到此信息。 服务器中的每个登录名都具有唯一的 SID。|41|是|  
|MethodName|`nvarchar`|调用方法的名称。|47|否|  
|NTDomainName|`nvarchar`|用户所属的 Windows 域。|7|是|  
|NTUserName|`nvarchar`|Windows 用户名。|6|是|  
|ProviderName|`nvarchar`|OLE DB 访问接口的名称。|46|是|  
|RequestID|`int`|包含该语句的请求的 ID。|49|是|  
|SessionLoginName|`nvarchar`|发起会话的用户的登录名。 例如，如果您使用 Login1 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 并以 Login2 身份执行语句，则 `SessionLoginName` 将显示 Login1，而 `LoginName` 则显示 Login2。 此列将同时显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和 Windows 登录名。|64|是|  
|SPID|`int`|发生该事件的会话的 ID。|12|是|  
|StartTime|`datetime`|该事件（如果存在）的启动时间。|14|是|  
|TextData|`nvarchar`|在 OLE DB 调用中发送和接收的参数。|1|否|  
|TransactionID|`bigint`|系统分配的事务 ID。|4|是|  
  
## <a name="see-also"></a>另请参阅  
 [扩展事件](../extended-events/extended-events.md)   
 [sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Transact-SQL 中的 OLE 自动化对象](../stored-procedures/ole-automation-objects-in-transact-sql.md)  
  
  
