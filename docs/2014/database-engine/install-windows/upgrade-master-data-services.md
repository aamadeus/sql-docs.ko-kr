---
title: MDS(Master Data Services) 업그레이드 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c3543f3-3eb9-455d-a9bf-f17e9506ad21
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c827edd76774e7f2204c20fa7e25d8037c834777
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36186163"
---
# <a name="upgrade-master-data-services"></a>MDS(Master Data Services) 업그레이드
  Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2로 업그레이드하는 데는 네 가지 시나리오가 있습니다. 해당 상황에 적합한 시나리오를 선택하십시오.  
  
-   [데이터베이스 엔진 업그레이드 없이 업그레이드](#noengine)  
  
-   [데이터베이스 엔진 업그레이드를 사용해서 업그레이드](#engine)  
  
-   [두 컴퓨터에서의 업그레이드 시나리오](#twocomputer)  
  
-   [백업에서 데이터베이스를 복원하여 업그레이드](#restore)  
  
> [!IMPORTANT]  
>  -   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP1 릴리스에서 CTP2 릴리스로 업그레이드할 수는 없습니다.  
> -   업그레이드를 수행하기 전에 데이터베이스를 백업합니다.  
> -   업그레이드 프로세스는 저장 프로시저를 다시 만들고 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]에서 사용되는 테이블을 업그레이드합니다. 이러한 구성 요소에 사용자 지정된 내용은 손실될 수 있습니다.  
> -   모델 배포 패키지는 해당 패키지를 만드는 데 사용한 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서만 사용할 수 있습니다. 만든 모델 배포 패키지를 배포할 수 없습니다 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] / [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]합니다.  
> -   계속 사용할 수 있습니다는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 의 Master Data Services 추가 기능을 Excel 용 Master Data Services 및 Data Quality Services를 업그레이드 한 후의 SP1 버전 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2 합니다. 하지만 SQL Server 2014 CTP2로 업그레이드한 후에는 이전 버전의 Excel용 MDS(Master Data Services) 추가 기능이 모두 작동하지 않습니다. 다운로드할 수 있습니다는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 버전의 Master Data Services 추가 기능을 for Excel에서 [여기](http://go.microsoft.com/fwlink/?LinkId=328664)합니다.  
  
##  <a name="noengine"></a> 데이터베이스 엔진 업그레이드 없이 업그레이드  
 이 시나리오 간주 될 수 있습니다-나란히 설치 되므로 둘 다 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] / [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 및 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 동일한 컴퓨터 또는 별도 컴퓨터에서 동시에 설치 됩니다.  
  
 이 시나리오에서는 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]를 계속 사용하여 MDS 데이터베이스를 호스팅합니다. 그러나 MDS 데이터베이스의 스키마를 업그레이드한 다음 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 웹 응용 프로그램을 만들어 MDS 데이터베이스에 액세스해야 합니다. MDS 데이터베이스는 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 웹 응용 프로그램에서 더 이상 액세스할 수 없습니다.  
  
 설치 하도록 선택한 경우 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 및 이전 버전의 SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]/[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) 동일한 컴퓨터에 그렇게 할 수 있습니다는 파일이 다른 위치에 설치 되어 있으므로 합니다.  
  
-   기본적으로 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 경우 파일은 *드라이브*:\Program Files\Microsoft SQL Server\120\Master Data Services에 설치됩니다.  
  
-   기본적으로 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]의 경우 파일은 *드라이브*:\Program Files\Microsoft SQL Server\110\Master Data Services에 설치됩니다.  
  
-   기본적으로 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]의 경우 파일은 *드라이브*:\Program Files\Microsoft SQL Server\Master Data Services에 설치됩니다.  
  
 이 태스크를 수행하려면 다음 단계를 완료합니다.  
  
1.  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 및 원하는 다른 기능을 설치합니다.  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 마법사를 엽니다.  
  
    2.  왼쪽 창에서 **설치**를 클릭합니다.  
  
    3.  오른쪽 창에서 **새 SQL Server 독립 실행형 설치 또는 기존 설치에 기능 추가**를 클릭합니다.  
  
    4.  **기능 선택** 페이지에서 **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** 및 설치할 다른 기능을 선택합니다.  
  
    5.  마법사를 완료합니다.  
  
2.  설치가 완료되면 MDS 데이터베이스 스키마를 업그레이드합니다.  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]를 엽니다.  
  
        > [!IMPORTANT]  
        >  MDS 데이터베이스 스키마를 업그레이드하려면 MDS 데이터베이스를 만들 때 지정한 관리자 계정으로 로그인해야 합니다. MDS 데이터베이스의 mdm.tblUser에서 이 사용자의 **ID** 값은 **1**입니다. 이 사용자를 변경 하는 방법에 대 한 정보를 참조 하십시오. [시스템 관리자 계정 변경 &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md)합니다.  
  
    2.  왼쪽 창에서 **데이터베이스 구성**을 클릭합니다.  
  
    3.  오른쪽 창에서 클릭 **데이터베이스 선택** 에 대 한 정보를 지정 하면 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 데이터베이스 인스턴스.  
  
    4.  **데이터베이스 업그레이드** 를 클릭하여 **데이터베이스 업그레이드 마법사**를 시작합니다. 자세한 내용은 [데이터베이스 업그레이드 마법사&#40;Master Data Services 구성 관리자&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md)를 참조하세요.  
  
3.  업그레이드가 완료되면 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 웹 응용 프로그램을 만듭니다.  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]를 엽니다.  
  
    2.  왼쪽 창에서 **웹 구성**을 클릭합니다.  
  
    3.  오른쪽 창의 **웹 사이트** 목록에서 다음 옵션 중 하나를 선택합니다.  
  
        -   **기본 웹 사이트**를 선택하고 **응용 프로그램 만들기**를 클릭합니다.  
  
        -   **새 사이트 만들기**를 선택합니다. 새 웹 사이트를 만들면 새 웹 응용 프로그램이 자동으로 만들어집니다.  
  
        > [!IMPORTANT]  
        >  이전 버전의 SQL Server([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)])에 있는 기존 MDS 웹 응용 프로그램을 SQL Server 2014 버전의 Master Data Services 구성 관리자에서 선택할 수 있습니다. 기존 웹 응용 프로그램을 선택하는 대신 MDS용 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 웹 응용 프로그램을 만들어야 합니다. 이렇게 하지 않으면 웹 응용 프로그램을 업그레이드된 MDS 데이터베이스와 연결하려고 할 때 요청된 페이지의 관련 구성 데이터가 잘못되었기 때문에 해당 페이지에 액세스할 수 없다는 오류 메시지가 나타납니다.  
        >   
        >  MDS 웹 응용 프로그램에 기존([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) 웹 응용 프로그램과 동일한 이름(별칭)을 사용하려면 먼저 웹 응용 프로그램과 관련 응용 프로그램 풀을 IIS에서 삭제한 다음 SQL Server 2014 버전의 Master Data Services 구성 관리자를 사용하여 동일한 이름의 웹 응용 프로그램을 만들어야 합니다. 웹 응용 프로그램과 응용 프로그램 풀을 IIS에서 제거하는 방법은 [응용 프로그램 제거(IIS)](http://go.microsoft.com/fwlink/?LinkId=323537) 및 [응용 프로그램 풀 제거(IIS)](http://go.microsoft.com/fwlink/?LinkId=323538)를 참조하세요.  
  
4.  이제 새 웹 응용 프로그램을 업그레이드된 MDS 데이터베이스와 연결합니다.  
  
    1.  **응용 프로그램을 데이터베이스에 연결** 섹션에서 **선택**을 클릭합니다.  
  
    2.  MDS 데이터베이스를 선택합니다.  
  
    3.  **적용**을 클릭합니다.  
  
##  <a name="engine"></a> 데이터베이스 엔진 업그레이드를 사용해서 업그레이드  
 이 시나리오에서는 데이터베이스 엔진과 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 응용 프로그램을 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 SQL Server 2012에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 모두 업그레이드합니다.  
  
 이 태스크를 수행하려면 다음 단계를 완료합니다.  
  
1.  **[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]의 경우에만**: **제어판** > **프로그램 및 기능**을 열고 Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]를 제거합니다.  
  
2.  데이터베이스 엔진을 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드합니다.  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 마법사를 엽니다.  
  
    2.  왼쪽 창에서 **설치**를 클릭합니다.  
  
    3.  오른쪽 창에서 클릭 **SQL Server 2005, SQL Server 2008, SQL Server 2008 R2 또는 SQL Server 2012에서 업그레이드**합니다.  
  
    4.  마법사를 완료합니다.  
  
3.  **에 대 한 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 만**: 업그레이드가 완료 되 면 추가 **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** 기능입니다.  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 마법사를 엽니다.  
  
    2.  왼쪽 창에서 **설치**를 클릭합니다.  
  
    3.  오른쪽 창에서 **새 SQL Server 독립 실행형 설치 또는 기존 설치에 기능 추가**를 클릭합니다.  
  
    4.  에 **설치 유형을** 선택 마법사의 페이지는 **기존 인스턴스에 기능 추가** 옵션을 MDS 데이터베이스가 설치 된 인스턴스를 선택 합니다.  
  
    5.  에 **기능 선택** 페이지의 **공유 기능**선택, **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** 합니다.  
  
    6.  마법사를 완료합니다.  
  
4.  MDS 데이터베이스 스키마를 업그레이드합니다.  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]를 엽니다.  
  
        > [!IMPORTANT]  
        >  MDS 데이터베이스 스키마를 업그레이드하려면 MDS 데이터베이스를 만들 때 지정한 관리자 계정으로 로그인해야 합니다. MDS 데이터베이스의 mdm.tblUser에서 이 사용자의 **ID** 값은 **1**입니다. 이 사용자를 변경 하는 방법에 대 한 정보를 참조 하십시오. [시스템 관리자 계정 변경 &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md)합니다.  
  
    2.  왼쪽 창에서 **데이터베이스 구성**을 클릭합니다.  
  
    3.  오른쪽 창에서 클릭 **데이터베이스 선택** 데이터베이스 인스턴스에 대 한 정보를 지정 합니다.  
  
    4.  **데이터베이스 업그레이드** 를 클릭하여 **데이터베이스 업그레이드 마법사**를 시작합니다. 자세한 내용은 [데이터베이스 업그레이드 마법사&#40;Master Data Services 구성 관리자&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md)를 참조하세요.  
  
    5.  **적용**을 클릭합니다.  
  
5.  업그레이드가 완료되면 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 웹 응용 프로그램을 만듭니다.  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]를 엽니다.  
  
    2.  왼쪽 창에서 **웹 구성**을 클릭합니다.  
  
    3.  오른쪽 창의 **웹 사이트** 목록에서 다음 옵션 중 하나를 선택합니다.  
  
        -   **기본 웹 사이트**를 선택하고 **응용 프로그램 만들기**를 클릭합니다.  
  
        -   **새 사이트 만들기**를 선택합니다. 새 웹 사이트를 만들면 새 웹 응용 프로그램이 자동으로 만들어집니다.  
  
        > [!IMPORTANT]  
        >  이전 버전의 SQL Server([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)])에 있는 기존 MDS 웹 응용 프로그램을 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 Master Data Services 구성 관리자에서 선택할 수 있습니다. 기존 웹 응용 프로그램을 선택하는 대신 MDS용 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 웹 응용 프로그램을 만들어야 합니다. 이렇게 하지 않으면 웹 응용 프로그램을 업그레이드된 MDS 데이터베이스와 연결하려고 할 때 요청된 페이지의 관련 구성 데이터가 잘못되었기 때문에 해당 페이지에 액세스할 수 없다는 오류 메시지가 나타납니다.  
        >   
        >  MDS 웹 응용 프로그램에 기존([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) 웹 응용 프로그램과 동일한 이름(별칭)을 사용하려면 먼저 웹 응용 프로그램과 관련 응용 프로그램 풀을 IIS에서 삭제한 다음 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 Master Data Services 구성 관리자를 사용하여 동일한 이름의 웹 응용 프로그램을 만들어야 합니다. 웹 응용 프로그램과 응용 프로그램 풀을 IIS에서 제거하는 방법은 [응용 프로그램 제거(IIS)](http://go.microsoft.com/fwlink/?LinkId=323537) 및 [응용 프로그램 풀 제거(IIS)](http://go.microsoft.com/fwlink/?LinkId=323538)를 참조하세요.  
  
6.  이제 새 웹 응용 프로그램을 업그레이드된 MDS 데이터베이스와 연결합니다.  
  
    1.  **응용 프로그램을 데이터베이스에 연결** 섹션에서 **선택**을 클릭합니다.  
  
    2.  MDS 데이터베이스를 선택합니다.  
  
    3.  **적용**을 클릭합니다.  
  
##  <a name="twocomputer"></a> 두 컴퓨터에서의 업그레이드 시나리오  
 이 시나리오에서는 두 대의 컴퓨터에 SQL Server를 설치 하는 시스템 업그레이드: 한 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]와 SQL Server 2008 R2 또는 SQL Server 2012를 사용 합니다.  
  
 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]가 설치된 경우 계속 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]를 각각 사용하여 한 컴퓨터에서 MDS 데이터베이스를 호스팅합니다. 그러나 MDS 데이터베이스의 스키마를 업그레이드한 다음 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 웹 응용 프로그램을 사용하여 MDS 데이터베이스에 액세스해야 합니다. MDS 데이터베이스는 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 웹 응용 프로그램에서 더 이상 액세스할 수 없습니다.  
  
-   기본적으로 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 경우 파일은 *드라이브*:\Program Files\Microsoft SQL Server\120\Master Data Services에 설치됩니다.  
  
-   기본적으로 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]의 경우 파일은 *드라이브*:\Program Files\Microsoft SQL Server\110\Master Data Services에 설치됩니다.  
  
-   기본적으로 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]의 경우 파일은 *드라이브*:\Program Files\Microsoft SQL Server\Master Data Services에 설치됩니다.  
  
 이 태스크를 수행하려면 다음 단계를 완료합니다.  
  
1.  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 및 원하는 다른 기능을 설치합니다.  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 마법사를 엽니다.  
  
    2.  왼쪽 창에서 **설치**를 클릭합니다.  
  
    3.  오른쪽 창에서 **새 SQL Server 독립 실행형 설치 또는 기존 설치에 기능 추가**를 클릭합니다.  
  
    4.  **기능 선택** 페이지에서 **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** 및 설치할 다른 기능을 선택합니다.  
  
    5.  마법사를 완료합니다.  
  
2.  설치가 완료되면 MDS 데이터베이스 스키마를 업그레이드합니다.  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]를 엽니다.  
  
        > [!IMPORTANT]  
        >  MDS 데이터베이스 스키마를 업그레이드하려면 MDS 데이터베이스를 만들 때 지정한 관리자 계정으로 로그인해야 합니다. MDS 데이터베이스의 mdm.tblUser에서 이 사용자의 **ID** 값은 **1**입니다. 이 사용자를 변경 하는 방법에 대 한 정보를 참조 하십시오. [시스템 관리자 계정 변경 &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md)합니다.  
  
    2.  왼쪽 창에서 **데이터베이스 구성**을 클릭합니다.  
  
    3.  오른쪽 창에서 클릭 **데이터베이스 선택** 에 대 한 정보를 지정 하 고 프로그램 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 경우 다른 컴퓨터의 인스턴스에 데이터베이스 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 다른 컴퓨터에 설치 합니다.  
  
    4.  **데이터베이스 업그레이드** 를 클릭하여 **데이터베이스 업그레이드 마법사**를 시작합니다. 자세한 내용은 [데이터베이스 업그레이드 마법사&#40;Master Data Services 구성 관리자&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md)를 참조하세요.  
  
3.  업그레이드가 완료되면 SQL Server 2014 웹 응용 프로그램을 만듭니다.  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]를 엽니다.  
  
    2.  왼쪽 창에서 **웹 구성**을 클릭합니다.  
  
    3.  오른쪽 창의 **웹 사이트** 목록에서 다음 옵션 중 하나를 선택합니다.  
  
        -   **기본 웹 사이트**를 선택하고 **응용 프로그램 만들기**를 클릭합니다.  
  
        -   **새 사이트 만들기**를 선택합니다. 새 웹 사이트를 만들면 새 웹 응용 프로그램이 자동으로 만들어집니다.  
  
        > [!IMPORTANT]  
        >  이전 버전의 SQL Server([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)])에 있는 기존 MDS 웹 응용 프로그램을 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 Master Data Services 구성 관리자에서 선택할 수 있습니다. 기존 웹 응용 프로그램을 선택하는 대신 MDS용 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 웹 응용 프로그램을 만들어야 합니다. 이렇게 하지 않으면 웹 응용 프로그램을 업그레이드된 MDS 데이터베이스와 연결하려고 할 때 요청된 페이지의 관련 구성 데이터가 잘못되었기 때문에 해당 페이지에 액세스할 수 없다는 오류 메시지가 나타납니다.  
        >   
        >  MDS 웹 응용 프로그램에 기존([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) 웹 응용 프로그램과 동일한 이름(별칭)을 사용하려면 먼저 웹 응용 프로그램과 관련 응용 프로그램 풀을 IIS에서 삭제한 다음 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 Master Data Services 구성 관리자를 사용하여 동일한 이름의 웹 응용 프로그램을 만들어야 합니다. 웹 응용 프로그램과 응용 프로그램 풀을 IIS에서 제거하는 방법은 [응용 프로그램 제거(IIS)](http://go.microsoft.com/fwlink/?LinkId=323537) 및 [응용 프로그램 풀 제거(IIS)](http://go.microsoft.com/fwlink/?LinkId=323538)를 참조하세요.  
  
4.  이제 웹 응용 프로그램을 업그레이드된 MDS 데이터베이스와 연결합니다.  
  
    1.  **응용 프로그램을 데이터베이스에 연결** 섹션에서 **선택**을 클릭합니다.  
  
    2.  MDS 데이터베이스를 선택합니다.  
  
    3.  **적용**을 클릭합니다.  
  
##  <a name="restore"></a> 백업에서 데이터베이스를 복원하여 업그레이드  
 이 시나리오에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]가 SQL Server 2008 R2 또는 SQL Server 2012와 함께 컴퓨터 한 대나 두 대에 설치되어 있습니다. 또한 업그레이드하기 전에 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2 릴리스보다 이전 버전에서 데이터베이스가 백업되었으며 이 데이터베이스가 복원되어야 합니다.  
  
-   기본적으로 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 경우 파일은 *드라이브*:\Program Files\Microsoft SQL Server\120\Master Data Services에 설치됩니다.  
  
-   기본적으로 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]의 경우 파일은 *드라이브*:\Program Files\Microsoft SQL Server\110\Master Data Services에 설치됩니다.  
  
-   기본적으로 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]의 경우 파일은 *드라이브*:\Program Files\Microsoft SQL Server\Master Data Services에 설치됩니다.  
  
 이 태스크를 수행하려면 다음 단계를 완료합니다.  
  
1.  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 및 원하는 다른 기능을 설치합니다.  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 마법사를 엽니다.  
  
    2.  왼쪽 창에서 **설치**를 클릭합니다.  
  
    3.  오른쪽 창에서 **새 SQL Server 독립 실행형 설치 또는 기존 설치에 기능 추가**를 클릭합니다.  
  
    4.  **기능 선택** 페이지에서 **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** 및 설치할 다른 기능을 선택합니다.  
  
    5.  마법사를 완료합니다.  
  
2.  백업한 데이터베이스를 복원합니다.  
  
3.  설치가 완료되면 MDS 데이터베이스 스키마를 업그레이드합니다.  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]를 엽니다.  
  
        > [!IMPORTANT]  
        >  MDS 데이터베이스 스키마를 업그레이드하려면 MDS 데이터베이스를 만들 때 지정한 관리자 계정으로 로그인해야 합니다. MDS 데이터베이스의 mdm.tblUser에서 이 사용자의 **ID** 값은 **1**입니다. 이 사용자를 변경 하는 방법에 대 한 정보를 참조 하십시오. [시스템 관리자 계정 변경 &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md)합니다.  
  
    2.  왼쪽 창에서 **데이터베이스 구성**을 클릭합니다.  
  
    3.  오른쪽 창에서 클릭 **데이터베이스 선택** 에 대 한 정보를 지정 하면 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 데이터베이스 인스턴스.  
  
    4.  **데이터베이스 업그레이드** 를 클릭하여 **데이터베이스 업그레이드 마법사**를 시작합니다. 자세한 내용은 [데이터베이스 업그레이드 마법사&#40;Master Data Services 구성 관리자&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md)를 참조하세요.  
  
4.  업그레이드가 완료되면 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 웹 응용 프로그램을 만듭니다.  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]를 엽니다.  
  
    2.  왼쪽 창에서 **웹 구성**을 클릭합니다.  
  
    3.  오른쪽 창의 **웹 사이트** 목록에서 다음 옵션 중 하나를 선택합니다.  
  
        -   **기본 웹 사이트**를 선택하고 **응용 프로그램 만들기**를 클릭합니다.  
  
        -   **새 사이트 만들기**를 선택합니다. 새 웹 사이트를 만들면 새 웹 응용 프로그램이 자동으로 만들어집니다.  
  
        > [!IMPORTANT]  
        >  이전 버전의 SQL Server([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)])에 있는 기존 MDS 웹 응용 프로그램을 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 Master Data Services 구성 관리자에서 선택할 수 있습니다. 기존 웹 응용 프로그램을 선택하는 대신 MDS용 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 웹 응용 프로그램을 만들어야 합니다. 이렇게 하지 않으면 웹 응용 프로그램을 업그레이드된 MDS 데이터베이스와 연결하려고 할 때 요청된 페이지의 관련 구성 데이터가 잘못되었기 때문에 해당 페이지에 액세스할 수 없다는 오류 메시지가 나타납니다.  
        >   
        >  MDS 웹 응용 프로그램에 기존([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) 웹 응용 프로그램과 동일한 이름(별칭)을 사용하려면 먼저 웹 응용 프로그램과 관련 응용 프로그램 풀을 IIS에서 삭제한 다음 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 Master Data Services 구성 관리자를 사용하여 동일한 이름의 웹 응용 프로그램을 만들어야 합니다. 웹 응용 프로그램과 응용 프로그램 풀을 IIS에서 제거하는 방법은 [응용 프로그램 제거(IIS)](http://go.microsoft.com/fwlink/?LinkId=323537) 및 [응용 프로그램 풀 제거(IIS)](http://go.microsoft.com/fwlink/?LinkId=323538)를 참조하세요.  
  
5.  이제 새 웹 응용 프로그램을 업그레이드된 MDS 데이터베이스와 연결합니다.  
  
    1.  **응용 프로그램을 데이터베이스에 연결** 섹션에서 **선택**을 클릭합니다.  
  
    2.  MDS 데이터베이스를 선택합니다.  
  
    3.  **적용**을 클릭합니다.  
  
## <a name="troubleshooting"></a>문제 해결  
 **문제:** 열 때는 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 응용 프로그램을 "클라이언트 버전이 데이터베이스 버전과 호환 되지 않습니다." 오류 메시지가 표시 됩니다.  
  
 **해결 방법:** 이 문제가 발생 하면는 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 마스터 데이터 관리자 웹 응용 프로그램을 업그레이드 된 데이터베이스에 액세스 하려고 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Master Data Services입니다. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 웹 응용 프로그램을 대신 사용해야 합니다.  
  
 MDS 데이터베이스 스키마를 업그레이드할 때 IIS에서 **MDS 응용 프로그램 풀** 을 정지하고 다시 시작하지 않은 경우에도 이 문제가 발생할 수 있습니다. **MDS 응용 프로그램 풀** 을 다시 시작하여 문제를 해결합니다.  
  
## <a name="see-also"></a>관련 항목  
 [MDS(Master Data Services) 설치](../../master-data-services/install-windows/install-master-data-services.md)  
  
  