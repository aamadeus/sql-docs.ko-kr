---
title: 사용자 지정 태스크에서 데이터 원본에 연결 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ConnectionManager objects
- connection managers [Integration Services], external data sources
- data sources [Integration Services], external
- custom tasks [Integration Services], external data sources
- external data sources [Integration Services]
- connections [Integration Services], external data sources
- SSIS custom tasks, external data sources
ms.assetid: 9f0b3a43-3eaa-4b3c-bb08-29b630c11306
caps.latest.revision: 49
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: d4a63ff7db9cc4a4a36b9d6ef7739f627ef9fe6a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36080890"
---
# <a name="connecting-to-data-sources-in-a-custom-task"></a>사용자 지정 태스크에서 데이터 원본에 연결
  태스크는 연결 관리자를 통해 외부 데이터 원본에 연결하여 데이터를 검색하거나 저장합니다. 디자인 타임에 연결 관리자는 논리적 연결을 나타내며 서버 이름 및 인증 속성과 같은 주요 정보를 설명합니다. 런타임에 태스크에서는 연결 관리자의 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 메서드를 호출하여 데이터 원본에 대한 실제 연결을 설정합니다.  
  
 패키지에는 각기 다른 데이터 원본에 연결하는 여러 태스크가 있을 수 있으므로 패키지에서는 모든 연결 관리자를 <xref:Microsoft.SqlServer.Dts.Runtime.Connections>라는 컬렉션에서 추적합니다. 태스크에서는 해당 패키지의 컬렉션을 사용하여 유효성 검사 및 실행 중 사용할 연결 관리자를 찾습니다. <xref:Microsoft.SqlServer.Dts.Runtime.Connections> 컬렉션은 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 메서드에 대한 첫 번째 매개 변수입니다.  
  
 컬렉션의 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 개체를 사용자에게 표시하거나 그래픽 사용자 인터페이스의 대화 상자 또는 드롭다운 목록을 사용하여 태스크에서 잘못된 연결 관리자를 사용하지 못하도록 할 수 있습니다. 이렇게 하면 사용자는 패키지에 포함된 적절한 유형의 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 개체 중에서만 선택할 수 있습니다.  
  
 태스크에서는 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 메서드를 호출하여 데이터 원본에 대한 실제 연결을 설정합니다. 이 메서드는 태스크에서 사용될 수 있는 기본 연결 개체를 반환합니다. 연결 관리자는 기본 연결 개체의 구현 세부 사항을 태스크에서 격리하므로 태스크에서는 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 메서드를 호출하여 연결을 설정하기만 하면 되고 연결의 다른 측면은 고려할 필요가 없습니다.  
  
## <a name="example"></a>예제  
 다음 예제 코드에서는 Validate 및 Execute 메서드에서 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 이름의 유효성을 검사하는 방법과 Execute 메서드에서 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 메서드를 사용하여 실제 연결을 설정하는 방법을 보여 줍니다.  
  
```csharp  
private string connectionManagerName = "";  
  
public string ConnectionManagerName  
{  
  get { return this.connectionManagerName; }  
  set { this.connectionManagerName = value; }  
}  
  
public override DTSExecResult Validate(  
  Connections connections, VariableDispenser variableDispenser,  
  IDTSComponentEvents componentEvents, IDTSLogging log)  
{  
  // If the connection manager exists, validation is successful;  
  // otherwise, fail validation.  
  try  
  {  
    ConnectionManager cm = connections[this.connectionManagerName];  
    return DTSExecResult.Success;  
  }  
  catch (System.Exception e)  
  {  
    componentEvents.FireError(0, "SampleTask", "Invalid connection manager.", "", 0);  
    return DTSExecResult.Failure;  
  }  
}  
  
public override DTSExecResult Execute(Connections connections,   
  VariableDispenser variableDispenser, IDTSComponentEvents componentEvents,   
  IDTSLogging log, object transaction)  
{  
  try  
  {  
    ConnectionManager cm = connections[this.connectionManagerName];  
    object connection = cm.AcquireConnection(transaction);  
    return DTSExecResult.Success;  
  }  
  catch (System.Exception exception)  
  {  
    componentEvents.FireError(0, "SampleTask", exception.Message, "", 0);  
    return DTSExecResult.Failure;  
  }  
}  
```  
  
```vb  
Private _connectionManagerName As String = ""  
  
Public Property ConnectionManagerName() As String  
  Get  
    Return Me._connectionManagerName  
  End Get  
  Set(ByVal Value As String)  
    Me._connectionManagerName = value  
  End Set  
End Property  
  
Public Overrides Function Validate( _  
  ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, _  
  ByVal variableDispenser As Microsoft.SqlServer.Dts.Runtime.VariableDispenser, _  
  ByVal componentEvents As Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents, _  
  ByVal log As Microsoft.SqlServer.Dts.Runtime.IDTSLogging) _  
  As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  ' If the connection manager exists, validation is successful;  
  ' otherwise fail validation.  
  Try  
    Dim cm As ConnectionManager = connections(Me._connectionManagerName)  
    Return DTSExecResult.Success  
  Catch e As System.Exception  
    componentEvents.FireError(0, "SampleTask", "Invalid connection manager.", "", 0)  
    Return DTSExecResult.Failure  
  End Try  
  
End Function  
  
Public Overrides Function Execute( _  
  ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, _  
  ByVal variableDispenser As Microsoft.SqlServer.Dts.Runtime.VariableDispenser, _  
  ByVal componentEvents As Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents, _  
  ByVal log As Microsoft.SqlServer.Dts.Runtime.IDTSLogging, ByVal transaction As Object) _  
  As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  Try  
    Dim cm As ConnectionManager = connections(Me._connectionManagerName)  
    Dim connection As Object = cm.AcquireConnection(transaction)  
    Return DTSExecResult.Success  
  Catch exception As System.Exception  
    componentEvents.FireError(0, "SampleTask", exception.Message, "", 0)  
    Return DTSExecResult.Failure  
  End Try  
  
End Function  
```  
  
![Integration Services 아이콘 (작은)](../../media/dts-16.gif "Integration Services 아이콘 (작은)")**Integration Services를 사용 하 여 날짜를 알림 설정** <br /> Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.<br /><br /> [MSDN의 Integration Services 페이지를 방문 하십시오.](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> 이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.  
  
## <a name="see-also"></a>관련 항목  
 [Integration Services&#40;SSIS&#41; 연결](../../connection-manager/integration-services-ssis-connections.md)   
 [연결 관리자 만들기](../../create-connection-managers.md)  
  
  