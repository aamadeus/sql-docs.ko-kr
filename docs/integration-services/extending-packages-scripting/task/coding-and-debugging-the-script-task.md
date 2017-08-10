---
title: "코딩 및 스크립트 태스크 디버깅 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], debugging
- SSIS Script task, development environment
- SSIS Script task, debugging
- Script task [Integration Services], development environment
- Script task [Integration Services], coding
- debugging [Integration Services], scripts
- VSTA
- SSIS Script task, coding
ms.assetid: 687c262f-fcab-42e8-92ae-e956f3d92d69
caps.latest.revision: 81
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8c706fc1db3e31130a7754b9e4c3d16f9a13eaf4
ms.contentlocale: ko-kr
ms.lasthandoff: 08/03/2017

---
# <a name="coding-and-debugging-the-script-task"></a>스크립트 태스크 코딩 및 디버깅
  스크립트를 구성한 후에 작업의 **스크립트 태스크 편집기**, 스크립트 태스크 개발 환경에서 사용자 지정 코드를 작성 합니다.  
  
## <a name="script-task-development-environment"></a>스크립트 태스크 개발 환경  
 스크립트 태스크를 사용 하 여 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] VSTA Tools for Applications ()에서 스크립트 자체에 대 한 개발 환경으로 합니다.  
  
 스크립트 코드는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 또는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#으로 작성됩니다. 설정 하 여 스크립트 언어를 지정 된 **u a g e** 속성에는 **스크립트 태스크 편집기**합니다. 다른 프로그래밍 언어를 사용하고 싶으면 원하는 언어로 사용자 지정 어셈블리를 개발하고 스크립트 태스크의 코드에서 해당 기능을 호출할 수 있습니다.  
  
 스크립트 태스크에서 작성하는 스크립트는 패키지 정의에 저장되며 별도의 스크립트 파일은 없습니다. 따라서 스크립트 태스크를 사용해도 패키지 배포에 영향을 주지 않습니다.  
  
> [!NOTE]  
>  패키지를 디자인하고 스크립트를 디버깅할 때 스크립트 코드는 임시로 프로젝트 파일에 기록됩니다. 중요한 정보를 파일에 저장하면 보안상 위험할 수 있으므로 암호와 같은 중요한 정보는 스크립트 코드에 포함하지 않는 것이 좋습니다.  
  
 기본적으로 **Option Strict** IDE에서 사용할 수 없습니다.  
  
## <a name="script-task-project-structure"></a>스크립트 태스크 프로젝트 구조  
 스크립트 태스크에 포함되는 스크립트를 만들거나 수정할 경우 VSTA에서는 빈 새 프로젝트가 열리거나 기존 프로젝트가 다시 열립니다. 이 프로젝트는 패키지 파일 내에 저장되며 스크립트 태스크에서는 추가 파일을 만들지 않으므로 이 VSTA 프로젝트를 만들어도 패키지의 배포에는 영향이 없습니다.  
  
### <a name="project-items-and-classes-in-the-script-task-project"></a>스크립트 태스크 프로젝트의 프로젝트 항목 및 클래스  
 기본적으로 VSTA 프로젝트 탐색기 창에 표시 되는 스크립트 태스크 프로젝트는 단일 항목 포함 **ScriptMain**합니다. **ScriptMain** 라고도 하는 단일 클래스를 차례로 포함 하는 항목을 **ScriptMain**합니다. 클래스의 코드 요소는 스크립트 태스크용으로 선택한 프로그래밍 언어에 따라 다릅니다.  
  
-   스크립트 태스크에 대해 구성 된 경우는 [!INCLUDE[vb_orcas_long](../../../includes/vb-orcas-long-md.md)] 프로그래밍 언어는 **ScriptMain** 클래스에 공용 서브루틴이 **Main**합니다. **ScriptMain.Main** 서브루틴은 개발자가 스크립트 태스크를 실행할 때 런타임에서 호출 하는 메서드.  
  
     유일한 코드가 기본적으로는 **Main** 새 스크립트의 서브루틴은 선 `Dts.TaskResult = ScriptResults.Success`합니다. 이 줄은 태스크가 작업에 성공했음을 런타임에 알립니다. **Dts.TaskResult** 속성에 대해서는 설명 [스크립트 태스크에서 결과 반환](../../../integration-services/extending-packages-scripting/task/returning-results-from-the-script-task.md)합니다.  
  
-   스크립트 태스크에 대 한 Visual C# 프로그래밍 언어에서 구성 하는 경우는 **ScriptMain** 클래스에는 공용 메서드가 **Main**합니다. 이 메서드는 스크립트 태스크가 실행될 때 호출됩니다.  
  
     기본적으로는 **Main** 메서드는 행이 포함 되어 `Dts.TaskResult = (int)ScriptResults.Success`합니다. 이 줄은 태스크가 작업에 성공했음을 런타임에 알립니다.  
  
 **ScriptMain** 항목 이외의 클래스를 포함할 수는 **ScriptMain** 클래스입니다. 클래스는 해당 클래스가 있는 스크립트 태스크에서만 사용할 수 있습니다.  
  
 기본적으로는 **ScriptMain** 프로젝트 항목에는 다음 자동 생성 코드가 포함 되어 있습니다. 코드 템플릿은 또한 스크립트 태스크에 대한 개요와 SSIS 개체(예: 변수, 이벤트 및 연결)를 검색 및 조작하는 방법에 대한 추가 정보를 제공합니다.  
  
```vb  
' Microsoft SQL Server Integration Services Script Task  
' Write scripts using Microsoft Visual Basic 2008.  
' The ScriptMain is the entry point class of the script.  
  
Imports System  
Imports System.Data  
Imports System.Math  
Imports Microsoft.SqlServer.Dts.Runtime.VSTAProxy  
  
<System.AddIn.AddIn("ScriptMain", Version:="1.0", Publisher:="", Description:="")> _  
Partial Class ScriptMain  
  
Private Sub ScriptMain_Startup(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Startup  
  
End Sub  
  
Private Sub ScriptMain_Shutdown(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Shutdown  
Try  
' Unlock variables from the read-only and read-write variable collection properties  
If (Dts.Variables.Count <> 0) Then  
Dts.Variables.Unlock()  
End If  
Catch ex As Exception  
        End Try  
End Sub  
  
Enum ScriptResults  
Success = DTSExecResult.Success  
Failure = DTSExecResult.Failure  
End Enum  
  
' The execution engine calls this method when the task executes.  
' To access the object model, use the Dts property. Connections, variables, events,  
' and logging features are available as members of the Dts property as shown in the following examples.  
'  
' To reference a variable, call Dts.Variables("MyCaseSensitiveVariableName").Value  
' To post a log entry, call Dts.Log("This is my log text", 999, Nothing)  
' To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, True)  
'  
' To use the connections collection use something like the following:  
' ConnectionManager cm = Dts.Connections.Add("OLEDB")  
' cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;"  
'  
' Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.  
'   
' To open Help, press F1.  
  
Public Sub Main()  
'  
' Add your code here  
'  
Dts.TaskResult = ScriptResults.Success  
End Sub  
  
End Class  
```  
  
```csharp  
/*  
   Microsoft SQL Server Integration Services Script Task  
   Write scripts using Microsoft Visual C# 2008.  
   The ScriptMain is the entry point class of the script.  
*/  
  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime.VSTAProxy;  
using System.Windows.Forms;  
  
namespace ST_1bcfdbad36d94f8ba9f23a10375abe53.csproj  
{  
    [System.AddIn.AddIn("ScriptMain", Version = "1.0", Publisher = "", Description = "")]  
    public partial class ScriptMain  
    {  
        private void ScriptMain_Startup(object sender, EventArgs e)  
        {  
  
        }  
  
        private void ScriptMain_Shutdown(object sender, EventArgs e)  
        {  
            try  
            {  
                // Unlock variables from the read-only and read-write variable collection properties  
                if (Dts.Variables.Count != 0)  
                {  
                    Dts.Variables.Unlock();  
                }  
            }  
            catch  
            {  
            }  
        }  
  
        #region VSTA generated code  
        private void InternalStartup()  
        {  
            this.Startup += new System.EventHandler(ScriptMain_Startup);  
            this.Shutdown += new System.EventHandler(ScriptMain_Shutdown);  
        }  
        enum ScriptResults  
        {  
            Success = DTSExecResult.Success,  
            Failure = DTSExecResult.Failure  
        };  
  
        #endregion  
  
        /*  
The execution engine calls this method when the task executes.  
To access the object model, use the Dts property. Connections, variables, events,  
and logging features are available as members of the Dts property as shown in the following examples.  
  
To reference a variable, call Dts.Variables["MyCaseSensitiveVariableName"].Value;  
To post a log entry, call Dts.Log("This is my log text", 999, null);  
To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, true);  
  
To use the connections collection use something like the following:  
ConnectionManager cm = Dts.Connections.Add("OLEDB");  
cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;";  
  
Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.  
  
To open Help, press F1.  
*/  
  
        public void Main()  
        {  
            // TODO: Add your code here  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
    }  
```  
  
### <a name="additional-project-items-in-the-script-task-project"></a>스크립트 태스크 프로젝트의 추가 프로젝트 항목  
 스크립트 태스크 프로젝트 기본값 이외의 다른 항목에 포함할 수 **ScriptMain** 항목입니다. 이 프로젝트에는 클래스, 모듈 및 코드 파일을 추가할 수 있습니다. 폴더를 사용하여 항목 그룹을 구성할 수도 있습니다. 추가하는 모든 항목은 패키지 내부에 지속됩니다.  
  
### <a name="references-in-the-script-task-project"></a>스크립트 태스크 프로젝트의 참조  
 스크립트 태스크 프로젝트를 마우스 오른쪽 단추로 클릭 하 여 관리 되는 어셈블리에 대 한 참조를 추가할 수 있습니다 **프로젝트 탐색기**을 클릭 한 다음 **참조 추가**합니다. 자세한 내용은 참조 [스크립팅 솔루션에서 다른 어셈블리 참조](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md)합니다.  
  
> [!NOTE]  
>  VSTA IDE에서 프로젝트 참조를 볼 수 있습니다 **클래스 뷰** 또는 **프로젝트 탐색기**합니다. 이들이 창 중 하나를 열면는 **보기** 메뉴. 새 참조를 추가할 수는 **프로젝트** 메뉴에서 **프로젝트 탐색기**, 또는 **클래스 뷰**합니다.  
  
## <a name="interacting-with-the-package-in-the-script-task"></a>스크립트 태스크에서 패키지와 상호 작용  
 스크립트 태스크를 사용 하 여 전역 **Dts** 인스턴스 개체의는 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 클래스 및 해당 멤버를 포함 하는 패키지와 상호 작용 하는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 런타임.  
  
 다음 표에서의 주요 공용 멤버를 보여 줍니다.는 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 전역 통해 스크립트 태스크 코드에 제공 되는 클래스 **Dts** 개체입니다. 이 섹션의 항목에서는 이러한 멤버의 사용 방법을 보다 자세히 설명합니다.  
  
|멤버|용도|  
|------------|-------------|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>|패키지에 정의된 연결 관리자에 액세스할 수 있게 해 줍니다.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>|스크립트 태스크에서 오류, 경고 및 정보 메시지를 발생시킬 수 있게 해 주는 이벤트 인터페이스를 제공합니다.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>|런타임에 단일 개체를 반환 하는 간단한 방법을 제공 (외에 **TaskResult**) 워크플로 분기에 사용할 수도 있는 합니다.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>|사용하도록 설정된 로그 공급자에 태스크 진행률 및 결과 등의 정보를 로깅합니다.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A>|태스크의 성공 또는 실패를 보고합니다.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Transaction%2A>|태스크의 컨테이너가 실행 중인 트랜잭션을 제공합니다.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>|에 나열 된 변수에 액세스할 수 있도록는 **ReadOnlyVariables** 및 **ReadWriteVariables** 스크립트 내에서 사용 하기 위해 속성 작업입니다.|  
  
 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 클래스에는 대개 사용하지 않는 공용 멤버도 일부 포함되어 있습니다.  
  
|멤버|Description|  
|------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 속성은 변수에 보다 편리하게 액세스할 수 있게 해 줍니다. <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>를 사용할 수도 있지만 읽기 및 쓰기를 위해 변수를 잠그거나 잠금 해제하려면 명시적으로 메서드를 호출해야 합니다. 스크립트 태스크에서는 개발자가 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 속성을 사용할 때 잠금 의미 체계를 자동으로 처리합니다.|  
  
## <a name="debugging-the-script-task"></a>스크립트 태스크 디버깅  
 스크립트 태스크의 코드를 디버깅하려면 코드에 하나 이상의 중단점을 설정한 다음 VSTA IDE를 닫고 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 패키지를 실행합니다. 패키지 실행 중 스크립트 태스크 실행이 시작되면 VSTA IDE가 다시 열리고 코드가 읽기 전용 모드에서 열립니다. 중단점에 도달한 후에는 변수 값을 검사하고 나머지 코드를 단계별로 실행할 수 있습니다.  
  
> [!WARNING]  
>  64비트 모드로 패키지를 실행할 때 스크립트 태스크를 디버깅할 수 있습니다.  
  
> [!NOTE]  
>  스크립트 태스크를 디버깅하려면 패키지를 실행해야 합니다. 개별 태스크만 실행하면 스크립트 태스크 코드의 중단점이 무시됩니다.  
  
> [!NOTE]  
>  스크립트 태스크를 패키지 실행 태스크에서 실행된 자식 패키지의 일부로 실행할 경우에는 스크립트 태스크를 디버깅할 수 없습니다. 이러한 경우에는 자식 패키지에서 스크립트 태스크에 설정한 중단점이 무시됩니다. 자식 패키지는 별도로 실행하여 정상적으로 디버깅할 수 있습니다.  
  
> [!NOTE]  
>  여러 스크립트 태스크가 포함되어 있는 패키지를 디버깅하는 경우 디버거는 한 개의 스크립트 태스크를 디버깅합니다. Foreach 루프 또는 For 루프 컨테이너의 경우와 같이 디버거가 완료되는 경우 시스템에서 다른 스크립트 태스크를 디버깅할 수 있습니다.  
  
## <a name="external-resources"></a>외부 리소스  
  
-   블로그 항목- [SSIS 2008 및 R2 설치의 VSTA 설치 및 구성 문제](http://go.microsoft.com/fwlink/?LinkId=215661), blogs.msdn.com에서 합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [스크립팅 솔루션에서 다른 어셈블리 참조](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md)   
 [스크립트 태스크 편집기에서 스크립트 태스크 구성](../../../integration-services/extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)  
  
  