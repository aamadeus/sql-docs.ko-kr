---
title: '3 단원: 패키지 설치 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 87bc4d82-39d8-424f-886f-98cf1e4bb07a
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1ded3fa139483e5a9e3c337bbfd8c63825a749a9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48130033"
---
# <a name="lesson-3-installing-packages"></a>3단원: 패키지 설치
  [2 단원: 배포 번들 만들기](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md), 배포 유틸리티를 만든 항목이 포함 된 배포 번들을 생성 및 다른 컴퓨터에서 패키지를 설치 해야 합니다. 또한 배포 번들에서 파일 목록을 확인하고 배포 유틸리티를 작성할 때 만들었던 매니페스트 파일의 내용을 검사했습니다.  
  
 이 단원에서는 배포 번들을 대상 컴퓨터에 복사한 다음 패키지 설치 마법사를 실행하여 패키지, 패키지 종속 파일 및 보조 파일을 해당 컴퓨터에 설치합니다. 패키지는 **msdb**[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스에 설치되고 다른 항목은 파일 시스템에 설치됩니다. 패키지 설치를 완료한 후에 패키지 실행 유틸리티를 통해 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 에서 패키지를 실행하여 배포를 테스트합니다.  
  
 **이 단원에 소요되는 예상 시간:** 30분  
  
## <a name="lesson-tasks"></a>단원 태스크  
 이 단원에서는 다음 태스크를 다룹니다.  
  
-   [1단계: 배포 번들 복사](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
-   [2단계: 패키지 설치 마법사 실행](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
-   [3단계: 배포된 패키지 테스트](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
## <a name="start-the-lesson"></a>단원 시작  
 [1단계: 배포 번들 복사](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
![Integration Services 아이콘 (작은)](media/dts-16.gif "Integration Services 아이콘 (작은)")**Integration Services를 사용 하 여 날짜를 알림 설정** <br /> Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.<br /><br /> [MSDN의 Integration Services 페이지 방문](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> 이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.  
  
  
