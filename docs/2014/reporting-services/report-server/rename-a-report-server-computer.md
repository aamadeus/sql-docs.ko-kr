---
title: 보고서 서버 컴퓨터 이름 바꾸기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- renaming report servers
ms.assetid: 82fc4ba2-291a-4939-a025-271b8d687c54
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c040f3afade749772ae1560e9f99af8cd4ac0a85
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48114293"
---
# <a name="rename-a-report-server-computer"></a>보고서 서버 컴퓨터 이름 바꾸기
  컴퓨터 이름을 바꾸면 웹 서버 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 같은 컴퓨터에 있는 경우 이에 해당하는 이름이 변경됩니다. 컴퓨터 이름을 변경한 다음에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에 액세스할 수 없는 경우도 있습니다. 컴퓨터 이름을 변경한 다음에는 이 항목의 단계를 사용하여 보고서 서버를 다시 구성합니다.  
  
## <a name="renaming-a-sql-server-database-engine"></a>SQL Server 데이터베이스 엔진 이름 바꾸기  
 보고서 서버 데이터베이스를 실행하는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스의 이름을 바꾸는 경우 다음을 수행하십시오.  
  
1.  Reporting Services 구성 도구를 시작한 다음 이름이 바뀐 서버에 있는 보고서 서버 데이터베이스를 사용하는 보고서 서버에 연결합니다.  
  
2.  데이터베이스 설치 페이지를 엽니다.  
  
3.  **서버 이름**에서 해당 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이름을 입력하거나 선택한 다음 **연결**을 클릭합니다.  
  
4.  **적용**을 클릭합니다.  
  
 보고서 서버에서 로컬 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스를 사용하는 경우 *(local)* 또는 *(local)\instancename* 을 사용하여 서버를 지정할 수 있습니다. *(local)* 을 사용하여 서버를 참조하는 경우에는 서버 이름을 바꿔도 연결에 문제가 생기지 않습니다. 원격 서버를 사용하거나 서버 이름을 사용하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 구성하는 경우에는 서버 이름을 변경할 때마다 데이터베이스 연결 정보를 업데이트해야 합니다.  
  
## <a name="renaming-a-report-server-computer"></a>보고서 서버 컴퓨터 이름 바꾸기  
 보고서 서버를 실행하는 컴퓨터의 이름을 바꾸는 경우 다음을 수행하십시오.  
  
1.  오픈 **RSReportServer.config** 텍스트 편집기에서 수정 하 고는 `UrlRoot` 새 서버 이름을 반영 하도록 설정 합니다. `UrlRoot` 설정은 배달 확장 프로그램에서 보고서 서버에 저장된 항목 액세스에 사용하는 URL을 작성하는 데 사용됩니다. 업데이트 해야 보고서 서버 URL 주소를 변경 합니다 `UrlRoot` 구독 계속 예상 대로 보고서를 제공할 수 있도록 설정 합니다.  
  
2.  동일한 파일에서이 속성을 설정 하는 경우 수정 된 `ReportServerUrl` 새 서버 이름을 반영 하도록 설정 합니다. 이 설정이 모든 설치에 사용되는 것은 아닙니다. 이 설정이 비어 있는 경우 아무 작업도 수행하지 마십시오.  
  
    > [!NOTE]  
    >  회사 네트워크에서 WINS(Windows Internet Naming Service)를 사용하는 경우 보고서 서버와 보고서 관리자가 일정 기간 동안 이전 이름으로 사용 가능하다고 표시될 수 있습니다. WINS에서는 서비스하는 각 컴퓨터에 IP 주소를 매핑합니다. WINS에서 이름이 바뀐 컴퓨터의 IP 주소를 새로 고친 다음에는 더 이상 이전 컴퓨터 이름을 사용하여 보고서 서버나 보고서 관리자에 액세스할 수 없습니다.  
  
## <a name="see-also"></a>관련 항목  
 [RSReportServer 구성 파일](rsreportserver-config-configuration-file.md)   
 [Reporting Services 구성 관리자 &#40;기본 모드&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Reporting Services 보고서 서버&#40;기본 모드&#41;](reporting-services-report-server-native-mode.md)   
 [보고서 서버 서비스 시작 및 중지](start-and-stop-the-report-server-service.md)   
 [rsconfig 유틸리티&#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md)  
  
  
