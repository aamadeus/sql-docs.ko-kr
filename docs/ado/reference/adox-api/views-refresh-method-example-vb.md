---
title: "뷰 새로 메서드 예제 (VB) | Microsoft Docs"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Refresh method [ADOX]
ms.assetid: cdad2d66-6ade-40dc-9e74-e40cfa9bc127
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b6e526091804e36790f79a051399ff69e479df4a
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="views-refresh-method-example-vb"></a>뷰는 메서드 예제를 (VB)를 새로 고칩니다.
다음 코드에서는 새로 고치는 방법을 보여 줍니다.는 [뷰](../../../ado/reference/adox-api/views-collection-adox.md) 의 컬렉션을 [카탈로그](../../../ado/reference/adox-api/catalog-object-adox.md)합니다. 하기 전에 반드시 지정 해야 [보기](../../../ado/reference/adox-api/view-object-adox.md) 에서 개체는 **카탈로그** 액세스할 수 있습니다.  
  
```  
' BeginViewsRefreshVB  
Sub Main()  
    On Error GoTo ProcedureViewsRefreshError  
  
    Dim cat As New ADOX.Catalog  
  
    ' Open the catalog.  
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Refresh the Procedures collection.  
    cat.Views.Refresh  
  
    'Clean up  
    Set cat = Nothing  
    Exit Sub  
  
ProcedureViewsRefreshError:  
  
    If Not cat Is Nothing Then  
        Set cat = Nothing  
    End If  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndViewsRefreshVB  
```  
  
## <a name="see-also"></a>관련 항목:  
 [Refresh 메서드 (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)   
 [Views 컬렉션(ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)