---
title: '1단계: 작업 폴더 및 환경 변수 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 45091ba2-ea3d-4399-9814-489d812b42cc
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 640d865069769d826b3d0a3f7839c718bdf47cd6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201253"
---
# <a name="step-1-creating-working-folders-and-environment-variables"></a>1단계: 작업 폴더 및 환경 변수 만들기
  이 태스크에서는 이후의 자습서 태스크에서 사용할 작업 폴더(C:\DeploymentTutorial)와 새 시스템 환경 변수(`DataTransfer` 및 `LoadXMLData`)를 만듭니다.  
  
 작업 폴더는 C 드라이브의 루트에 있습니다. 필요한 경우 다른 드라이브나 위치를 사용할 수 있습니다. 단, 해당 위치를 메모해 두었다가 자습서에서 DeploymentTutorial 작업 폴더의 위치를 참조할 때마다 사용해야 합니다.  
  
 이후 단원에서는 파일 시스템에 저장된 패키지를 msdb[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스의 sysssispackages 테이블에 배포합니다. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 다른 컴퓨터에 배포하는 것이 가장 좋습니다. 그렇게 할 수 없는 경우에는 로컬 컴퓨터에 있는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 패키지를 배포하여 이 자습서에서 수행하는 많은 것들을 배울 수 있습니다. 로컬 및 대상 컴퓨터에서 사용되는 환경 변수는 동일한 변수 이름을 가져야 하지만 변수에 다른 값이 저장됩니다. 예를 들어 로컬 컴퓨터에서 `DataTransfer` 환경 변수의 값은 C:\DeploymentTutorial 폴더를 참조하고 대상 컴퓨터에서 `DataTransfer` 환경 변수는 C:\DeploymentTutorialInstall 폴더를 참조합니다.  
  
 로컬 컴퓨터에 배포하려는 경우 하나의 환경 변수 집합만 만들어야 합니다. 단, 로컬 배포를 수행하기 전에 환경 변수의 값을 적절한 값으로 업데이트해야 합니다.  
  
 패키지를 다른 컴퓨터에 배포하려는 경우 두 개의 환경 변수 집합을 만들어야 합니다. 이러한 집합 중 하나는 로컬 컴퓨터용이고 다른 하나는 대상 컴퓨터용입니다. 지금은 원본 컴퓨터에 대한 변수만 만들 수 있고 나중에 대상 컴퓨터에 대한 변수를 만들 수 있지만 패키지를 대상 컴퓨터에 설치할 수 있으려면 폴더 및 환경 변수를 대상 컴퓨터에서 모두 사용할 수 있어야 합니다.  
  
### <a name="to-create-the-local-working-folder"></a>로컬 작업 폴더를 만들려면  
  
1.  시작 메뉴를 마우스 오른쪽 단추로 클릭하고 탐색을 클릭합니다.  
  
2.  **로컬 디스크(C:)** 를 클릭합니다.  
  
3.  **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **폴더**를 클릭합니다.  
  
4.  새 폴더 이름 바꾸기 `DeploymentTutorial`합니다.  
  
### <a name="to-create-local-environment-variables"></a>로컬 환경 변수를 만들려면  
  
1.  **시작** 메뉴에서 **제어판**을 클릭합니다.  
  
2.  제어판에서 **시스템**을 두 번 클릭합니다.  
  
3.  **시스템 속성** 대화 상자에서 **고급** 탭을 클릭한 다음 **환경 변수**를 클릭합니다.  
  
4.  **환경 변수** 대화 상자의 **시스템 변수** 프레임에서 **새로 만들기**를 클릭합니다.  
  
5.  에 **새 시스템 변수** 대화 상자에서 `DataTransfer` 에 **변수 이름** 상자 및 `C:\DeploymentTutorial\datatransferconfig.dtsconfig` 에서 **변수 값** 상자.  
  
6.  **확인**을 클릭합니다.  
  
7.  클릭 **새로 만들기** 다시 유형과 `LoadXMLData` 에 **변수 이름** 상자 및 `C:\DeploymentTutorial\loadxmldataconfig.dtsconfig` 에 **변수 값** 상자.  
  
8.  **확인** 을 클릭하여 **환경 변수** 대화 상자를 종료합니다.  
  
9. **확인** 을 클릭하여 **시스템 속성** 대화 상자를 종료합니다.  
  
10. 필요에 따라 컴퓨터를 다시 시작합니다. 컴퓨터를 다시 시작하지 않을 경우 새 변수의 이름이 패키지 구성 마법사에 표시되지 않지만 새 변수를 사용할 수는 있습니다.  
  
### <a name="to-create-destination-environment-variables"></a>대상 환경 변수를 만들려면  
  
1.  **시작** 메뉴에서 **제어판**을 클릭합니다.  
  
2.  제어판에서 **시스템**을 두 번 클릭합니다.  
  
3.  **시스템 속성** 대화 상자에서 **고급** 탭을 클릭한 다음 **환경 변수**를 클릭합니다.  
  
4.  **환경 변수** 대화 상자의 **시스템 변수** 프레임에서 **새로 만들기**를 클릭합니다.  
  
5.  에 **새 시스템 변수** 대화 상자에서 `DataTransfer` 에 **변수 이름** 상자 및 `C:\DeploymentTutorialInstall\datatransferconfig.dtsconfig` 에서 **변수 값** 상자.  
  
6.  **확인**을 클릭합니다.  
  
7.  클릭 **새로 만들기** 다시 유형과 `LoadXMLData` 에 **변수 이름** 상자 및 `C:\DeploymentTutorialInstall\loadxmldataconfig.dtsconfig` 에 **변수 값** 상자.  
  
8.  **확인** 을 클릭하여 **환경 변수** 대화 상자를 종료합니다.  
  
9. **확인** 을 클릭하여 **시스템 속성** 대화 상자를 종료합니다.  
  
10. 필요에 따라 컴퓨터를 다시 시작합니다.  
  
## <a name="next-task-in-lesson"></a>단원의 다음 태스크  
 [2단계: 배포 프로젝트 만들기](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
![Integration Services 아이콘 (작은)](media/dts-16.gif "Integration Services 아이콘 (작은)")**Integration Services를 사용 하 여 날짜를 알림 설정** <br /> Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.<br /><br /> [MSDN의 Integration Services 페이지 방문](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> 이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.  
  
  
