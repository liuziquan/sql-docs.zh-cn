---
title: DataTypeEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataTypeEnum
helpviewer_keywords:
- DataTypeEnum enumeration [ADO]
ms.assetid: 2c57eca6-9336-4b06-ba10-9fef5926b1d0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 27386894ce6d1d393505d49b4863a0ba9bf3320b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933224"
---
# <a name="datatypeenum"></a>DataTypeEnum
指定[字段](../../../ado/reference/ado-api/field-object.md)、[参数](../../../ado/reference/ado-api/parameter-object.md)或[属性](../../../ado/reference/ado-api/property-object-ado.md)的数据类型。 下表的 "说明" 列中的括号内显示了相应的 OLE DB 类型指示器。  
  
|一直|值|说明|  
|--------------|-----------|-----------------|  
|**AdArray**|0x2000|标志值始终与另一个数据类型常量合并，指示另一个数据类型的数组。 不适用于 ADOX。|  
|**adBigInt**|20|指示八字节有符号整数（DBTYPE_I8）。|  
|**adBinary**|128|指示二进制值（DBTYPE_BYTES）。|  
|**adBoolean**|11|指示一个**布尔**值（DBTYPE_BOOL）。|  
|**adBSTR**|8|指示一个以 null 结尾的字符串（Unicode）（DBTYPE_BSTR）。|  
|**adChapter**|136|指示用于标识子行集中的行的四字节章节值（DBTYPE_HCHAPTER）。|  
|**adChar**|129|指示字符串值（DBTYPE_STR）。|  
|**adCurrency**|6|指示货币值（DBTYPE_CY）。 货币是小数点右侧具有四位数的固定点数字。 它存储在10000的8字节有符号整数中。|  
|**adDate**|7|指示日期值（DBTYPE_DATE）。 日期存储为 double，其中是自1899年12月30日以来的天数，而小数部分是一天的小数部分。|  
|**adDBDate**|133|指示日期值（yyyymmdd）（DBTYPE_DBDATE）。|  
|**adDBTime**|134|指示时间值（hhmmss）（DBTYPE_DBTIME）。|  
|**adDBTimeStamp**|135|指示日期/时间戳（十亿分之一中的 yyyymmddhhmmss）（DBTYPE_DBTIMESTAMP）。|  
|**adDecimal**|14|指示具有固定精度和小数位数的精确数值（DBTYPE_DECIMAL）。|  
|**adDouble**|5|指示一个双精度浮点值（DBTYPE_R8）。|  
|**adEmpty**|0|不指定任何值（DBTYPE_EMPTY）。|  
|**adError**|10|指示32位错误代码（DBTYPE_ERROR）。|  
|**adFileTime**|64|表示自64年1月1日起，位值，表示从1601（DBTYPE_FILETIME）开始的100毫微秒间隔数。|  
|**adGUID**|72|指示全局唯一标识符（GUID）（DBTYPE_GUID）。|  
|**adIDispatch**|9|指示指向 COM 对象（DBTYPE_IDISPATCH）上的**IDispatch**接口的指针。<br /><br /> **注意**ADO 目前不支持此数据类型。 使用可能导致不可预知的结果。|  
|**adInteger**|3|指示四字节有符号整数（DBTYPE_I4）。|  
|**adIUnknown**|13|指示指向 COM 对象（DBTYPE_IUNKNOWN）上的**IUnknown**接口的指针。<br /><br /> **注意**ADO 目前不支持此数据类型。 使用可能导致不可预知的结果。|  
|**adLongVarBinary**|205|指示长二进制值。|  
|**adLongVarChar**|201|指示长字符串值。|  
|**adLongVarWChar**|203|指示一个以 null 结尾的长 Unicode 字符串值。|  
|**adNumeric**|131|指示具有固定精度和小数位数的精确数值（DBTYPE_NUMERIC）。|  
|**adPropVariant**|138|指示自动化 PROPVARIANT （DBTYPE_PROP_VARIANT）。|  
|**adSingle**|4|指示单精度浮点值（DBTYPE_R4）。|  
|**adSmallInt**|2|指示2字节有符号整数（DBTYPE_I2）。|  
|**adTinyInt**|16|指示单字节有符号整数（DBTYPE_I1）。|  
|**adUnsignedBigInt**|21|指示八字节无符号整数（DBTYPE_UI8）。|  
|**adUnsignedInt**|19|指示四字节无符号整数（DBTYPE_UI4）。|  
|**adUnsignedSmallInt**|18|指示一个2字节无符号整数（DBTYPE_UI2）。|  
|**adUnsignedTinyInt**|17|指示单字节无符号整数（DBTYPE_UI1）。|  
|**adUserDefined**|132|指示用户定义的变量（DBTYPE_UDT）。|  
|**adVarBinary**|204|指示二进制值。|  
|**adVarChar**|200|指示字符串值。|  
|**adVariant**|12|指示自动化**变体**（DBTYPE_VARIANT）。<br /><br /> **注意**ADO 目前不支持此数据类型。 使用可能导致不可预知的结果。|  
|**adVarNumeric**|139|指示数字值。|  
|**adVarWChar**|202|指示一个以 null 结尾的 Unicode 字符串。|  
|**adWChar**|130|指示一个以 null 结尾的 Unicode 字符串（DBTYPE_WSTR）。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 等效项  
 Package： **.com. 数据**  
  
|一直|  
|--------------|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums. 为 DBDATE|  
|AdoEnums. DBTIME|  
|AdoEnums. DBTIMESTAMP|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums。错误|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums. LONGVARBINARY|  
|AdoEnums. LONGVARCHAR|  
|AdoEnums. LONGVARWCHAR|  
|AdoEnums|  
|AdoEnums. PROPVARIANT|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums. UNSIGNEDBIGINT|  
|AdoEnums. UNSIGNEDINT|  
|AdoEnums. UNSIGNEDSMALLINT|  
|AdoEnums. UNSIGNEDTINYINT|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums. VARNUMERIC|  
|AdoEnums. OLEDBTYPE.VARWCHAR|  
|AdoEnums. WCHAR|  
  
## <a name="applies-to"></a>应用于  
  
|||  
|-|-|  
|[Append 方法 (ADO)](../../../ado/reference/ado-api/append-method-ado.md)|[CreateParameter 方法 (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|  
|[CreateRecordset 方法 (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)|[Type 属性 (ADO)](../../../ado/reference/ado-api/type-property-ado.md)|
