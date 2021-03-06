---
title: 스크립트 구성 요소 개체 모델 이해 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], object model
ms.assetid: 2a0aae82-39cc-4423-b09a-72d2f61033bd
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 855278c35de37f2b02e1bb7b194e174c66c643d2
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49460668"
---
# <a name="understanding-the-script-component-object-model"></a>스크립트 구성 요소 개체 모델 이해
  [코딩 and Debugging the Script Component]에 설명 된 대로 (... / extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md, 스크립트 구성 요소 프로젝트에 세 개의 프로젝트 항목이 있습니다.  
  
1.  `ScriptMain` 항목: 코드를 작성할 `ScriptMain` 클래스가 들어 있습니다. `ScriptMain` 클래스는 `UserComponent` 클래스에서 상속됩니다.  
  
2.  `ComponentWrapper` 항목: 데이터를 처리하고 패키지와 상호 작용하는 데 사용할 메서드 및 속성이 포함된 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>의 인스턴스인 `UserComponent` 클래스가 들어 있습니다. `ComponentWrapper` 항목에는 `Connections` 및 `Variables` 컬렉션 클래스도 들어 있습니다.  
  
3.  `BufferWrapper` 항목: 각 입력 및 출력에 대해 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>에서 상속되는 클래스와 각 열에 대한 형식화된 속성이 들어 있습니다.  
  
 `ScriptMain` 항목에서 코드를 작성할 때는 이 항목에 설명된 개체, 메서드 및 속성을 사용합니다. 각 구성 요소에서 여기에 나열된 메서드를 모두 사용하는 것은 아니지만 사용될 경우에는 여기에 표시된 순서대로 사용됩니다.  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 기본 클래스에는 이 항목에 설명된 메서드의 구현 코드가 들어 있지 않습니다. 따라서 메서드 구현에 기본 클래스 구현에 대한 호출을 추가하는 것은 불필요하지만 해가 되지는 않습니다.  
  
 특정 유형의 스크립트 구성 요소에서 이러한 클래스의 메서드와 속성을 사용하는 방법에 대한 자세한 내용은 [추가 스크립트 구성 요소 예제](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md) 섹션을 참조하세요. 예 항목에는 전체 코드 예제도 들어 있습니다.  
  
## <a name="acquireconnections-method"></a>AcquireConnections 메서드  
 원본 및 대상은 일반적으로 외부 데이터 원본에 연결해야 합니다. <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> 기본 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 메서드를 재정의하여 적절한 연결 관리자에서 연결 또는 연결 정보를 검색합니다.  
  
 다음 예에서는 ADO.NET 연결 관리자에서 `System.Data.SqlClient.SqlConnection`을 반환합니다.  
  
```vb  
Dim connMgr As IDTSConnectionManager100  
Dim sqlConn As SqlConnection  
  
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
    connMgr = Me.Connections.MyADONETConnection  
    sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)  
  
End Sub  
```  
  
 다음 예에서는 플랫 파일 연결 관리자에서 전체 경로 및 파일 이름을 반환한 다음 `System.IO.StreamReader`를 사용하여 파일을 엽니다.  
  
```vb  
Private textReader As StreamReader  
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
    Dim connMgr As IDTSConnectionManager100 = _  
        Me.Connections.MyFlatFileSrcConnectionManager  
    Dim exportedAddressFile As String = _  
        CType(connMgr.AcquireConnection(Nothing), String)  
    textReader = New StreamReader(exportedAddressFile)  
  
End Sub  
```  
  
## <a name="preexecute-method"></a>PreExecute 메서드  
 데이터 행의 처리를 시작하기 전에만 한 번 수행해야 하는 처리가 있을 때마다 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A> 기본 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 메서드를 재정의합니다. 예를 들어 대상에서 데이터 원본에 각 데이터 행을 삽입하는 데 사용할 매개 변수가 있는 명령을 구성할 수 있습니다.  
  
```vb  
    Dim sqlConn As SqlConnection  
    Dim sqlCmd As SqlCommand  
    Dim sqlParam As SqlParameter  
...  
    Public Overrides Sub PreExecute()  
  
        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
            "VALUES(@addressid, @city)", sqlConn)  
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)  
        sqlCmd.Parameters.Add(sqlParam)  
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)  
        sqlCmd.Parameters.Add(sqlParam)  
  
    End Sub  
```  
  
```csharp  
SqlConnection sqlConn;   
SqlCommand sqlCmd;   
SqlParameter sqlParam;   
  
public override void PreExecute()   
{   
  
    sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " + "VALUES(@addressid, @city)", sqlConn);   
    sqlParam = new SqlParameter("@addressid", SqlDbType.Int);   
    sqlCmd.Parameters.Add(sqlParam);   
    sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30);   
    sqlCmd.Parameters.Add(sqlParam);   
  
}  
```  
  
## <a name="processing-inputs-and-outputs"></a>입력 및 출력 처리  
  
### <a name="processing-inputs"></a>입력 처리  
 변환 또는 대상으로 구성된 스크립트 구성 요소에는 하나의 입력이 있습니다.  
  
#### <a name="what-the-bufferwrapper-project-item-provides"></a>BufferWrapper 프로젝트 항목의 제공 내용  
 `BufferWrapper` 프로젝트 항목에는 사용자가 구성한 각 입력에 대해 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>에서 파생되며 입력과 이름이 동일한 클래스가 들어 있습니다. 각 입력 버퍼 클래스에는 다음과 같은 속성, 함수 및 메서드가 들어 있습니다.  
  
-   선택한 각 입력 열에 대한 명명되고 형식화된 접근자 속성. 이러한 속성은 **스크립트 변환 편집기**의 **입력 열** 페이지에서 열에 대해 지정된 **사용 유형**에 따라 읽기 전용 또는 읽기/쓰기입니다.  
  
-   선택한 각 입력 열에 대한 **\<column>_IsNull** 속성 - 이 속성도 열에 대해 지정된 **사용 유형**에 따라 읽기 전용 또는 읽기/쓰기입니다.  
  
-   구성된 각 출력에 대한 **DirectRowTo\<outputbuffer>** 메서드 - 이러한 메서드는 행을 동일한 `ExclusionGroup`의 여러 출력 중 하나로 필터링할 때 사용합니다.  
  
-   다음 입력 행을 가져오기 위한 `NextRow` 함수와 데이터의 마지막 버퍼가 처리되었는지 여부를 확인하기 위한 `EndOfRowset` 함수. 일반적으로 `UserComponent` 기본 클래스에 구현된 입력 처리 메서드를 사용할 때는 이러한 함수가 필요하지 않습니다. 다음 섹션에서는 `UserComponent` 기본 클래스에 대한 더 많은 정보를 제공합니다.  
  
#### <a name="what-the-componentwrapper-project-item-provides"></a>ComponentWrapper 프로젝트 항목의 제공 내용  
 ComponentWrapper 프로젝트 항목에는 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>에서 파생된 `UserComponent`라는 클래스가 들어 있습니다. 사용자 지정 코드를 작성하는 위치인 `ScriptMain` 클래스는 `UserComponent`에서 파생됩니다. `UserComponent` 클래스에는 다음과 같은 메서드가 들어 있습니다.  
  
-   `ProcessInput` 메서드의 재정의된 구현. 이 메서드는 데이터 흐름 엔진에서 런타임에 `PreExecute` 메서드 다음으로 호출하는 메서드이며 여러 번 호출될 수 있습니다. `ProcessInput` 처리를 넘깁니다 합니다  **\<inputbuffer > _ProcessInput** 메서드. 그런 다음 `ProcessInput` 메서드는 입력 버퍼의 끝을 확인하고 버퍼의 끝에 도달한 경우 재정의 가능한 `FinishOutputs` 메서드와 전용 `MarkOutputsAsFinished` 메서드를 호출합니다. 그런 다음 `MarkOutputsAsFinished` 메서드가 마지막 출력 버퍼에서 `SetEndOfRowset`을 호출합니다.  
  
-   **\<inputbuffer>_ProcessInput** 메서드의 재정의 가능한 구현 - 이 기본 구현은 단순히 각 입력 행을 반복하며 **\<inputbuffer>_ProcessInputRow**를 호출합니다.  
  
-   **\<inputbuffer>_ProcessInputRow** 메서드의 재정의 가능한 구현 - 기본 구현은 비어 있습니다. 이 메서드는 일반적으로 사용자 지정 데이터 처리 코드를 작성하기 위해 재정의하는 메서드입니다.  
  
#### <a name="what-your-custom-code-should-do"></a>사용자 지정 코드로 수행하는 작업  
 `ScriptMain` 클래스에서 다음 메서드를 사용하여 입력을 처리할 수 있습니다.  
  
-   **\<inputbuffer>_ProcessInputRow**를 재정의하여 각 입력 행의 데이터를 전달할 때 처리합니다.  
  
-   입력 행을 반복하면서 추가 작업을 수행해야 하는 경우에만 **\<inputbuffer>_ProcessInput**을 재정의합니다. 예를 들어 모든 행이 처리된 후 다른 동작을 수행하려면 `EndOfRowset`을 테스트해야 합니다. 행 처리를 수행하려면 **\<inputbuffer>_ProcessInputRow**를 호출합니다.  
  
-   출력을 닫기 전에 출력에 대한 작업을 수행해야 하는 경우 `FinishOutputs`를 재정의합니다.  
  
 `ProcessInput` 메서드를 사용하면 이러한 메서드가 적절한 시기에 호출됩니다.  
  
### <a name="processing-outputs"></a>출력 처리  
 원본 또는 변환으로 구성된 스크립트 구성 요소에는 하나 이상의 출력이 있습니다.  
  
#### <a name="what-the-bufferwrapper-project-item-provides"></a>BufferWrapper 프로젝트 항목의 제공 내용  
 BufferWrapper 프로젝트 항목에는 사용자가 구성한 각 출력에 대해 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>에서 파생되며 출력과 이름이 동일한 클래스가 들어 있습니다. 각 입력 버퍼 클래스에는 다음과 같은 속성 및 메서드가 들어 있습니다.  
  
-   각 출력 열에 대한 명명되고 형식화된 쓰기 전용 접근자 속성  
  
-   쓰기 전용  **\<열 > _IsNull** 선택한 각 출력 열으로 열 값을 설정 하는 데 사용할 수 있는 속성 `null`합니다.  
  
-   비어 있는 새 행을 출력 버퍼에 추가하는 데 사용하는 `AddRow` 메서드  
  
-   데이터 흐름 엔진에 데이터 버퍼가 더 이상 없음을 알려 주는 `SetEndOfRowset` 메서드. 현재 버퍼가 마지막 데이터 버퍼인지를 확인하기 위한 `EndOfRowset` 함수도 있습니다. 일반적으로 `UserComponent` 기본 클래스에 구현된 입력 처리 메서드를 사용할 때는 이러한 함수가 필요하지 않습니다.  
  
#### <a name="what-the-componentwrapper-project-item-provides"></a>ComponentWrapper 프로젝트 항목의 제공 내용  
 ComponentWrapper 프로젝트 항목에는 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>에서 파생된 `UserComponent`라는 클래스가 들어 있습니다. 사용자 지정 코드를 작성하는 위치인 `ScriptMain` 클래스는 `UserComponent`에서 파생됩니다. `UserComponent` 클래스에는 다음과 같은 메서드가 들어 있습니다.  
  
-   `PrimeOutput` 메서드의 재정의된 구현. 데이터 흐름 엔진에서는 런타임에 이 메서드를 `ProcessInput`보다 먼저 호출하며 이 메서드는 한 번만 호출됩니다. `PrimeOutput`은 `CreateNewOutputRows` 메서드로 처리를 넘깁니다. 그런 다음 구성 요소가 원본인 경우, 즉 구성 요소에 입력이 없는 경우 `PrimeOutput`은 재정의 가능한 `FinishOutputs` 메서드와 전용 `MarkOutputsAsFinished` 메서드를 호출합니다. `MarkOutputsAsFinished` 메서드는 마지막 출력 버퍼에서 `SetEndOfRowset`을 호출합니다.  
  
-   `CreateNewOutputRows` 메서드의 재정의 가능한 구현. 기본 구현은 비어 있습니다. 이 메서드는 일반적으로 사용자 지정 데이터 처리 코드를 작성하기 위해 재정의하는 메서드입니다.  
  
#### <a name="what-your-custom-code-should-do"></a>사용자 지정 코드로 수행하는 작업  
 `ScriptMain` 클래스에서 다음 메서드를 사용하여 출력을 처리할 수 있습니다.  
  
-   입력 행을 처리하기 전에 출력 행을 추가하고 채울 수 있는 경우에 한해 `CreateNewOutputRows`를 재정의합니다. 예를 들어 원본에서는 `CreateNewOutputRows`를 사용할 수 있지만 비동기 출력을 사용하는 변환에서는 입력 데이터를 처리하는 동안이나 그 이후에 `AddRow`를 호출해야 합니다.  
  
-   출력을 닫기 전에 출력에 대한 작업을 수행해야 하는 경우 `FinishOutputs`를 재정의합니다.  
  
 `PrimeOutput` 메서드를 사용하면 이러한 메서드가 적절한 시기에 호출됩니다.  
  
## <a name="postexecute-method"></a>PostExecute 메서드  
 데이터 행의 처리를 시작한 후에만 한 번 수행해야 하는 처리가 있을 때마다 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> 기본 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 메서드를 재정의합니다. 예를 들어 원본에서는 데이터 흐름으로 데이터를 로드하는 데 사용한 `System.Data.SqlClient.SqlDataReader`를 닫을 수 있습니다.  
  
> [!IMPORTANT]  
>  `ReadWriteVariables`의 컬렉션은 `PostExecute` 메서드에서만 사용할 수 있습니다. 따라서 각 데이터 행을 처리할 때 패키지 변수의 값을 직접 증분시킬 수 없습니다. 대신 지역 변수의 값을 증분시키고 모든 데이터가 처리된 후에 `PostExecute` 메서드에서 패키지 변수의 값을 지역 변수 값으로 설정합니다.  
  
## <a name="releaseconnections-method"></a>ReleaseConnections 메서드  
 원본과 대상은 일반적으로 외부 데이터 원본에 연결해야 합니다. <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> 기본 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 메서드를 재정의하여 이전에 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> 메서드에서 연 연결을 닫고 해제합니다.  
  
```vb  
    Dim connMgr As IDTSConnectionManager100  
...  
    Public Overrides Sub ReleaseConnections()  
  
        connMgr.ReleaseConnection(sqlConn)  
  
    End Sub  
```  
  
```csharp  
IDTSConnectionManager100 connMgr;  
  
public override void ReleaseConnections()  
{  
  
    connMgr.ReleaseConnection(sqlConn);  
  
}  
```  
  
![Integration Services 아이콘 (작은)](../../media/dts-16.gif "Integration Services 아이콘 (작은)")**Integration Services를 사용 하 여 날짜를 알림 설정**<br /> Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.<br /><br /> [MSDN의 Integration Services 페이지 방문](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> 이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.  
  
## <a name="see-also"></a>관련 항목  
 [스크립트 구성 요소 편집기에서 스크립트 구성 요소 구성](configuring-the-script-component-in-the-script-component-editor.md)   
 [코딩 and Debugging the Script Component] (.. /extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md  
  
  
