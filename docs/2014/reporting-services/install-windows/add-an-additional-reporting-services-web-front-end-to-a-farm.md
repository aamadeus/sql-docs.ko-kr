---
title: 팜에 추가 Reporting Services 웹 프런트 엔드 추가 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7a11bda-ae26-49ac-b071-37d83cae5afe
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 203bd23082d0dcf6e6f9e38d83c25fce6eef2125
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36185782"
---
# <a name="add-an-additional-reporting-services-web-front-end-to-a-farm"></a>팜에 추가 Reporting Services 웹 프런트 엔드 추가
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드에는 응용 프로그램 서버와 WFE(웹 프런트 엔드) 서버에 필요한 구성 요소가 포함됩니다. 이 항목은 구독, 데이터 경고 및 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 같은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능에서 사용하는 응용 프로그램 페이지를 포함하여 WFE 서버에 필요한 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]구성 요소 설치에 대해 설명합니다. WFE에 필요한 기본 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치는 SharePoint 2010 제품용 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능을 설치하는 것입니다.  
  
## <a name="prerequisites"></a>사전 요구 사항  
  
-   SQL Server 설치 프로그램을 실행하려면 로컬 관리자여야 합니다.  
  
-   컴퓨터가 도메인에 조인되어 있어야 합니다.  
  
-   SharePoint 구성과 콘텐츠 데이터베이스를 호스팅하는 기존 데이터베이스 서버의 이름을 알고 있어야 합니다.  
  
-   원격 데이터베이스 연결을 허용하도록 데이터베이스 서버를 구성해야 합니다.  이렇게 하지 않으면 새 서버는 SharePoint 구성 데이터베이스에 연결할 수 없기 때문에 새 서버를 팜에 조인할 수 없습니다.  
  
-   현재 팜 서버에서 실행하고 있는 것과 같은 버전의 SharePoint가 새 서버에 설치되어 있어야 합니다. 예를 들어 팜에 이미 SharePoint 2010 SP1(서비스 팩 1)이 설치된 경우 팜을 조인하려면 새 서버에도 SP1을 설치해야 합니다.  
  
-   시스템 및 버전 요구 사항을 이해하려면 다음 항목을 검토하십시오.  
  
     [SharePoint 2010 팜에서 SQL Server BI 기능을 사용하기 위한 지침](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
## <a name="steps"></a>단계  
 이 항목의 단계에서는 SharePoint 팜 관리자가 서버를 설치하고 구성한다고 가정합니다. 다이어그램은 일반적인 3계층 환경을 보여주고 다이어그램의 번호가 매겨진 항목이 다음 목록에 설명됩니다.  
  
-   (1) 여러 WFE(웹 프런트 엔드) 서버. WFE 서버에는 SharePoint 2010용 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능이 필요합니다. 다음 단계에서는 두 번째 응용 프로그램 서버를 이 계층에 추가합니다.  
  
-   (2) [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 실행하는 두 응용 프로그램 서버 및 중앙 관리 같은 웹 사이트.  
  
-   (3) 두 SQL Server 데이터베이스 서버.  
  
-   (4) 소프트웨어 또는 하드웨어 네트워크 부하 분산 솔루션(NLB)을 나타냅니다.  
  
 ![새 SharePoint WFE에 SSRS 추가](../../../2014/sql-server/install/media/rs-sharepointscale-wfe.gif "새 SharePoint WFE에 SSRS 추가")  
  
 다음 단계에서는 관리자가 서버를 설치하고 구성한다고 가정합니다.  
  
|단계|설명 및 링크|  
|----------|--------------------------|  
|SharePoint 2010 제품 준비 도구 실행|SharePoint 2010 설치 미디어가 있어야 합니다. 준비 도구는 설치 미디어의 **PrerequisiteInstaller.exe** 입니다.|  
|SharePoint 2010 제품 설치|1) 선택 된 **서버 팜** 설치 유형입니다.<br /><br /> 2) 선택 **완료** 서버 유형에 대 한 합니다.<br /><br /> 3) 기존 SharePoint 팜에 SharePoint 2010 SP1이 설치되어 있으면 설치가 완료된 후 SharePoint 제품 구성 마법사를 실행하지 마세요. SharePoint 제품 구성 마법사를 실행하기 전에 SharePoint SP1을 설치해야 합니다.|  
|SharePoint Server 2010 SP1 설치|기존 SharePoint 팜에 SharePoint 2010 SP1 다운로드 하 여 SharePoint 2010 s p 1에서 설치 하는 경우:[http://support.microsoft.com/kb/2460045](http://go.microsoft.com/fwlink/p/?linkID=219697)합니다.<br /><br /> SharePoint 2010 SP1에 대한 자세한 내용은 [Office 2010 SP1 및 SharePoint 2010 SP1을 설치할 때의 알려진 문제](http://support.microsoft.com/kb/2532126)를 참조하십시오.|  
|SharePoint 제품 구성 마법사를 실행하여 팜에 서버 추가|1)에 **Microsoft SharePoint 2010 제품** 프로그램 그룹에서 클릭 **Microsoft SharePoint 2010 제품 구성 마법사**합니다.<br /><br /> 2)는 **서버 팜에 연결** 페이지 선택 **기존 팜에 연결** 클릭 **다음**합니다.<br /><br /> 3)는 **구성 데이터베이스 설정 지정** 페이지에서 기존 팜 구성 데이터베이스의 이름에 사용 되는 데이터베이스 서버의 이름을 입력 합니다. **다음**을 클릭합니다.<br />**\*\* 중요 한 \* \***  다음과 비슷한 오류 메시지가 나타나고 권한이 확인 한 경우의에서 SQL Server 네트워크 구성을 위해 어떤 프로토콜이 활성화 되었는지 확인 한 다음 **Sql Server Configuration Manager**합니다. "데이터베이스 서버에 연결 하지 못했습니다. 데이터베이스가 존재, Sql Server, 하며 서버에 액세스 하는 적절 한 권한이 있는지 확인 합니다. "<br />**\*\* 중요 한 \* \***  페이지를 참조 하는 경우 **서버 팜 제품 및 패치 상태**를 페이지에 대 한 정보를 검토 하 고 계속 하려면 먼저 서버를 필요한 파일에 업데이트 해야 합니다 서버를 팜에 조인 합니다.<br /><br /> 4)는 **팜 보안 설정 지정** 페이지에서 팜 암호를 입력 하 고 클릭 **다음**합니다. 확인 페이지에서 **다음** 을 클릭하여 마법사를 실행합니다.<br /><br /> 5) 클릭 **다음** 실행 하는 **팜 구성 마법사**합니다.|  
|서버가 SharePoint 팜에 추가되었는지 확인|1) SharePoint 중앙 관리의 **시스템 설정** 그룹에서 **이 팜의 서버 관리** 를 클릭합니다.<br /><br /> 2) 새 서버가 추가되었고 상태가 올바른지 확인합니다.<br /><br /> 3) WFE 역할에서이 서버를 제거 하려면 클릭 **서버의 서비스 관리** 서비스를 중지 하 고 **Microsoft SharePoint Foundation 웹 응용 프로그램**합니다.|  
|설치는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능에서 SharePoint 2010 제품에 대 한 합니다.|추가 기능을 설치하는 방법은 여러 가지가 있습니다. 다음 단계는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 마법사를 사용합니다. 추가 기능을 설치 하는 방법에 대 한 자세한 내용은 참조 하십시오. [설치 SharePoint 용 Reporting Services 추가 기능을 제거 하거나 &#40;SharePoint 2010 및 SharePoint 2013&#41;](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)합니다. 실행 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치:<br /><br /> 1) **설치 역할** 페이지에서 **SQL Server 기능 설치**를 선택합니다.<br /><br /> 2)는 **기능 선택** 페이지에서 **Reporting Services 추가 기능을 SharePoint 제품에 대 한**<br /><br /> 3)을 클릭 **다음** 설치 옵션을 완료 한 다음 여러 페이지에 있습니다.<br /><br /> 설치에 대 한 자세한 내용은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], 참조 [Reporting Services SharePoint 모드 설치에 대 한 SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|새 서버가 작동하는지 확인합니다.|1) SharePoint 중앙 관리의 **시스템 설정** 그룹에서 **이 팜의 서버 관리** 를 클릭합니다.<br /><br /> 2) 새 서버가 목록에 있는지 확인합니다.|  
|NLB 솔루션을 업데이트합니다.|해당하는 경우 새 서버를 포함하도록 하드웨어 또는 소프트웨어 NLB 환경을 업데이트합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [추가 웹 또는 응용 프로그램 서버 팜 (SharePoint Server 2010)](http://technet.microsoft.com/library/bb218968.aspx?missingurl=%2fen-us%2flibrary%2fe1aeaddf-6ee4-43a9-82b7-db20b68c71db\(Office.14\))   
 [(SharePoint Server 2010) 서비스 구성](http://technet.microsoft.com/library/ee794878.aspx)  
  
  