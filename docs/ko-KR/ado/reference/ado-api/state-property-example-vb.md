---
title: 상태 속성 예제 (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- State property [ADO], Visual Basic example
ms.assetid: 9da6db50-d9bb-47e1-ae8b-be3c9b88cf9a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00806576cb0d7bd121505ed74031bf49b42a0776
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="state-property-example-vb"></a>State 속성 예제 (VB)
사용 하 여이 예제는 [상태](../../../ado/reference/ado-api/state-property-ado.md) 비동기 연결을 여는 동안 비동기 명령이 실행 되는 메시지를 표시 하는 속성입니다.  
  
```  
'BeginStateVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    Dim Cnxn1 As ADODB.Connection  
    Dim Cnxn2 As ADODB.Connection  
    Dim cmdChange As ADODB.Command  
    Dim cmdRestore As ADODB.Command  
    Dim strCnxn As String  
    Dim strSQL As String  
  
    ' Open two asynchronous connections, displaying  
    ' a message while connecting  
    Set Cnxn1 = New ADODB.Connection  
    Set Cnxn2 = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
  
    Cnxn1.Open strCnxn, , , adAsyncConnect  
    Do Until Cnxn1.State <> adStateConnecting  
       Debug.Print "Opening first connection...."  
    Loop  
  
    Cnxn2.Open strCnxn, , , adAsyncConnect  
    Do Until Cnxn2.State <> adStateConnecting  
       Debug.Print "Opening second connection...."  
    Loop  
  
    ' Create two command objects  
    Set cmdChange = New ADODB.Command  
    cmdChange.ActiveConnection = Cnxn1  
    strSQL = "UPDATE Titles SET type = 'self_help' WHERE type = 'psychology'"  
    cmdChange.CommandText = strSQL  
  
    Set cmdRestore = New ADODB.Command  
    cmdRestore.ActiveConnection = Cnxn2  
    strSQL = "UPDATE Titles SET type = 'psychology' WHERE type = 'self_help'"  
    cmdRestore.CommandText = strSQL  
  
    ' Executing the commands, displaying a message  
    ' while they are executing  
    cmdChange.Execute , , adAsyncExecute  
    Do Until cmdChange.State <> adStateExecuting  
       Debug.Print "Change command executing...."  
    Loop  
  
    cmdRestore.Execute , , adAsyncExecute  
    Do Until cmdRestore.State <> adStateExecuting  
       Debug.Print "Restore command executing...."  
    Loop  
  
    ' clean up  
    Cnxn1.Close  
    Cnxn2.Close  
    Set Cnxn1 = Nothing  
    Set Cnxn2 = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not Cnxn1 Is Nothing Then  
        If Cnxn1.State = adStateOpen Then Cnxn1.Close  
    End If  
    Set Cnxn1 = Nothing  
  
    If Not Cnxn2 Is Nothing Then  
        If Cnxn2.State = adStateOpen Then Cnxn2.Close  
    End If  
    Set Cnxn2 = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndStateVB  
```  
  
## <a name="see-also"></a>관련 항목:  
 [레코드 집합 개체 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [State 속성(ADO)](../../../ado/reference/ado-api/state-property-ado.md)