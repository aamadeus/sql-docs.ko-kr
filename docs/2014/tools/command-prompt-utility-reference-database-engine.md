---
title: 명령 프롬프트 유틸리티 참조 (데이터베이스 엔진) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server]
- command prompt utilities [SQL Server], about command prompt utilities
- command prompt [SQL Server]
- utilities [SQL Server], command prompt
- command prompt [SQL Server], utilities
ms.assetid: 48364bd9-6ea7-45e9-a332-acf3d81bbfae
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1f3e2995450e23cc5217ef4437a1319833f50243
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48070860"
---
# <a name="command-prompt-utility-reference-database-engine"></a>명령 프롬프트 유틸리티 참조(데이터베이스 엔진)
  명령 프롬프트 유틸리티를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 작업을 스크립트로 작성할 수 있습니다. 다음 표에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 제공하는 명령 프롬프트 유틸리티를 보여 줍니다.  
  
|**유틸리티**|**설명**|**설치 위치**|  
|-----------------|---------------------|----------------------|  
|[bcp 유틸리티](bcp-utility.md)|[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스와 사용자가 지정한 형식의 데이터 파일 간에 데이터를 복사하는 데 사용합니다.|\<*drive*:>\Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[dta Utility](dta/dta-utility.md)|작업을 분석하고 해당 작업에서 서버 성능을 최적화하기 위한 물리적 디자인 구조를 제시하는 데 사용합니다.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[dtexec 유틸리티](../integration-services/packages/dtexec-utility.md)|[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 구성 및 실행하는 데 사용합니다. 이 명령 프롬프트 유틸리티의 사용자 인터페이스 버전을 **DTExecUI**라고 하며 이는 패키지 실행 유틸리티를 표시합니다.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[dtutil 유틸리티](../integration-services/dtutil-utility.md)|SSIS 패키지를 관리하는 데 사용합니다.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[배포 유틸리티를 사용하여 모델 솔루션 배포](../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트를 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스에 배포하는 데 사용합니다.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VShell\Common7\IDE|  
|[osql 유틸리티](osql-utility.md)|명령 프롬프트에서 [!INCLUDE[tsql](../includes/tsql-md.md)] 문, 시스템 프로시저 및 스크립트 파일을 입력할 수 있습니다.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[프로파일러 유틸리티](profiler-utility.md)|명령 프롬프트에서 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 를 시작하는 데 사용합니다.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[RS.exe 유틸리티&#40;SSRS&#41;](../reporting-services/tools/rs-exe-utility-ssrs.md)|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 서버를 관리하기 위한 스크립트를 실행하는 데 사용합니다.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[rsconfig 유틸리티&#40;SSRS&#41;](../reporting-services/tools/rsconfig-utility-ssrs.md)|보고서 서버 연결을 구성하는 데 사용합니다.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[rskeymgmt 유틸리티&#40;SSRS&#41;](../reporting-services/tools/rskeymgmt-utility-ssrs.md)|보고서 서버에서 암호화 키를 관리하는 데 사용합니다.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlagent90 응용 프로그램](sqlagent90-application.md)|명령 프롬프트에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트를 시작하는 데 사용합니다.|\<drive>:\Program Files\Microsoft SQL Server\\<*instance_name*>\MSSQL\Binn|  
|[sqlcmd 유틸리티](sqlcmd-utility.md)|명령 프롬프트에서 [!INCLUDE[tsql](../includes/tsql-md.md)] 문, 시스템 프로시저 및 스크립트 파일을 입력할 수 있습니다.|\<*drive*:>\Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[SQLdiag 유틸리티](sqldiag-utility.md)|[!INCLUDE[msCoName](../includes/msconame-md.md)] 고객 서비스 지원 센터에 제공할 진단 정보를 수집하는 데 사용합니다.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqllogship 응용 프로그램](sqllogship-application.md)|응용 프로그램에서 백업, 복사 및 복원 작업을 실행하지 않고 로그 전달 구성에 대해 백업, 복사, 복원 작업 및 관련 정리 태스크를 수행하는 데 사용됩니다.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[SqlLocalDB 유틸리티](sqllocaldb-utility.md)|프로그램 개발자를 대상으로 하는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 실행 모드입니다.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\|  
|[sqlmaint 유틸리티](sqlmaint-utility.md)|이전 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 만든 데이터베이스 유지 관리 계획을 실행하는 데 사용합니다.|\<드라이브 >: \Program Files\Microsoft SQL Server\MSSQL12. MSSQLSERVER\MSSQL\Binn|  
|[sqlps 유틸리티](sqlps-utility.md)|PowerShell 명령 및 스크립트를 실행하는 데 사용합니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 공급자 및 cmdlet을 로드하고 등록합니다.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlservr 응용 프로그램](sqlservr-application.md)|문제 해결을 위해 명령 프롬프트에서 [!INCLUDE[ssDE](../includes/ssde-md.md)] 인스턴스를 시작 및 중지하는 데 사용합니다.|\<드라이브 >: \Program Files\Microsoft SQL Server\MSSQL12. MSSQLSERVER\MSSQL\Binn|  
|[Ssms 유틸리티](../ssms/ssms-utility.md)|명령 프롬프트에서 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 시작하는 데 사용합니다.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VSShell\Common7\IDE|  
|[tablediff 유틸리티](tablediff-utility.md)|두 테이블의 데이터를 비교하여 불일치가 있는지 확인하는 데 사용합니다. 복제 토폴로지 문제를 해결할 때 유용합니다.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]COM|  
  
 **을(를) 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 관리자에 액세스하려면(!!) [!INCLUDE[win8](../includes/win8-md.md)]**  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 관리자는 독립 실행형 프로그램이 아니라 [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console 프로그램용 스냅인이므로 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 관리자는 [!INCLUDE[win8](../includes/win8-md.md)]을(를) 실행할 때 응용 프로그램으로 표시되지 않습니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 관리자를 열려면 **검색** 참의 **앱**아래에 **SQLServerManager12.msc** ( [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]) 또는 **SQLServerManager11.msc** ([!INCLUDE[ssSQL11](../includes/sssql11-md.md)])를 입력한 다음 **Enter**키를 누릅니다.  
  
## <a name="command-prompt-utilities-syntax-conventions"></a>명령 프롬프트 유틸리티 구문 규칙  
  
|**규칙**|**사용 대상**|  
|--------------------|------------------|  
|대문자|운영 체제 수준에서 사용하는 문 및 용어|  
|`monospace`|예제 명령 및 프로그램 코드|  
|*기울임꼴*|사용자가 제공하는 매개 변수|  
|**굵게**|표시된 대로 입력해야 하는 명령, 매개 변수 및 다른 구문|  
  
## <a name="see-also"></a>관련 항목  
 [복제 배포 에이전트](../relational-databases/replication/agents/replication-distribution-agent.md)   
 [복제 로그 판독기 에이전트](../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [복제 병합 에이전트](../relational-databases/replication/agents/replication-merge-agent.md)   
 [복제 큐 판독기 에이전트](../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  
