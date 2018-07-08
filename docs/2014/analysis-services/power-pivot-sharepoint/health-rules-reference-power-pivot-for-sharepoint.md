---
title: 상태 규칙 참조 (SharePoint 용 PowerPivot) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47ae04ce-7b9d-49c2-8dbc-bafcb73d4603
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2da3dbfeba6a7c0b4931286e06ef48590ce846f5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36078722"
---
# <a name="health-rules-reference-powerpivot-for-sharepoint"></a>상태 규칙 참조(SharePoint용 PowerPivot)
  이 참조 항목에서는 SharePoint용 PowerPivot  설치 시 추가되는 SharePoint  상태 규칙에 대해 설명합니다. 이러한 규칙은 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 서비스 응용 프로그램 또는 연결된 해당 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 구성,  가용성 또는 서버 상태에 대한 문제를 보고하는 데 사용됩니다.  
  
 다음 표에는 SharePoint  중앙 관리의 상태 분석기 규칙 정의 페이지에 표시되는 순서대로 규칙이 나열되어 있습니다. 구성 가능한 규칙은 규칙이 트리거되는 임계값을 변경할 수 있는 규칙입니다. 자세한 내용은 참조 [PowerPivot 상태 규칙-구성](configure-power-pivot-health-rules.md)합니다. 자동 복구는 문제 보고서 페이지 내에서 클릭하여 문제를 해결할 수 있는 기본 제공 해결 방법이 있음을 나타냅니다.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010|  
  
 **참고:** [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 에서는 다른 SharePoint 버전의 다른 상태 규칙 집합을 설치합니다. 아래 표의 "버전"  열을 참조하거나 다음 Windows  PowerShell  명령을 실행하여 설치된 규칙을 볼 수 있습니다.  
  
```  
Get-SPHealthAnalysisRule | select name, enabled, summary | where {$_.summary -like “*power*”}  | format-table -property * -autosize | out-default  
```  
  
|규칙|구성 가능|자동 복구|버전|Description|  
|----------|------------------|-----------------|-------------|-----------------|  
|PowerPivot: Analysis Services OLE DB 공급자는이 컴퓨터에 설치 되지 않았습니다.|아니요|아니요|SharePoint 2010|Analysis  Services  OLE  DB  공급자가 서버에 설치되어 있지 않거나 잘못된 버전입니다. 이 규칙은 SharePoint  팜에 SharePoint용 PowerPivot이 없는 응용 프로그램 서버의 Excel  서비스 인스턴스가 포함된 경우에 나타납니다. 이 규칙은 Excel  서비스에서 PowerPivot  데이터에 연결하는 데 사용되는 Analysis  Services  OLE  DB  공급자가 설치되어 있지 않음을 경고합니다. 이 문제를 해결하려면 Analysis  Services  OLE  DB  공급자가 설치되지 않은 각 Excel  서비스 서버에 OLE  DB  공급자를 설치합니다. Microsoft  다운로드 센터에서 Analysis  Services  OLE  DB  공급자를 다운로드하여 설치할 수 있습니다. 자세한 내용은 [SharePoint 서버에서 Analysis Services OLE DB 공급자 설치](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)를 참조하세요.|  
|PowerPivot:이 컴퓨터에서 MSOLAP 공급자의 SQL Server 2008 R2 버전을 설치한 후 Microsoft.AnalysisServices.ChannelTransport.dll에 대 한 레지스트리 설정이 유효 하지 않습니다 됩니다.|아니요|예|SharePoint 2010|서버 구성 문제입니다. ChannelTransport.dll이 전역 어셈블리에 등록되어 있지 않을 가능성이 가장 높습니다. 이 규칙에 대해 자동 복구를 실행하여 SharePoint용 PowerPivot이 설치된 각 서버에 .dll을 등록하십시오. 또는 regasm.exe를 수동으로 실행하여 파일을 등록할 수 있습니다. SharePoint  Timer  Service가 로컬 관리자로 실행되지 않는 경우 수동 등록이 필요할 수 있습니다. 레지스트리 설정을 업데이트하지 못하면 Excel  서비스와 PowerPivot  시스템 서비스 간의 서버 통신이 느려지고 특정 보안 구성에서 연결에 실패할 수 있습니다.|  
|PowerPivot: PowerPivot 서비스 응용 프로그램 게 작업을 완료할 수 있습니다.|아니요|아니요|SharePoint 2010|이 규칙은 PowerPivot  서비스 응용 프로그램 ID가 PowerPivot  서버 응용 프로그램 데이터베이스의 데이터베이스 소유자이고 로컬 SQL  Server  Analysis  Services  인스턴스에 대한 관리 권한을 가지고 있는지 여부를 확인합니다. 이러한 권한은 설치 및 배포 중에 자동으로 부여되지만 해당 단계가 완료되지 못한 경우 이 상태 규칙이 발생합니다.|  
|PowerPivot: PowerPivot 서비스 응용 프로그램 id는 로컬 관리자 그룹의 구성원을 되지 않아야 합니다.|아니요|아니요|SharePoint 2010|이는 전반적인 배포 보안을 향상시키는 최상의 방법입니다. 로컬 관리자 그룹에 속한 계정으로 실행되도록 PowerPivot  서비스 응용 프로그램을 구성한 경우 서비스 계정을 해당 그룹에 속하지 않은 계정으로 변경해야 합니다. 따라서 각 서비스에 최소 권한의 전용 계정을 사용하는 것이 좋습니다. 이렇게 하면 서비스가 격리되고 로그인 감사를 보다 쉽게 수행할 수 있습니다. 서비스 계정을 변경 하는 방법에 대 한 자세한 내용은 참조 [PowerPivot 서비스 계정 구성](configure-power-pivot-service-accounts.md)합니다.|  
|PowerPivot: Analysis Services 인스턴스가 테이블 형식 모드에서 실행 되 있지만이 모드를 지정 하는 구성 설정이 해제 됩니다.|아니요|아니요|SharePoint 2010|이 규칙은 SharePoint용 PowerPivot 설치에 있는 SQL Server Analysis Services 인스턴스의 `DeploymentMode` 서버 속성이 1로 설정되었는지 여부를 확인합니다. 속성이 다른 값으로 설정되거나 규칙 검사기를 실행하는 SharePoint Timer Service에 파일을 열 권한이 없는 경우에는 이 규칙이 실패합니다. 배포 모드 속성에 대한 자세한 내용은 [Analysis Services 인스턴스의 서버 모드 확인](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)을 참조하세요.|  
|PowerPivot: PowerPivot 데이터 새로 고침 타이머 작업은 사용할 수 없습니다.|아니요|아니요|SharePoint 2013<br /><br /> SharePoint 2010|타이머 작업이 설정되어 있는지 타이머 작업 설정을 확인합니다. PowerPivot  데이터 새로 고침 기능을 사용하지 않을 경우 이 규칙을 무시할 수 있습니다. 자세한 내용은 참조 [SharePoint 2010과 PowerPivot 데이터 새로 고침](../powerpivot-data-refresh-with-sharepoint-2010.md)합니다.|  
|PowerPivot: SQL Server 구성 관리자에서 관리 되는 SQL Server Analysis Services (PowerPivot) 서비스 계정 정보는 중앙 관리에서 관리 되는 계정 정보와 다릅니다.|아니요|아니요|SharePoint 2010|이 규칙은 SQL  Server  구성 관리자의 서비스 계정 정보가 동일한 Analysis  Services  인스턴스에 대해 중앙 관리에서 관리되는 계정 정보와 동일한지 확인합니다. 계정이 서로 다른 경우 SQL  Server  구성 관리자의 서비스 계정 정보를 중앙 관리에 지정된 계정으로 다시 변경할 수 있도록 문제 및 해결 방법 보고서에 항목이 추가됩니다. SQL  Server  구성 관리자는 SharePoint용 PowerPivot  설치에서 서비스 계정 사용자 이름 또는 암호를 변경하도록 지원되는 도구가 아닙니다. 중앙 관리를 사용하여 SharePoint에서 관리되는 계정 기능을 사용하도록 설정할 수 있습니다. 특히 팜에 SharePoint용 PowerPivot  서버가 여러 개 있는 경우 서비스 계정 설정이 일치하지 않으면 서비스 정보가 잘못된 서버에서 처리 및 쿼리 작업이 중단될 수 있습니다.<br /><br /> 단일 서버에서는 이 규칙이 트리거된 경우 PowerPivot  통합 문서가 일시적으로 작동하지만 가능한 한 신속히 문제를 해결하는 것이 좋습니다. 데이터베이스 및 파일 시스템 사용 권한은 중앙 관리에 지정된 계정 정보를 사용하여 업데이트됩니다.|  
|PowerPivot: 배포 된 팜 솔루션이 최신 상태가 아닙니다.|아니요|예|SharePoint 2010|SharePoint용 PowerPivot  설치에서는 팜 수준 솔루션 및 웹 응용 프로그램 수준 솔루션을 사용하여 해당 기능을 설치합니다. 이 규칙은 팜 솔루션이 서버 또는 웹 솔루션(해당되는 경우)  버전에 비해 최신 버전이 아님을 나타냅니다. 이는 대부분 서버 배포 문제일 수 있습니다. 이 문제를 해결하려면 SQL  Server  설치 프로그램을 실행하여 팜의 SharePoint용 PowerPivot  설치 중 하나를 복구하는 것이 좋습니다. PowerPivot for SharePoint 설치에서에서 솔루션에 대 한 자세한 내용은 참조 [SharePoint에 PowerPivot 솔루션 배포](deploy-power-pivot-solutions-to-sharepoint.md)합니다.|  
|PowerPivot: 전체 CPU 사용량이 너무 높습니다.|예|아니요|SharePoint 2010|이 규칙은 시스템 수준에서 CPU  사용량을 보고합니다. PowerPivot  시스템 서비스는 팜에 있는 여러 SharePoint용 PowerPivot  서버 간 상태 기반 부하 분산을 위해 CPU  사용량을 서버 상태의 측정값으로 사용하므로 전체 CPU  사용량이 모니터링됩니다. 다른 응용 프로그램 서버를 팜에 추가하고 CPU  사용량이 많은 응용 프로그램을 해당 서버로 이동하는 것이 좋습니다.|  
|PowerPivot: Analysis Services 없는 충분 한 CPU 리소스가 요청 된 작업을 수행 합니다.|예|아니요|SharePoint 2010|Analysis  Services  프로세스(msmdsrv.exe)에 사용할 수 있는 CPU  리소스 양이 이 서버의 작업 수준에 부족합니다. 또 다른 SharePoint용 PowerPivot  서버를 팜에 추가하는 것이 좋습니다. 자세한 내용은 참조 [배포 검사 목록: SharePoint 2010 팜에 PowerPivot 서버를 추가 하 여 스케일 아웃](../../sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)합니다.|  
|PowerPivot: Analysis Services 충분 한 메모리가 없는 요청 된 작업을 수행할 수 있습니다.|아니요|아니요|SharePoint 2010|이 규칙은 Analysis  Services에 사용할 수 있는 메모리가 5%만 남은 경우에 트리거됩니다. SharePoint  응용 프로그램 서버에서 SQL  Server  Analysis  Services  인스턴스는 항상 소량의 사용되지 않는 메모리를 가지고 있어야 합니다. 서버 작업은 대부분 메모리 집중형이기 때문에 서버는 최대 한도까지 실행되지 않을 때 최상의 성능을 발휘합니다.<br /><br /> 기본적으로 메모리 부족 경고는 사용 가능한 메모리가 5%  미만인 경우에 발생합니다. Analysis  Services  인스턴스에 대한 설정을 조정하여 이 값을 높이거나 낮출 수 있습니다. 자세한 내용은 참조 [PowerPivot 상태 규칙-구성](configure-power-pivot-health-rules.md)합니다.<br /><br /> 5%의 사용되지 않는 메모리는 Analysis  Services에 할당된 메모리의 백분율로 계산됩니다. 예를 들어 총 메모리가 200GB이고 Analysis  Services에 80%(160GB)가 할당된 경우 5%의 사용되지 않는 메모리는 160GB의 5%인 8GB입니다.|  
|PowerPivot:는 높은 연결 수가 크므로 현재 로드를 처리 하려면 더 많은 서버를 배포 해야 합니다.|예|아니요|SharePoint 2010|기본적으로 이 상태 규칙은 고유한 사용자 연결 수가 100개를 초과한 경우에 트리거됩니다. 이 기본값은 서버의 하드웨어 사양 또는 사용자 작업을 기반으로 하지 않고 임의로 지정되므로 사용자 환경의 서버 용량 및 사용자 작업에 따라 값을 높이거나 낮출 수 있습니다. 자세한 내용은 참조 [PowerPivot 상태 규칙-구성](configure-power-pivot-health-rules.md)합니다.|  
|PowerPivot: 연결에 대 한 로드 이벤트의 비율이 너무 높습니다.|예|아니요|SharePoint 2013<br /><br /> SharePoint 2010|기본적으로 이 상태 규칙은 전체 데이터 수집 기간(기본적으로 4시간)  동안 연결 이벤트에 대한 로드 이벤트의 백분율이 50%를 초과한 경우에 트리거됩니다. 이 비율이 높으면 고유 통합 문서에 대한 연결 수가 매우 많거나 캐시 감소 설정이 너무 가파름을 나타냅니다.  이 경우 해당 데이터에 대한 요청이 활성 상태인 동안 통합 문서가 빠르게 언로드되고 시스템에서 제거됩니다. 거짓 긍정을 계산하지 않으려면 비율을 계산하기 전에 4시간 동안 20개 이상의 연결이 유지되어야 합니다. 이 상태 규칙의 기준을 다른 비율로 지정할 수 있습니다. 자세한 내용은 참조 [PowerPivot 상태 규칙-구성](configure-power-pivot-health-rules.md)합니다. 캐시를 구성 하는 방법에 대 한 자세한 내용은 참조 [디스크 공간 사용 구성 &#40;PowerPivot for SharePoint&#41;](configure-disk-space-usage-power-pivot-for-sharepoint.md)합니다.|  
|PowerPivot: 하나 이상의 미니 덤프 파일이 있으며 프로그램 중단을 나타내는 Logs 디렉터리에서 찾았습니다.|아니요|아니요|SharePoint 2013<br /><br /> SharePoint 2010|프로그램 중단 시 미니덤프 파일이 생성되어 중단 바로 전의 PowerPivot  서비스 응용 프로그램 상태에 대한 정보를 캡처합니다. 이 정보는 Microsoft에 전송되어 문제를 해결하는 데 사용될 수 있습니다. 이 규칙은 서버에서 .dmp  파일이 검색된 경우에 트리거됩니다. 이 규칙은 SharePoint용 PowerPivot  인스턴스의 \OLAP\Log  폴더에서 찾을 수 있는 파일에 대한 링크를 제공합니다. 텍스트 편집기를 사용하여 파일 내용을 볼 수 없습니다. 미니덤프 파일을 보려면 별도의 디버깅 도구를 다운로드하여 설치해야 합니다. 창에 대한 자세한 내용은 [Windows용 디버깅 도구](http://go.microsoft.com/fwlink/?linkID=208266)를 참조하십시오.|  
|PowerPivot: 디스크 공간이 부족 PowerPivot 데이터가 캐시 된 드라이브에 있습니다.|예|아니요|SharePoint 2010|기본적으로 이 상태 규칙은 백업 폴더가 있는 디스크 드라이브의 디스크 공간이 5%  미만일 때 트리거됩니다. 이 백분율을 설정 하는 방법에 대 한 자세한 내용은 참조 [PowerPivot 상태 규칙-구성](configure-power-pivot-health-rules.md)합니다. 디스크 사용에 대 한 자세한 내용은 참조 [디스크 공간 사용 구성 &#40;PowerPivot for SharePoint&#41;](configure-disk-space-usage-power-pivot-for-sharepoint.md)합니다.|  
|PowerPivot: 사용 데이터가 예상 된 빈도로 업데이트 되지 않습니다.|예|아니요|SharePoint 2013<br /><br /> SharePoint 2010|SharePoint용 PowerPivot은 기본 제공 사용 데이터 컬렉션 시스템을 사용하여 연결,  데이터 새로 고침 및 쿼리 응답 시간에 대한 측정값을 수집한 다음 PowerPivot  서비스 응용 프로그램 데이터베이스에 저장합니다.  그러면 PowerPivot  관리 대시보드의 보고서에 데이터를 제공하는 PowerPivot  통합 문서(PowerPivot  Management  Data.xlsx)가 업데이트됩니다. 이 규칙은 사용 데이터가 PowerPivot  Management  Data.xlsx  파일로 충분히 자주 이동하지 않음을 나타냅니다. 이 규칙에서는 .xlsx  파일의 타임스탬프를 파일이 업데이트된 증거로 사용합니다. 사용 데이터 수집 시스템에 데이터의 정확도를 손상시키는 다른 문제가 있는 경우 이 규칙은 데이터를 검색하지 않습니다. 이 오류를 해결하려면 타이머 작업이 실행되고 있는지 확인하십시오. 사용 현황 데이터 수집에 대 한 자세한 내용은 참조 [에 대 한 사용 현황 데이터 수집 구성 &#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)합니다.|  
|PowerPivot: 중간 계층 프로세스 계정은 연결 된 모든 SPWebApplications에 ' 전체 읽기 ' 권한이 있어야 합니다.|아니요|예|SharePoint 2013<br /><br /> SharePoint 2010|PowerPivot 서비스 응용 프로그램 id 있어야 **전체 읽기** SharePoint 액세스 하려면 사용 권한을 콘텐츠 문서에 대해 보기만 권한이 있는 사용자를 대신 하 여 데이터베이스입니다. PowerPivot 서비스 응용 프로그램 id로 사용 되는 계정을 확인 하려면 열에서 **서비스 계정 구성** 중앙 관리 페이지에서에서. 서비스 응용 프로그램은 대부분 **SharePoint  웹 서비스 시스템** 서비스 응용 프로그램 풀 또는 전용 응용 프로그램 풀에서 실행됩니다. 이 규칙을 자동으로 복구 옵션을 제공 하며 다음을 수행 하 여 사용 권한을 수동으로 부여 하면 더 나은 결과 발생 합니다.<br /><br /> 1) 중앙 관리에서 **웹 응용 프로그램 관리**를 클릭합니다.<br /><br /> 2) 웹 사이트를 선택한 다음 **사용자 정책**을 클릭합니다.<br /><br /> 3) **사용자 추가**를 클릭합니다.<br /><br /> 4) (모든 영역)을 선택하고 **다음**을 클릭합니다.<br /><br /> 사용자 5)에 PowerPivot 서비스 응용 프로그램 id를 입력 한 다음 클릭는 **전체 읽기** 확인란을 선택 합니다. **마침**을 클릭합니다.<br /><br /> 6) 복구를 확인합니다. 모니터링 중에 **규칙 정의 검토**를 클릭합니다. PowerPivot  규칙을 찾은 다음 엽니다. **지금 실행**을 클릭합니다. **문제 및 솔루션 검토** 로 돌아가서 더 이상 규칙이 나타나지 않는지 확인합니다.|  
|PowerPivot: 보조 로그온 서비스 (seclogon)가 사용할 수 없습니다.|아니요|아니요|SharePoint 2013<br /><br /> SharePoint 2010|보조 로그온 서비스는 PowerPivot  갤러리에서 PowerPivot  통합 문서의 축소판 이미지를 생성하는 데 사용됩니다. 기본적으로 보조 로그온 서비스는 수동 시작으로 설정됩니다. 서비스를 사용하지 않도록 설정되어 있으면 축소판 이미지 생성에 실패합니다. 또한 ULS 로그에 다음 오류가 포함됩니다. “Windows 서비스 “보조 로그온”을 사용하지 않도록 설정되어 있기 때문에 오류 1058에 루트로 포함될 수 있습니다.”<br /><br /> 서비스 구성을 확인하려면 서비스 콘솔 응용 프로그램을 사용하여 보조 로그온을 찾고 **시작 유형** 을 **수동**으로 변경하십시오. 서비스를 사용하도록 설정할 수 없는 경우 조직에 서비스를 비활성화하는 그룹 정책이 있을 수 있습니다. 이 경우가 해당 경우인지 여부는 관리자에게 확인하십시오.<br /><br /> 서비스를 사용하도록 설정하고 나면 시간이 지남에 따라 축소판 또는 스냅숏 이미지가 새로 고쳐집니다. 필요에 따라 서비스를 다시 시작하고 연 다음 특정 보고서의 속성 페이지를 다시 저장하여 강제로 새로 고칠 수 있습니다. 자세한 내용은 참조 [PowerPivot 갤러리 사용 방법](http://go.microsoft.com/fwlink/?LinkId=246462)합니다.|  
|PowerPivot: 독립 실행형 중앙 관리를 위해 구성 된 WFE에 ADOMD.NET이 설치 되지|아니요|아니요|SharePoint 2013<br /><br /> SharePoint 2010|ADOMD.NET은 Analysis  Services  데이터베이스에 대한 연결을 지원하는 Analysis  Services  클라이언트 라이브러리입니다. SharePoint용 PowerPivot에서 ADOMD.NET에서는 중앙 관리에 있는 PowerPivot  관리 대시보드의 기본 제공 보고서에 액세스할 수 있습니다. 실제로 기본 제공 보고서는 포함된 Analysis  Services  데이터를 포함하는 PowerPivot  통합 문서입니다. 관리 대시보드는 ADOMD.NET을 사용하여 통합 문서에 포함된 데이터를 로드하는 서버에 연결 요청을 보냅니다.<br /><br /> 독립 실행형 웹 프런트 엔드 서버에서 실행되는 중앙 관리를 포함하는 토폴로지의 경우 관리 대시보드에서 이러한 보고서를 보려면 ADOMD.NET을 수동으로 설치해야 합니다. 자세한 내용은 [중앙 관리를 실행하는 웹 프런트 엔드 서버에 ADOMD.NET 설치](../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md)를 참조하세요.|  
  
  