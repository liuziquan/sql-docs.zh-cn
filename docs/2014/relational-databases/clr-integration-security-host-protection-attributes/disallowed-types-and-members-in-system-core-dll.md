---
title: 不允许的类型和成员Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
ms.assetid: dcd24cd6-f4ab-42cc-9786-a1604e8a4b4e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f078caae791e4009a309e7cc70d7af333ca4c90f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "62919563"
---
# <a name="disallowed-types-and-members-in-systemcoredll"></a>System.Core.dll 中禁用的类型和成员
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]公共`HostProtectionAttribute`语言集成（CLR）编程不允许使用具有`System.Security.Permissions.HostProtectionResource` `ExternalProcessMgmt`、 `ExternalThreading` `MayLeakOnAbort` `SecurityInfrastructure` `SelfAffectingProcessMgmnt` `SelfAffectingThreading`、、、、、、 **SharedState**、 `Synchronization`或`UI`的值的类型或成员。 下表列出了宿主保护属性 (HPA) 值被禁用的 System.Core.dll 程序集的成员和类型。  
  
> [!NOTE]  
>  此列表是通过支持的程序集生成的。 有关详细信息，请参阅[支持的 .NET Framework 库](../clr-integration/database-objects/supported-net-framework-libraries.md)。  
  
|类型或成员|HPA 值|  
|--------------------|--------------------|  
|System.Diagnostics.Eventing.EventDescriptor|MayLeakOnAbort|  
|System.Diagnostics.Eventing.EventProvider|MayLeakOnAbort|  
|System.Diagnostics.Eventing.EventProviderTraceListener|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementEntityAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.WmiConfigurationAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementMemberAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementNewInstanceAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementBindAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementCreateAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementRemoveAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementEnumeratorAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementProbeAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementTaskAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementKeyAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementReferenceAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementConfigurationAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementCommitAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementNameAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.InstrumentationBaseException|MayLeakOnAbort|  
|System.Management.Instrumentation.InstrumentationException|MayLeakOnAbort|  
|System.Management.Instrumentation.InstanceNotFoundException|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventBookmark|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogConfiguration|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogLink|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogStatus|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventProperty|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogPropertySelector|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventRecord|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventKeyword|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLevel|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogRecord|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogReader|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogWatcher|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventRecordWrittenEventArgs|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogSession|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventMetadata|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventOpcode|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventTask|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogException|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogNotFoundException|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogReadingException|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogProviderDisabledException|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogInvalidDataException|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogInformation|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.ProviderMetadata|MayLeakOnAbort|  
|Microsoft.Win32.SafeHandles.SafeNCryptHandle|MayLeakOnAbort|  
|Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle|MayLeakOnAbort|  
|Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle|MayLeakOnAbort|  
|Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle|MayLeakOnAbort|  
|System.Security.Cryptography.Aes|MayLeakOnAbort|  
|System.Security.Cryptography.AesCryptoServiceProvider|MayLeakOnAbort|  
|System.Security.Cryptography.AesManaged|MayLeakOnAbort|  
|System.Security.Cryptography.CngAlgorithm|MayLeakOnAbort|  
|System.Security.Cryptography.CngAlgorithmGroup|MayLeakOnAbort|  
|System.Security.Cryptography.CngKey|MayLeakOnAbort|  
|System.Security.Cryptography.CngKeyBlobFormat|MayLeakOnAbort|  
|System.Security.Cryptography.CngKeyCreationParameters|MayLeakOnAbort|  
|System.Security.Cryptography.CngProperty|MayLeakOnAbort|  
|System.Security.Cryptography.CngPropertyCollection|MayLeakOnAbort|  
|System.Security.Cryptography.CngProvider|MayLeakOnAbort|  
|System.Security.Cryptography.CngUIPolicy|MayLeakOnAbort|  
|System.Security.Cryptography.ECDiffieHellman|MayLeakOnAbort|  
|System.Security.Cryptography.ECDiffieHellmanPublicKey|MayLeakOnAbort|  
|System.Security.Cryptography.ECDiffieHellmanCng|MayLeakOnAbort|  
|System.Security.Cryptography.ECDiffieHellmanCngPublicKey|MayLeakOnAbort|  
|System.Security.Cryptography.ECDsa|MayLeakOnAbort|  
|System.Security.Cryptography.ECDsaCng|MayLeakOnAbort|  
|System.Security.Cryptography.ManifestSignatureInformation|MayLeakOnAbort|  
|System.Security.Cryptography.ManifestSignatureInformationCollection|MayLeakOnAbort|  
|System.Security.Cryptography.MD5Cng|MayLeakOnAbort|  
|System.Security.Cryptography.SHA1Cng|MayLeakOnAbort|  
|System.Security.Cryptography.SHA256Cng|MayLeakOnAbort|  
|System.Security.Cryptography.SHA256CryptoServiceProvider|MayLeakOnAbort|  
|System.Security.Cryptography.SHA384Cng|MayLeakOnAbort|  
|System.Security.Cryptography.SHA384CryptoServiceProvider|MayLeakOnAbort|  
|System.Security.Cryptography.SHA512Cng|MayLeakOnAbort|  
|System.Security.Cryptography.SHA512CryptoServiceProvider|MayLeakOnAbort|  
|System.Security.Cryptography.StrongNameSignatureInformation|MayLeakOnAbort|  
|System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation|MayLeakOnAbort|  
|System.Security.Cryptography.X509Certificates.TimestampInformation|MayLeakOnAbort|  
|Microsoft.Win32.SafeHandles.SafePipeHandle|MayLeakOnAbort|  
|System.TimeZoneInfo|MayLeakOnAbort|  
|System.TimeZoneNotFoundException|MayLeakOnAbort|  
|System.InvalidTimeZoneException|MayLeakOnAbort|  
|System.Diagnostics.EventSchemaTraceListener|MayLeakOnAbort|  
|System.Diagnostics.UnescapedXmlDiagnosticData|MayLeakOnAbort|  
|System.Diagnostics.PerformanceData.CounterData|MayLeakOnAbort|  
|System.Diagnostics.PerformanceData.CounterSetInstanceCounterDataSet|MayLeakOnAbort|  
|System.Diagnostics.PerformanceData.CounterSet|MayLeakOnAbort|  
|System.Diagnostics.PerformanceData.CounterSetInstance|MayLeakOnAbort|  
|System.Collections.Generic.HashSet`1|MayLeakOnAbort|  
|System.IO.Pipes.PipeStream|MayLeakOnAbort|  
|System.IO.Pipes.AnonymousPipeServerStream|MayLeakOnAbort|  
|System.IO.Pipes.AnonymousPipeClientStream|MayLeakOnAbort|  
|System.IO.Pipes.NamedPipeServerStream|MayLeakOnAbort|  
|System.IO.Pipes.NamedPipeClientStream|MayLeakOnAbort|  
|System.IO.Pipes.PipeAccessRule|MayLeakOnAbort|  
|System.IO.Pipes.PipeAuditRule|MayLeakOnAbort|  
|System.IO.Pipes.PipeSecurity|MayLeakOnAbort|  
|System.Threading.LockRecursionException|MayLeakOnAbort|  
|System.Threading.ReaderWriterLockSlim|MayLeakOnAbort|  
  
## <a name="see-also"></a>另请参阅  
 [宿主保护属性和 CLR 集成编程](host-protection-attributes-and-clr-integration-programming.md)   
 [不允许的类型和成员在](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Mscorlib.dll 中禁用的类型和成员](disallowed-types-and-members-in-mscorlib-dll.md)   
 [系统中不允许的类型和成员](disallowed-types-and-members-in-system-dll.md)   
 [System.Data.dll 中禁用的类型和成员](disallowed-types-and-members-in-system-data-dll.md)  
  
  
