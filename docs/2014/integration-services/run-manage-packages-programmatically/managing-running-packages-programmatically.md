---
title: 프로그래밍 방식으로 패키지 실행 관리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
helpviewer_keywords:
- packages [Integration Services], managing
- running packages [Integration Services]
ms.assetid: 0e91f4ac-6f29-40d7-8c28-9b82e4802c35
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b6537078fed6047fa16d759635d18ec484612b12
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48070681"
---
# <a name="managing-running-packages-programmatically"></a>프로그래밍 방식으로 실행 중인 패키지 관리
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 프로그래밍 방식으로 사용할 때 현재 실행 중인 패키지를 확인할 수 있습니다. <xref:Microsoft.SqlServer.Dts.Runtime.Application> 네임스페이스의 <xref:Microsoft.SqlServer.Dts.Runtime> 클래스는 이 요구 사항을 충족하기 위한 메서드와 클래스를 제공합니다.  
  
 패키지 모니터링에 대한 자세한 내용은 [패키지 관리&#40;SSIS 서비스&#41;](../service/package-management-ssis-service.md)를 참조하세요.  
  
 이 항목에서 설명한 모든 메서드에는 `Microsoft.SqlServer.ManagedDTS` 어셈블리에 대한 참조가 있어야 합니다. 새 프로젝트에 참조를 추가한 후 `using` 또는 `Imports` 문을 사용하여 <xref:Microsoft.SqlServer.Dts.Runtime> 네임스페이스를 가져오십시오.  
  
> [!IMPORTANT]  
>  SSIS 패키지 저장소를 사용하기 위한 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 클래스의 메서드는 ".", localhost 또는 로컬 서버의 서버 이름만 지원합니다. "(local)"은 사용할 수 없습니다.  
  
## <a name="determining-which-packages-are-currently-running"></a>현재 실행 중인 패키지 확인  
 지정한 서버에서 현재 실행 중인 패키지를 확인하려면 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetRunningPackages%2A> 메서드를 호출합니다. 이 메서드는 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> 개체의 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> 컬렉션을 반환합니다.  
  
> [!NOTE]  
>  관리자는 컴퓨터에서 현재 실행 중인 모든 패키지를 볼 수 있고 다른 사용자는 자신이 실행한 패키지만 볼 수 있습니다.  
  
## <a name="working-with-running-packages"></a>실행 중인 패키지 작업  
 현재 실행 중인 패키지를 확인한 후에는 패키지에 대한 정보를 가져오고 패키지를 중지하도록 요청할 수 있습니다.  
  
### <a name="getting-information-about-a-running-package"></a>실행 중인 패키지에 대한 정보 얻기  
 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> 컬렉션을 반복할 때 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> 개체의 속성을 사용하여 패키지를 찾거나 실행 중인 패키지에 대한 추가 정보를 얻을 수 있습니다.  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionDuration%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionStartTime%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.InstanceID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageDescription%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageName%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.UserName%2A>  
  
### <a name="stopping-a-running-package"></a>실행 중인 패키지 중지  
 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.Stop%2A> 개체의 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> 메서드를 호출하여 패키지를 중지하도록 요청할 수 있습니다. 중지 요청이 실행된 시간과 패키지가 실제로 중지되는 시간 사이에는 지연이 있을 수 있습니다.  
  
![Integration Services 아이콘 (작은)](../media/dts-16.gif "Integration Services 아이콘 (작은)")**Integration Services를 사용 하 여 날짜를 알림 설정** <br /> Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.<br /><br /> [MSDN의 Integration Services 페이지 방문](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> 이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.  
  
## <a name="see-also"></a>관련 항목  
 [패키지 관리&#40;SSIS 서비스&#41;](../service/package-management-ssis-service.md)   
 [프로그래밍 방식으로 사용 가능 패키지 열거](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
