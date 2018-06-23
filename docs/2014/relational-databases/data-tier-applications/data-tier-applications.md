---
title: 데이터 계층 응용 프로그램 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-data-tier-apps
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- designing DACs
- How to [DAC]
- data-tier application [SQL Server], designing
- wizard [DAC]
ms.assetid: a04a2aba-d07a-4423-ab8a-0a31658f6317
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c3fb074e97422942dfe9cac25a84c47ff65bac9e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36091303"
---
# <a name="data-tier-applications"></a>의
  DAC(데이터 계층 응용 프로그램)는 사용자의 데이터베이스와 연결된 로그인을 포함하여 테이블, 뷰 및 인스턴스 개체와 같은 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체를 정의하는 논리적인 데이터베이스 관리 엔터티입니다. DAC는 데이터 계층 개발자 및 데이터베이스 관리자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체를 DAC 패키지(또는 DACPAC)라고 부르는 이식 가능한 아티팩트로 패키징할 수 있게 해주는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 자체 포함 배포 단위입니다.  
  
 BACPAC는 데이터베이스에 저장된 데이터뿐만 아니라 데이터베이스 스키마를 캡슐화하는 관련 아티팩트입니다.  
  
## <a name="benefits-of-data-tier-applications"></a>데이터 계층 응용 프로그램의 이점  
 대부분의 데이터베이스 응용 프로그램 수명 주기에는 응용 프로그램 업데이트 및 유지 관리 활동을 위해 개발자 및 DBA의 스크립트 공유 및 교환과 임시 통합 정보가 포함됩니다. 이러한 방식은 데이터베이스 수가 많지 않은 경우에 허용 가능하지만 데이터베이스 수와 크기 및 복잡도가 증가할수록 확장성이 크게 떨어집니다.  
  
 DAC는 선언적인 데이터베이스 개발을 통해 배포 및 관리를 간소화할 수 있게 해주는 데이터베이스 수명 주기 관리 및 생산성 도구입니다. 개발자는 SQL Server Data Tools 데이터베이스 프로젝트에서 데이터베이스를 작성한 후 DBA에게 전달하기 위해 데이터베이스를 DACPAC로 작성할 수 있습니다. DBA는 SQL Server Management Studio를 사용하여 DAC를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 테스트 또는 프로덕션 인스턴스나 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]에 배포할 수 있습니다. 또는 DBA가 이전에 SQL Server Management Studio를 사용하여 배포된 데이터베이스를 DACPAC를 통해 업그레이드할 수 있습니다. DBA는 테스트 또는 프로덕션 조정을 반영하거나 응용 프로그램 내 변경 사항에 따라 데이터베이스 설계를 추가로 변경할 수 있도록 데이터베이스를 DACPAC로 추출하고 이를 개발자에게 전달함으로써 수명 주기를 완료합니다.  
  
 스크립트 기반 배포 대신 DAC 기반 배포를 사용할 경우의 이점은 DBA가 이 도구를 통해 다양한 원본 및 대상 데이터베이스의 동작을 식별하고 유효성을 검사할 수 있다는 점입니다. 업그레이드 중에 데이터 손실이 발생할 수 있는 경우 이 도구를 통해 DBA에게 경고가 표시되고 업그레이드 계획도 제공됩니다. DBA는 계획을 평가하고 도구를 활용하여 업그레이드를 계속 진행할 수 있습니다.  
  
 DAC는 또한 개발자와 DBA가 해당 수명 주기 전체에 걸쳐 데이터베이스 계보를 유지 관리할 수 있도록 버전 관리 기능을 지원합니다.  
  
## <a name="dac-concepts"></a>DAC 개념  
 DAC를 사용하면 응용 프로그램을 지원하는 데이터 계층 요소를 간편하게 개발, 배포 및 관리할 수 있습니다.  
  
-   DAC(데이터 계층 응용 프로그램)는 테이블, 뷰 및 인스턴스 개체와 같은 사용자의 데이터베이스와 연결된 모든 SQL Server 개체를 정의하는 논리적인 데이터베이스 관리 엔터티입니다. DAC는 데이터 계층 개발자 및 DBA가 SQL Server 개체를 DAC 패키지(또는 .dacpac 파일)라고 부르는 이식 가능한 아티팩트로 패키징할 수 있게 해주는 SQL Server 데이터베이스의 자체 포함 배포 단위입니다.  
  
-   SQL Server 데이터베이스가 DAC로 처리되도록 하려면 사용자 작업을 통해 명시적으로 또는 DAC 작업 중 하나를 통해 암시적으로 등록되어 있어야 합니다. 데이터베이스가 등록되면 DAC 버전 및 기타 속성이 데이터베이스의 메타데이터로 기록됩니다. 반대로, 데이터베이스의 등록을 취소하면 DAC 속성을 제거할 수 있습니다.  
  
-   일반적으로 DAC 도구는 이전 SQL Server 버전의 DAC 도구로 생성된 DACPAC 파일을 읽을 수 있으며, DACPAC를 이전 SQL Server 버전에 배포할 수도 있습니다. 그러나 이전 버전의 DAC 도구로는 이후 버전의 DAC 도구로 생성된 DACPAC 파일을 읽을 수 없습니다. 특히 다음에 대한 내용을 설명합니다.  
  
    -   DAC 작업은 SQL Server 2008 R2에 소개되었습니다. 이 도구는 SQL Server 2008 R2 데이터베이스 외에도 SQL Server 2008, SQL Server 2005 및 SQL Server 2000 데이터베이스에서 DACPAC 파일을 생성할 수 있도록 지원합니다.  
  
    -   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 에 제공되는 도구는 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 데이터베이스 외에도 SQL Server 2008 R2 또는 SQL Server 2012에 제공된 DAC 도구로 생성된 DACPAC 파일을 읽을 수 있습니다. 여기에는 SQL Server 2012, SQL Server 2008 R2, SQL Server 2008 및 SQL Server 2005의 데이터베이스가 포함되지만 SQL Server 2000은 포함되지 않습니다.  
  
    -   SQL Server 2008 R2의 DAC 도구는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 또는  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 도구로 생성된 DACPAC 파일을 읽을 수 없습니다.  
  
-   DACPAC는 확장명이 .dacpac인 Windows 파일입니다. 이 파일은 DACPAC 원본의 세부 사항을 나타내는 여러 XML 섹션, 데이터베이스의 개체 및 기타 특성으로 구성되는 개방형 형식을 지원합니다. 고급 사용자는 제품에 포함된 DacUnpack.exe 유틸리티를 사용하여 파일의 압축을 풀고 각 섹션을 보다 자세히 검사할 수 있습니다.  
  
-   DAC 패키지를 배포하여 데이터베이스를 만드는 작업을 포함하여 데이터베이스를 만들기 위해서는 사용자가 dbmanager 역할의 멤버이거나 사용자에게 CREATE DATABASE 권한이 할당되어 있어야 합니다. 데이터베이스를 삭제하기 위해서는 사용자가 dbmanager 역할의 멤버이거나 사용자에게 DROP DATABASE 권한이 할당되어 있어야 합니다.  
  
## <a name="dac-tools"></a>DAC 도구  
 DACPAC는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에 제공되는 여러 도구 간에 쉽게 사용할 수 있습니다. 이러한 도구는 상호 운용성 단위로 DACPAC를 사용하는 여러 사용자의 요구 사항을 해결해 줍니다.  
  
-   응용 프로그램 개발자  
  
    -   데이터베이스 개발자는 SQL Server Data Tools 데이터베이스 프로젝트를 사용하여 데이터베이스를 디자인할 수 있습니다. 이 프로젝트를 성공적으로 작성할 경우 .dacpac 파일에 포함된 DACPAC가 생성됩니다.  
  
    -   또한 개발자는 DACPAC를 데이터베이스 프로젝트에 포함하고 계속해서 데이터베이스를 디자인할 수 있습니다.  
  
    -   SQL Server Data Tools는 또한 연결되지 않은 클라이언트 쪽 데이터베이스 응용 프로그램 개발을 위한 로컬 DB를 지원합니다. 개발자는 이 로컬 데이터베이스의 스냅숏을 만들어서 .dacpac 파일에 포함된 DACPAC를 만들 수 있습니다.  
  
    -   개발자는 DACPAC를 생성하지 않고도 독립적으로 데이터베이스 프로젝트를 데이터베이스에 직접 게시할 수 있습니다. 게시 작업은 다른 도구를 사용한 배포 작업과 비슷한 동작을 따릅니다.  
  
-   데이터베이스 관리자  
  
    -   DBA는 SQL Server Management Studio를 사용하여 기존 데이터베이스로부터 DACPAC를 추출하고 다른 DAC 작업도 수행할 수 있습니다.  
  
    -   또한 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 의 DBA는 DAC 작업을 위해 SQL Azure용 관리 포털을 사용할 수 있습니다.  
  
-   개별 소프트웨어 공급업체  
  
    -   호스팅 서비스 및 SQL Server의 기타 데이터 관리 제품은 DAC 작업을 위해 DACFx API를 사용할 수 있습니다.  
  
-   IT 관리자  
  
    -   IT 시스템 통합업체 및 관리자는 DAC 작업을 위해 SqlPackage.exe 명령줄 도구를 사용할 수 있습니다.  
  
## <a name="dac-operations"></a>DAC 작업  
 DAC는 다음 작업을 지원합니다.  
  
-   **추출** – 사용자가 데이터베이스를 DACPAC로 추출할 수 있습니다.  
  
-   **배포** - 사용자가 DACPAC를 호스트 서버에 배포할 수 있습니다. SQL Server Management Studio 또는 SQL Azure용 관리 포털과 같은 관리 도구에서 배포를 수행할 경우 호스트 서버의 결과 데이터베이스가 암시적으로 데이터 계층 응용 프로그램으로 등록됩니다.  
  
-   **등록** - 사용자가 데이터베이스를 데이터 계층 응용 프로그램으로 등록할 수 있습니다.  
  
-   **등록 취소** - 이전에 DAC로 등록된 데이터베이스를 등록 취소할 수 있습니다.  
  
-   **업그레이드** - DACPAC를 사용하여 데이터베이스를 업그레이드할 수 있습니다. 이전에 데이터 계층 응용 프로그램으로 등록되지 않은 데이터베이스에서도 업그레이드가 지원되지만 업그레이드할 경우 데이터베이스가 암시적으로 등록됩니다.  
  
## <a name="backup-package-bacpac"></a>백업 패키지(.bacpac)  
 BACPAC는 데이터베이스에 저장된 데이터뿐만 아니라 데이터베이스 스키마를 캡슐화하는 아티팩트입니다. BACPAC는 확장명이 .bacpac인 Windows 파일입니다. DACPAC와 비슷하게 BACPAC 파일 형식도 개방형 형식이며, BACPAC의 스키마 콘텐츠는 DACPAC의 스키마 콘텐츠와 동일합니다. 데이터는 JSON 형식으로 저장됩니다.  
  
 DACPAC와 BACPAC는 서로 비슷하지만 대상 시나리오가 서로 다릅니다. DACPAC는 기존 데이터베이스의 업그레이드를 포함하여 스키마를 캡처하고 배포하는 데 사용됩니다. DACPAC는 개발, 테스트 하 고 다음 프로덕션 환경 및 역방향에 밀접 하 게 정의 된 스키마를 배포 하는 주요 사용 사례: 프로덕션 환경의 스키마를 캡처하고 테스트 및에 다시 개발 환경에 적용 합니다.  
  
 반면에 BACPAC는 스키마와 데이터를 캡처하는 데 사용됩니다. BACPAC는 데이터베이스 백업과 논리적으로 동일하며 기존 데이터베이스를 업그레이드하는 데 사용할 수 없습니다. BACPAC의 기본 용도는 한 서버에서 다른 서버로 또는 로컬 서버에서 클라우드로 데이터베이스를 이동하고 기존 데이터베이스를 개방형 형식으로 보관하기 위한 것입니다.  
  
 BACPAC는 두 가지 주요 작업을 지원합니다.  
  
-   **내보내기**- 사용자가 데이터베이스의 스키마 및 데이터를 BACPAC로 내보낼 수 있습니다.  
  
-   **가져오기** - 사용자가 스키마 및 데이터를 호스트 서버에 있는 새 데이터베이스로 가져올 수 있습니다.  
  
 데이터베이스 관리 도구에서는 이러한 기능이 모두 지원 됩니다: Server Management Studio, SQL Azure 용 관리 포털 및 DACFx API입니다.  
  
## <a name="permissions"></a>사용 권한  
 구성원 이어야 합니다는 `dbmanager` 역할 할당 또는 `CREATE DATABASE` DAC 패키지를 배포 하 여 데이터베이스를 만들기를 비롯 한 데이터베이스를 만들 수 있는 권한이 있습니다. 구성원 이어야 합니다는 `dbmanager` 역할, 할당 된 또는 `DROP DATABASE` 권한을 데이터베이스를 삭제 하려면.  
  
## <a name="data-tier-application-tasks"></a>데이터 계층 응용 프로그램 태스크  
  
|태스크 설명|항목|  
|----------------------|-----------|  
|DAC 패키지 파일을 사용하여 새 DAC 인스턴스를 만드는 방법에 대해 설명합니다.|[데이터 계층 응용 프로그램 배포](deploy-a-data-tier-application.md)|  
|새 DAC 패키지 파일을 사용하여 인스턴스를 새 DAC 버전으로 업그레이드하는 방법에 대해 설명합니다.|[데이터 계층 응용 프로그램 업그레이드](upgrade-a-data-tier-application.md)|  
|DAC 인스턴스를 제거하는 방법에 대해 설명합니다. 연결된 데이터베이스를 선택하여 분리 또는 삭제하거나 데이터베이스를 그대로 둘 수도 있습니다.|[데이터 계층 응용 프로그램 삭제](delete-a-data-tier-application.md)|  
|SQL Server 유틸리티를 사용하여 현재 배포된 DAC의 상태를 확인하는 방법에 대해 설명합니다.|[데이터 계층 응용 프로그램 모니터링](data-tier-applications.md)|  
|DAC의 데이터 및 메타데이터 보관 파일을 포함하는 .bacpac 파일을 만드는 방법에 대해 설명합니다.|[데이터 계층 응용 프로그램 내보내기](export-a-data-tier-application.md)|  
|DAC 보관 파일(.bacpac)을 사용하여 DAC 논리 복원을 수행하거나, DAC를 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 또는 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]의 다른 인스턴스로 마이그레이션하는 방법에 대해 설명합니다.|[BACPAC 파일을 가져와 새 사용자 데이터베이스 만들기](import-a-bacpac-file-to-create-a-new-user-database.md)|  
|BACPAC 파일을 가져와서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스 내에 새 사용자 데이터베이스를 만드는 방법에 대해 설명합니다.|[데이터베이스에서 DAC 추출](extract-a-dac-from-a-database.md)|  
|기존 데이터베이스를 DAC 인스턴스로 승격하는 방법에 대해 설명합니다. DAC 정의는 작성된 후 시스템 데이터베이스에 저장됩니다.|[DAC로 데이터베이스 등록](register-a-database-as-a-dac.md)|  
|프로덕션 시스템에서 DAC 패키지를 사용하기 전에 DAC 패키지의 내용 및 DAC 업그레이드에서 수행할 동작을 검토하는 방법에 대해 설명합니다.|[DAC 패키지 유효성 검사](validate-a-dac-package.md)|  
|패키지를 프로덕션 서버에 배포하기 전에 데이터베이스 관리자가 DAC에서 수행하는 작업을 검토할 수 있도록 DAC 패키지 내용을 폴더에 넣는 방법에 대해 설명합니다.|[DAC 패키지 압축 풀기](unpack-a-dac-package.md)|  
|마법사를 사용하여 기존 데이터베이스를 배포하는 방법에 대해 설명합니다. 마법사는 DAC를 사용하여 배포를 수행합니다.|[DAC를 사용하여 데이터베이스 배포](deploy-a-database-by-using-a-dac.md)|  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server 개체 및 버전에 대한 DAC 지원](dac-support-for-sql-server-objects-and-versions.md)  
  
  