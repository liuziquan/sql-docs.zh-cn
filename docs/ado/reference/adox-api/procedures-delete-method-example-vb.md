---
title: 过程 Delete 方法示例（VB） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Delete method [ADOX], Visual Basic example
ms.assetid: 94f1ac93-e778-4a40-a85e-94bce5316ac7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f5c7dfc901434c086b46bfb11c70e1eb2ee3bff7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965363"
---
# <a name="procedures-delete-method-example-vb"></a>过程 Delete 方法示例 (VB)
下面的代码演示如何使用 procedure 集合的[delete](../../../ado/reference/adox-api/delete-method-adox-collections.md)方法[删除过程。](../../../ado/reference/adox-api/procedures-collection-adox.md)  
  
```  
' BeginDeleteProcedureVB  
Sub Main()  
    On Error GoTo DeleteProcedureError  
  
    Dim cat As New ADOX.Catalog  
  
    ' Open the catalog.  
    cat.ActiveConnection = _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Delete the procedure.  
    cat.Procedures.Delete "CustomerById"  
  
    'Clean up.  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Exit Sub  
  
DeleteProcedureError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndDeleteProcedureVB  
```  
  
## <a name="see-also"></a>另请参阅  
 [ActiveConnection 属性（ADOX）](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [目录对象（ADOX）](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Delete 方法（ADOX 集合）](../../../ado/reference/adox-api/delete-method-adox-collections.md)   
 [Procedure 对象（ADOX）](../../../ado/reference/adox-api/procedure-object-adox.md)   
 [过程集合 (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)
