---
title: "SQL Server 2005에서 업그레이드하나요? | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad40e66f-71fe-4ee6-9ce3-17127e7b1d7a
caps.latest.revision: 21
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 21
---
# SQL Server 2005에서 업그레이드하나요?
  SQL Server 2005 지원 연장이 종료되므로 새 버전의 SQL Server와 Azure SQL 데이터베이스로 업그레이드할 이유가 생겼습니다. 업그레이드를 통해 보안 및 규정 준수를 유지할 수 있고, 획기적인 성능을 달성하고 데이터 플랫폼 인프라를 최적화할 수 있습니다.  
  
 업그레이드 또는 마이그레이션을 계획하고 자동화하기 위한 자세한 정보, 지침 및 도구는 [SQL Server 2005 지원 종료](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/)를 참조하세요.  
  
## 업그레이드가 필요한 이유  
  
> [!IMPORTANT]  
>  SQL Server 2005에 대한 추가 지원이 2016년 4월 12일에 끝납니다. 2016년 4월 12일 후에도 SQL Server 2005를 실행하는 경우 보안 업데이트를 더 이상 받을 수 없습니다.  
  
 SQL Server 2005에서 업그레이드 하는 경우의 이점을 설명하는 PDF 형식의 데이터 시트를 가져오려면 아래의 축소판 이미지를 클릭하지 말고 [여기를 클릭](https://info.microsoft.com/rs/157-GQE-382/images/EN-CNTNT-Infographic-UpgradeSQL2005Datasheet.pdf)하세요.  
  
 ![Data sheet about upgrading from SQL Server 2005](../../database-engine/install-windows/media/sqlserver2005eos.png "Data sheet about upgrading from SQL Server 2005")  
  
## 업그레이드 옵션 선택  
 관계형 데이터베이스를 SQL Server 2005에서 업그레이드하는 경우 Microsoft 플랫폼의 관계형 저장소에 대한 옵션은 다음과 같습니다.  
  
 이러한 옵션에 대한 보다 포괄적인 분석을 보려면 [여기를 클릭](http://sql05upgrade.azurewebsites.net/)하세요.  
  
|관계형 저장소 옵션|이점|고려할 기타 요소|  
|-------------------------------|--------------|-------------------------------|  
|**온-프레미스 SQL Server**<br /><br /> 트랜잭션 시스템에서 데이터 웨어하우스에 이르는 모든 종류의 데이터베이스 응용 프로그램의 경우 이 옵션을 고려합니다.|하드웨어와 소프트웨어를 모두 관리하기 때문에 기능과 확장성을 최대한으로 제어할 수 있습니다.<br /><br /> SQL Server 2005에서 업그레이드하는 경우 이 환경이 가장 유사한 환경입니다.|하드웨어와 소프트웨어를 직접 구입하고 유지 및 관리해야 하므로 사전 투자 비용이 가장 크고 최대한의 지속적 관리를 제공해야 합니다.<br /><br /> 자세한 내용은 [SQL Server 2016](https://www.microsoft.com/EN-US/server-cloud/products/sql-server-2016/)을 참조하세요.|  
|**Azure 가상 컴퓨터에 호스트된 SQL Server**<br /><br /> 다음 이점을 원하는 경우 이 옵션을 선택하는 것이 좋습니다.<br /><br /> 호스트된 환경으로 마이그레이션하는 경우의 이점<br /><br /> 운영 환경에 대한 제어<br /><br /> 익숙한 SQL Server 기능 집합|가상 컴퓨터 이미지의 라이브러리에서 신속하게 배포할 수 있습니다.<br /><br /> 전체 SQL Server 기능 집합을 사용할 수 있습니다.<br /><br /> 하드웨어와 서버 소프트웨어의 비용을 절감합니다. 시간 단위 사용량에 대한 요금만 지불합니다.|SQL Server와 운영 체제 소프트웨어를 모두 구성하고 관리해야 합니다.<br /><br /> <br /><br /> 자세한 내용은 [Azure 가상 컴퓨터의 SQL Server 개요](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/)를 참조하세요.<br /><br /> 마이그레이션에 대한 정보는 [Azure VM의 SQL Server로 데이터베이스 마이그레이션](https://azure.microsoft.com/documentation/articles/virtual-machines-migrate-onpremises-database/)을 참조하세요.|  
|**Azure SQL 데이터베이스에서 호스트된 데이터베이스 서비스**<br /><br /> 유지 관리가 적게 필요한 저렴한 비용의 솔루션을 원하는 경우 이 옵션을 고려합니다.<br /><br /> 이 옵션은 필요한 용량이 시기에 따라 일정하지 않거나 외부 액세스를 제공해야 하는 앱의 경우 특히 적합합니다.|신속하게 배포하고 쉽게 확장할 수 있습니다.<br /><br /> 시간 단위 사용량에 대한 요금만 지불합니다.<br /><br /> 서비스의 비용에는 저장소뿐 아니라 고가용성 및 자동화된 백업도 포함됩니다.|Azure SQL 데이터베이스에는 호스트된 클라우드 환경에서 적용할 수 없는 일부 SQL Server 기능이 없습니다. 자세한 내용은 [Azure SQL 데이터베이스 Transact-SQL 정보](https://azure.microsoft.com/documentation/articles/sql-database-transact-sql-information/)를 참조하세요.<br /><br /> Azure SQL 데이터베이스의 최대 데이터베이스 크기는 500GB이고 SQL Server의 경우에는 524PB입니다.<br /><br /> 자세한 내용은 [SQL 데이터베이스](https://azure.microsoft.com/services/sql-database/)를 참조하세요.<br /><br /> 마이그레이션에 대한 자세한 내용은 [Azure SQL 데이터베이스로 SQL Server 데이터베이스 마이그레이션](https://azure.microsoft.com/documentation/articles/sql-database-cloud-migrate/)을 참조하세요.|  
  
 특정 데이터 및 응용 프로그램의 경우 비관계형 또는 NoSQL 솔루션을 고려할 수도 있습니다.  
  
|비관계형 솔루션|이점|  
|------------------------------|--------------|  
|**Azure DocumentDB**<br /><br /> JSON 데이터를 사용하고 강력한 쿼리와 트랜잭션 데이터 처리를 함께 필요로 하는 확장 가능한 최신 모바일 및 웹 응용 프로그램의 경우 이 옵션을 고려합니다.<br /><br /> 자세한 내용은 [DocumentDB](https://azure.microsoft.com/en-us/services/documentdb/)를 참조하세요.<br /><br /> 데이터 가져오기에 대한 자세한 내용은 [DocumentDB에 데이터 가져오기](https://azure.microsoft.com/documentation/articles/documentdb-import-data/)를 참조하세요.|문서는 인덱싱되며 익숙한 SQL 구문을 사용하여 문서를 쿼리할 수 있습니다.<br /><br /> 데이터베이스는 스키마 없는 데이터베이스입니다.<br /><br /> 인덱스를 다시 작성하지 않고도 문서에 속성을 추가할 수 있습니다.<br /><br /> 데이터베이스 엔진 내에서 직접 JSON 및 JavaScript 지원을 이용합니다.<br /><br /> Azure 검색, HDInsight, Data Factory 등 다른 Azure 서비스와의 통합 및 지리 공간적 데이터에 대한 기본 지원을 이용합니다.<br /><br /> 예약된 처리량 수준을 통해 대기 시간이 짧은 고성능 저장소를 사용합니다.|  
|**Azure 테이블 저장소**<br /><br /> 비용 효율적인 솔루션에서 페타바이트 규모의 반구조적 데이터를 저장하려면 이 옵션을 고려합니다.<br /><br /> 자세한 내용은 [테이블 저장소](https://azure.microsoft.com/services/storage/tables/)를 참조하세요.|데이터를 오프라인으로 전환하지 않고도 앱과 테이블 스키마를 개발할 수 있습니다.<br /><br /> 데이터 집합을 분할하지 않고도 확장할 수 있습니다.<br /><br /> 여러 지역에 걸쳐 데이터를 복제하는 지역 중복 저장소를 사용합니다.|  
  
 Microsoft의 지침에 따라 업그레이드 옵션에 대한 자세한 정보가 있는 "SQL Server 2005에서 마이그레이션" 보고서를 다운로드하려면 [여기를 클릭](https://info.microsoft.com/CO-SQL-CNTNT-FY16-09Sep-14-ModernizationDirOnMFST-Register.html)하세요(아래의 축소판 이미지는 아님).  
  
 ![Report about migrating from SQL Server 2005](../../database-engine/install-windows/media/sqlserver2005migratingdoc.png "Report about migrating from SQL Server 2005")  
  
## 업그레이드 계획  
  
-   SQL Server 팀에서 올린 다음 일련의 블로그 게시물을 통해 업그레이드를 계획 하는 방법에 대해 알아봅니다.  
  
    -   [SQL Server 2005에서 효율적인 업그레이드 계획: 1/3단계](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/10/planning-an-efficient-upgrade-from-sql-server-2005-step-1-of-3.aspx)  
  
    -   [SQL Server 2005에서 효율적인 업그레이드 계획: 2/3단계](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/15/planning-an-efficient-upgrade-from-sql-server-2005-step-2-of-3.aspx)  
  
    -   [SQL Server 2005에서 효율적인 업그레이드 계획: 3/3단계](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/17/planning-an-efficient-upgrade-from-sql-server-2005-step-3-of-3.aspx)  
  
-   [Planning a SQL Server Installation](../../sql-server/install/planning-a-sql-server-installation.md)에서 [Hardware and Software Requirements for Installing SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)을 비롯한 요구 사항과 고려 사항을 검토합니다.  
  
-   업그레이드 하는 방법에 대해 알아봅니다.  
  
    -   [Upgrade Database Engine](../../database-engine/install-windows/upgrade-database-engine.md)항목에서 사용 가능한 업그레이드 방법을 검토하고 계획 및 테스트 방법을 알아봅니다.  
  
        > [!IMPORTANT]  
        >  SQL Server 2005 서버를 SQL Server 2016 서버로 현재 위치에서 업그레이드할 수는 없습니다. SQL Server 2016을 설치한 다음 SQL Server 2005 데이터베이스를 새 설치로 마이그레이션해야 합니다. 자세한 내용은 [Choose a Database Engine Upgrade Method](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md)항목에서 "새 설치 업그레이드" 섹션을 참조하세요.  
  
    -   더 자세한 "기술 업그레이드 가이드"를 PDF 형식으로 다운로드하려면 [여기를 클릭](http://download.microsoft.com/download/7/1/5/715BDFA7-51B6-4D7B-AF17-61E78C7E538F/SQL_Server_2014_Upgrade_technical_guide.pdf)하세요.  
  
        > [!NOTE]  
        >  이 문서는 현재 SQL Server 2014 버전의 "기술 업그레이드 가이드"입니다. SQL Server 2016 버전 가이드는 아직 제공되지 않습니다.  
  
-   업그레이드 또는 마이그레이션을 계획하고 자동화하기 위한 자세한 정보, 지침 및 도구는 [SQL Server 2005 지원 종료](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/)를 참조하세요.  
  
## SQL Server 2016 다운로드  
 SQL Server 2016의 평가판을 다운로드하려면 [여기를 클릭](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016/?wt.mc_id=upgrade2005)하세요.  
  
## 참고 항목  
 [SQL Server 2016](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2016/default.aspx)   
 [SQL Server 2005 지원 종료](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/)   
 [SQL Server 2005에서 SQL Server 2014로 업그레이드](https://msdn.microsoft.com/en-us/library/mt170591\(v=sql.120\).aspx)  
  
  