---
title: 유틸리티 탐색기를 사용하여 SQL Server 유틸리티 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 74012c90-b42e-4171-b27a-9c30cf69ff98
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 031efcdc80028e8366a2e19827f180b78a21af0a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124033"
---
# <a name="use-utility-explorer-to-manage-the-sql-server-utility"></a>유틸리티 탐색기를 사용하여 SQL Server 유틸리티 관리
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 구성 요소인 유틸리티 탐색기는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티의 모든 개체를 트리 방식으로 표시합니다. 유틸리티 탐색기 내용 창에서는 다양한 방법을 사용하여 SQL Server의 관리되는 인스턴스 상태에 대한 요약 및 자세한 데이터를 통해 볼 수 있습니다. 또한 유틸리티 탐색기는 정책 정의를 보고 관리하기 위한 사용자 인터페이스를 제공합니다. 유틸리티 탐색기의 기능은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에 있는 개체에 따라 조금씩 다르지만 일반적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 관리되는 개체, 데이터 및 정책을 포함합니다. 자세한 내용은 [SQL Server 유틸리티 기능 및 태스크](sql-server-utility-features-and-tasks.md)를 참조하세요.  
  
## <a name="create-utility-control-point"></a>유틸리티 제어 지점 만들기  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티를 사용하려면 먼저 유틸리티 제어 지점을 만들어야 합니다. 자세한 내용은 [SQL Server 유틸리티 기능 및 태스크](sql-server-utility-features-and-tasks.md) 또는 [SQL Server 유틸리티 제어 지점 만들기&#40;SQL Server 유틸리티&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md)를 참조하세요.  
  
## <a name="enroll-an-instance-of-sql-server-or-a-data-tier-application-from-utility-explorer"></a>Utility Explorer에서 SQL Server 인스턴스 또는 데이터 계층 응용 프로그램 등록  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 손쉽게 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 등록할 수 있습니다. 유틸리티 탐색기에서 **관리되는 인스턴스** 노드를 마우스 오른쪽 단추로 클릭하고 **관리되는 인스턴스 추가**를 클릭합니다. 마법사의 단계에 따라 과정을 완료합니다. 자세한 내용은 [SQL Server 인스턴스 등록&#40;SQL Server 유틸리티&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md)를 참조하세요.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 데이터 계층 응용 프로그램을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 관리되는 인스턴스로 배포하려면 **개체 탐색기** 탭을 클릭하고 **관리** 노드를 확장한 다음 **데이터 계층 응용 프로그램**을 마우스 오른쪽 단추로 클릭합니다. 오른쪽 클릭 메뉴에서 **데이터 계층 응용 프로그램 배포**를 선택합니다. 자세한 내용은 [데이터 계층 응용 프로그램 배포](../data-tier-applications/deploy-a-data-tier-application.md)를 참조하세요.  
  
## <a name="viewing-utility-explorer"></a>유틸리티 탐색기 보기  
 유틸리티 탐색기는 기본적으로 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에 표시되지 않습니다. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 사용자 인터페이스에 유틸리티 탐색기가 표시되지 않는 경우 **보기** 메뉴에서 **유틸리티 탐색기**를 클릭합니다. 유틸리티 탐색기 내용 창을 보려면 **보기** 메뉴에서 **유틸리티 탐색기 내용**을 클릭합니다.  
  
## <a name="viewing-objects-in-utility-explorer"></a>유틸리티 탐색기에서 개체 보기  
 유틸리티 탐색기 탐색 창과 유틸리티 탐색기 내용 창에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 관리되는 데이터, 개체 및 정책이 표시됩니다. 탐색 창을 사용하여 대시보드와 뷰 지점에 표시되는 정보를 지정한 다음 내용 창과 자세히 탭을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 관리되는 개체에 대한 데이터와 정책 정보에 액세스할 수 있습니다.  
  
### <a name="sql-server-utility-navigation-pane"></a>SQL Server 유틸리티 탐색 창  
 유틸리티 탐색기 탐색 창에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티의 개체를 유틸리티 제어 지점별로 그룹화하여 트리 뷰로 제공합니다. 폴더를 확장하려면 유틸리티 탐색기 탐색 창에서 더하기 기호(+)를 클릭하거나 UCP 이름을 두 번 클릭합니다. 일반적인 태스크를 수행하려면 폴더나 개체를 마우스 오른쪽 단추로 클릭하고, 트리 뷰의 노드는 다음과 같습니다.  
  
-   트리 뷰의 최상위 노드는 UCP(유틸리티 제어 지점)입니다. 노드 이름은 "Utility_Name" (ComputerName\UCP_instance_name) 형식으로 구성됩니다. UCP가 없는 경우 만들어야 합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에 연결하지 않은 경우 연결해야 합니다. 자세한 내용은 [SQL Server 유틸리티 기능 및 태스크](sql-server-utility-features-and-tasks.md)를 참조하세요. 대시 보드에 있는 데이터로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 탐색기 내용 창을 채우려면 트리 뷰의 UCP 이름을 클릭합니다. 자세한 내용은 [유틸리티 대시보드&#40;SQL Server 유틸리티&#41;](../../database-engine/utility-dashboard-sql-server-utility.md)를 참조하세요.  
  
     대시보드의 데이터를 새로 고치려면 UCP 노드를 마우스 오른쪽 단추로 클릭합니다.  
  
-   **유틸리티 내용 창의 목록 뷰 데이터에 액세스하려면 트리 뷰에서** 배포된 데이터 계층 응용 프로그램 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 노드를 클릭합니다. 내용 창 아래에 있는 자세히 탭에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티의 개별 데이터 계층 응용 프로그램의 정책 정의와 속성 정보는 물론 CPU와 저장소 사용에 대한 데이터가 표시됩니다. 자세한 내용은 [배포된 데이터 계층 응용 프로그램 세부 정보&#40;SQL Server 유틸리티&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md)를 참조하세요.  
  
     필터 설정에 액세스하거나 목록 뷰의 데이터를 새로 고치려면 트리 뷰에서 **배포된 데이터 계층 응용 프로그램** 노드를 마우스 오른쪽 단추로 클릭합니다.  
  
-   ph x="1" /&gt; 유틸리티 내용 창의 목록 뷰 데이터에 액세스하려면 트리 뷰에서 **관리되는 인스턴스[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 노드를 클릭합니다. 내용 창 아래에 있는 자세히 탭에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티의 개별 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스 정책 정의와 속성 정보는 물론 CPU와 저장소 볼륨 사용에 대한 데이터를 제공합니다. 자세한 내용은 [관리되는 인스턴스 세부 정보&amp;#40;SQL Server 유틸리티&amp;#41;](../../database-engine/managed-instance-details-sql-server-utility.md)를 참조하세요.  
  
     필터 설정에 액세스하거나 목록 뷰의 데이터를 새로 고치려면 트리 뷰에서 **관리되는 인스턴스** 노드를 마우스 오른쪽 단추로 클릭하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 관리되는 인스턴스를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에 추가합니다.  
  
-   **유틸리티의 모든** 의 관리되는 인스턴스와 배포한 데이터 계층 응용 프로그램의 글로벌 정책 정의에 액세스하고, UCP 관리자 정보를 보고, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 관리 데이터 웨어하우스의 구성 설정에 액세스하려면 트리 뷰에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]유틸리티 관리[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 노드를 클릭합니다. 자세한 내용은 [유틸리티 관리&#40;SQL Server 유틸리티&#41;](../../database-engine/utility-administration-sql-server-utility.md)를 참조하세요. **정책** 탭의 컨트롤을 사용하여 정책 위반 보고의 민감도를 변경할 수도 있습니다. 자세한 내용은 [CPU 사용 정책에서 노이즈 줄이기&#40;SQL Server 유틸리티&#41;](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)를 참조하세요.  
  
     내용 창의 데이터를 새로 고치려면 트리 뷰에서 **유틸리티 관리** 노드를 마우스 오른쪽 단추로 클릭합니다.  
  
### <a name="sql-server-utility-dashboard"></a>SQL Server 유틸리티 대시보드  
 유틸리티 탐색기 트리 뷰에서 UCP 노드를 선택하면 유틸리티 탐색기 내용 창의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 대시보드가 채워집니다. 대시보드는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티의 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스와 데이터 계층 응용 프로그램의 상태에 대한 알아보기 쉬운 요약과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 관리되는 개체의 전반적인 저장소 사용을 보여 줍니다. 자세한 내용은 [유틸리티 대시보드&#40;SQL Server 유틸리티&#41;](../../database-engine/utility-dashboard-sql-server-utility.md)를 참조하세요. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 등록 또는 제거하려면 [SQL Server 인스턴스 등록&#40;SQL Server 유틸리티&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md) 또는 [데이터 계층 응용 프로그램 배포](../data-tier-applications/deploy-a-data-tier-application.md) 또는 [SQL Server 유틸리티에서 SQL Server 인스턴스 제거](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)를 참조하세요.  
  
### <a name="filtering-the-list-of-objects-in-utility-explorer-contents"></a>유틸리티 탐색기 내용에서 개체 목록 필터링  
 노드에 개체가 많이 있으면 개체를 찾는 것이 어려울 수 있습니다. 이러한 경우에는 유틸리티 탐색기의 필터 기능을 사용하여 목록의 크기를 줄일 수 있습니다. 예를 들어 특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스나 사용 미달 파일 공간이 있는 컴퓨터만 찾으려고 할 수 있습니다. 이러한 경우에는 필터링할 폴더를 마우스 오른쪽 단추로 클릭하고 필터 단추를 클릭한 다음 **필터 설정** 을 클릭하여 유틸리티 탐색기 필터 설정 대화 상자를 엽니다. 이름, 컴퓨터 CPU, 인스턴스 CPU, 파일 공간, 볼륨 공간, 정책 재정의 설정 또는 마지막 보고 시간별로 목록을 필터링할 수 있습니다. **연산자** 및 **값** 열의 드롭다운 목록에는 추가 필터링 연산자가 제공됩니다.  
  
### <a name="starting-powershell"></a>PowerShell 시작  
 개체 탐색기 트리에서 대부분의 폴더 및 개체를 마우스 오른쪽 단추로 클릭하고 **Powershell 시작**을 선택하면 PowerShell 세션을 시작할 수 있습니다. 이렇게 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell 지원이 활성화되고 개체 탐색기에서 마우스 오른쪽 단추로 클릭한 개체로 경로가 설정되어 Powershell 세션이 시작됩니다. 이제 대화형 Powershell 환경에서 Powershell 명령을 입력할 수 있습니다. 자세한 내용은 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)을 참조하세요.  
  
 Powershell에는 F1 도움말이 없지만 Powershell 사용에 대한 정보를 제공하는 **Get-Help** cmdlet이 포함되어 있습니다. Get-Help를 사용하는 방법은 [SQL Server PowerShell 도움말 보기](../../database-engine/get-help-sql-server-powershell.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server 유틸리티 기능 및 태스크](sql-server-utility-features-and-tasks.md)   
 [상태 정책 구성&#40;SQL Server 유틸리티&#41;](configure-health-policies-sql-server-utility.md)   
 [개체 탐색기](../../ssms/object/object-explorer.md)  
  
  
