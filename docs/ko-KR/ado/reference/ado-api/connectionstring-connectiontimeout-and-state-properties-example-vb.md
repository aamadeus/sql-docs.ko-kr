---
title: 연결 속성 예 (VB) | Microsoft Docs
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
- ConnectionString property [ADO], Visual Basic example
- ConnectionTimeout property [ADO], Visual Basic example
- State property [ADO], Visual Basic example
ms.assetid: 4de7336a-b5ea-43f1-b750-5fa302b5b756
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 427c59b41d79a33da9bc3cc9354072542e95795c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="connectionstring-connectiontimeout-and-state-properties-example-vb"></a>ConnectionString, ConnectionTimeout, 및 상태 속성 예제 (VB)
이 예제에서는 여러 가지를 사용 하 여는 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) 속성을 열고는 [연결](../../../ado/reference/ado-api/connection-object-ado.md) 개체입니다. 또한 사용 하 여는 [ConnectionTimeout](../../../ado/reference/ado-api/connectiontimeout-property-ado.md) 연결 제한 시간을 설정 하는 속성 및 [상태](../../../ado/reference/ado-api/state-property-ado.md) 연결의 상태를 확인할 속성입니다. 우편 번호 함수는이 절차를 실행 하려면 필요 합니다.  
  
> [!NOTE]
>  지정 해야 하는 경우 Windows 인증을 지 원하는 데이터 원본 공급자에 연결 하는, **Trusted_Connection = yes** 또는 **통합 보안 = SSPI** 사용자 ID와 암호 대신 연결 문자열에 대 한 정보입니다.  
  
```  
'BeginConnectionStringVB  
  
    'To integrate this code replace  
    'the database, DSN or Data Source values  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    Dim Cnxn1 As ADODB.Connection  
    Dim Cnxn2 As ADODB.Connection  
    Dim Cnxn3 As ADODB.Connection  
    Dim Cnxn4 As ADODB.Connection  
  
     ' Open a connection without using a Data Source Name (DSN)  
    Set Cnxn1 = New ADODB.Connection  
    Cnxn1.ConnectionString = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn1.Open  
    MsgBox "Cnxn1 state: " & GetState(Cnxn1.State)  
  
     ' Open a connection using a DSN and ODBC tags  
     ' It is assumed that you have created DSN 'Pubs' with a user name as  
     ' 'MyUserId' and password as 'MyPassword'.  
    Set Cnxn2 = New ADODB.Connection  
    Cnxn2.ConnectionString = "Data Source='Pubs';" & _  
        "User ID='MyUserId';Password='MyPassword';"  
    Cnxn2.ConnectionTimeout = 30  
    Cnxn2.Open  
    MsgBox "Cnxn2 state: " & GetState(Cnxn2.State)  
  
     ' Open a connection using a DSN and OLE DB tags  
     ' It is assumed that you have created DSN 'Pubs1' with windows authentication.  
    Set Cnxn3 = New ADODB.Connection  
    Cnxn3.ConnectionString = "Data Source='Pubs1';"  
    Cnxn3.Open  
    MsgBox "Cnxn2 state: " & GetState(Cnxn3.State)  
  
     ' Open a connection using a DSN and individual  
     ' arguments instead of a connection string  
     ' It is assumed that you have created DSN 'Pubs' with a user name as  
     ' 'MyUserId' and password as 'MyPassword'.  
    Set Cnxn4 = New ADODB.Connection  
    Cnxn4.Open "Pubs", "MyUserId", "MyPassword"  
    MsgBox "Cnxn4 state: " & GetState(Cnxn4.State)  
  
    ' clean up  
    Cnxn1.Close  
    Cnxn2.Close  
    Cnxn3.Close  
    Cnxn4.Close  
    Set Cnxn1 = Nothing  
    Set Cnxn2 = Nothing  
    Set Cnxn3 = Nothing  
    Set Cnxn4 = Nothing  
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
  
    If Not Cnxn3 Is Nothing Then  
        If Cnxn3.State = adStateOpen Then Cnxn3.Close  
    End If  
    Set Cnxn3 = Nothing  
  
    If Not Cnxn4 Is Nothing Then  
        If Cnxn4.State = adStateOpen Then Cnxn4.Close  
    End If  
    Set Cnxn4 = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
  
Public Function GetState(intState As Integer) As String  
  
   Select Case intState  
      Case adStateClosed  
         GetState = "adStateClosed"  
      Case adStateOpen  
         GetState = "adStateOpen"  
   End Select  
  
End Function  
'EndConnectionStringVB  
```  
  
## <a name="see-also"></a>관련 항목:  
 [연결 개체 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [ConnectionString 속성 (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)   
 [ConnectionTimeout 속성 (ADO)](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)   
 [State 속성(ADO)](../../../ado/reference/ado-api/state-property-ado.md)