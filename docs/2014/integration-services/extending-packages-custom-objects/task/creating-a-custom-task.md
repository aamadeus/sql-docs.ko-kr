---
title: 사용자 지정 태스크 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
helpviewer_keywords:
- custom tasks [Integration Services], creating
ms.assetid: 42965c09-1782-4cdb-9ce1-216af4c23e0a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a4e390e13f44bcf09a698ebf8a13e363c5b085c8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48193183"
---
# <a name="creating-a-custom-task"></a>사용자 지정 태스크 만들기
  사용자 지정 태스크를 만드는 단계는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]의 다른 사용자 지정 개체를 만드는 단계와 비슷합니다.  
  
-   기본 클래스에서 상속되는 새 클래스를 만듭니다. 태스크의 경우 기본 클래스는 <xref:Microsoft.SqlServer.Dts.Runtime.Task>입니다.  
  
-   개체 유형을 식별하는 특성을 클래스에 적용합니다. 태스크의 경우 이 특성은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>입니다.  
  
-   기본 클래스의 메서드 및 속성 구현을 재정의합니다. 태스크의 경우 이러한 메서드로는 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 메서드가 포함됩니다.  
  
-   필요한 경우 사용자 지정 사용자 인터페이스를 개발합니다. 태스크의 경우 사용자 지정 사용자 인터페이스를 개발하려면 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> 인터페이스를 구현하는 클래스가 필요합니다.  
  
## <a name="getting-started-with-a-custom-task"></a>사용자 지정 태스크 시작  
  
### <a name="creating-projects-and-classes"></a>프로젝트 및 클래스 만들기  
 관리되는 태스크는 모두 <xref:Microsoft.SqlServer.Dts.Runtime.Task> 기본 클래스에서 파생되므로 사용자 지정 태스크를 만들려면 먼저 관리되는 프로그래밍 언어로 클래스 라이브러리 프로젝트를 만들고 기본 클래스에서 상속되는 클래스를 만들어야 합니다. 이 파생 클래스에서 기본 클래스의 메서드 및 속성을 재정의하여 사용자 지정 기능을 구현합니다.  
  
 동일한 솔루션에서 사용자 지정 사용자 인터페이스에 대한 두 번째 클래스 라이브러리 프로젝트를 만듭니다. 배포를 쉽게 하려면 사용자 인터페이스에 대한 별도의 어셈블리를 만드는 것이 좋습니다. 이렇게 하면 연결 관리자 또는 해당 사용자 인터페이스를 독립적으로 업데이트하거나 다시 배포할 수 있기 때문입니다.  
  
 강력한 이름 키 파일을 사용하여 빌드 시 생성될 어셈블리에 서명하도록 두 프로젝트를 구성합니다.  
  
### <a name="applying-the-dtstask-attribute"></a>DtsTask 특성 적용  
 앞에서 만든 클래스에 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 특성을 적용하여 해당 클래스를 태스크로 식별합니다. 이 특성은 태스크의 이름, 설명 및 태스크 유형 같은 디자인 타임 정보를 제공합니다.  
  
 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> 속성을 사용하여 태스크를 사용자 지정 사용자 인터페이스에 연결합니다. 이 속성에 필요한 공개 키 토큰을 가져오려면 **sn.exe -t**를 사용하여 사용자 인터페이스 어셈블리 서명에 사용할 키 쌍(.snk) 파일의 공개 키 토큰을 표시할 수 있습니다.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.SSIS.Samples  
{  
  [DtsTask  
  (  
   DisplayName = "MyTask",  
   IconResource = "MyTask.MyTaskIcon.ico",  
   UITypeName = "My Custom Task," +  
   "Version=1.0.0.0," +  
   "Culture = Neutral," +  
   "PublicKeyToken = 12345abc6789de01",  
   TaskType = "PackageMaintenance",  
   TaskContact = "MyTask; company name; any other information",  
   RequiredProductLevel = DTSProductLevel.None  
   )]  
  public class MyTask : Task  
  {  
    // Your code here.  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsTask(DisplayName:="MyTask", _  
 IconResource:="MyTask.MyTaskIcon.ico", _  
 UITypeName:="My Custom Task," & _  
 "Version=1.0.0.0,Culture=Neutral," & _  
 "PublicKeyToken=12345abc6789de01", _  
 TaskType:="PackageMaintenance", _  
 TaskContact:="MyTask; company name; any other information", _  
 RequiredProductLevel:=DTSProductLevel.None)> _  
Public Class MyTask  
  Inherits Task  
  
  ' Your code here.  
  
End Class 'MyTask  
```  
  
## <a name="building-deploying-and-debugging-a-custom-task"></a>사용자 지정 태스크 빌드, 배포 및 디버깅  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 사용자 지정 태스크의 빌드, 배포 및 디버깅 단계는 다른 형식의 사용자 지정 개체에 대해 필요한 단계와 비슷합니다. 자세한 내용은 [사용자 지정 개체 빌드, 배포 및 디버그](../building-deploying-and-debugging-custom-objects.md)를 참조하세요.  
  
![Integration Services 아이콘 (작은)](../../media/dts-16.gif "Integration Services 아이콘 (작은)")**Integration Services를 사용 하 여 날짜를 알림 설정** <br /> Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.<br /><br /> [MSDN의 Integration Services 페이지 방문](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> 이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.  
  
## <a name="see-also"></a>관련 항목  
 [사용자 지정 태스크 만들기](creating-a-custom-task.md)   
 [사용자 지정 태스크 코딩](coding-a-custom-task.md)   
 [사용자 지정 태스크의 사용자 인터페이스 개발](developing-a-user-interface-for-a-custom-task.md)  
  
  
