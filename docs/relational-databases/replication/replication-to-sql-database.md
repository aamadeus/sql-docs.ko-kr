---
title: "SQL 데이터베이스에 복제 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL 데이터베이스 복제"
  - "복제, SQL 데이터베이스"
ms.assetid: e8484da7-495f-4dac-b38e-bcdc4691f9fa
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# SQL 데이터베이스에 복제
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제 하도록 구성할 수 있습니다 [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]합니다.  
  
 **지원되는 구성:**  
  
-    [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스일 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온-프레미스 또는의 인스턴스를 실행 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라우드의 Azure 가상 컴퓨터에서 실행 합니다. 자세한 내용은 [Azure 가상 컴퓨터의 SQL Server 개요](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/)를 참조하십시오.  
  
-   [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 은(는) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자의 푸시 구독자여야 합니다.  
  
-   배포 데이터베이스 및 복제 에이전트는 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]에 위치할 수 없습니다.  
  
-   스냅숏 및 단방향 트랜잭션 복제만 지원됩니다. 피어 투 피어 트랜잭션 복제 및 병합 복제는 지원되지 않습니다.  
  
## 버전  
 게시자 및 배포자는 다음 버전 중 최소 하나여야 합니다.  
  
-   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP1 CU3  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] RTM CU10  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 CU8  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] s p 3에 필요합니다.  
  
 숫자 (프로세스 구독자에 연결 하지 못했습니다) MSSQL_REPL20084 및 MSSQL_REPL40532 오류가 발생할 수 있습니다 이전 버전을 사용 하 여 복제를 구성 하는 동안 (서버를 열 수 \< 이름> 로그인에서 요청한 합니다. 로그인 실패.)가 발생할 수 있습니다.  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 구독자는 최소 V12여야 하고 어느 지역에나 위치할 수 있습니다.  
  
 모든 기능을 사용 하 여 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 의 최신 버전을 사용 해야 [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx) 및 [SQL Server Data Tools](https://msdn.microsoft.com/library/mt204009.aspx)합니다.  
  
## 주의  
 복제는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을(를) 사용하거나 게시자의 기존 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행하여 구성할 수 있습니다. [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 포털을 사용하여 복제를 구성할 수 없습니다.  
  
 복제는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 로그인만 사용하여 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]에 연결할 수 있습니다.  
  
 복제된 테이블에는 기본 키가 있어야 합니다.  
  
 사용자는 기존 Azure 구독 및 기존 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] V12를 가져야 합니다.  
  
 단일 게시 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 모두 지원할 수 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (온-프레미스 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure 가상 컴퓨터에서) 구독자입니다.  
  
 복제 관리, 모니터링, 문제 해결 온-프레미스에서 수행 해야 하 고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다.  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에 대한 밀어넣기 구독만 지원됩니다.  
  
 만 `@subscriber_type = 0` 에서 지원 **sp_addsubscription** SQL 데이터베이스에 대 한 합니다.  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 양방향 텍스트, 즉시, 업데이트, 또는 피어 투 피어 복제를 지원 하지 않습니다.  
  
## 복제 아키텍처  
 ![replication-to-sql-database](../../relational-databases/replication/media/replication-to-sql-database.png "replication-to-sql-database")  
  
## 시나리오  
  
#### 일반적인 복제 시나리오  
  
1.  온-프레미스에서 트랜잭션 복제 게시를 만드는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스입니다.  
  
2.  온-프레미스에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용은 **새 구독 마법사** 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 푸시를 구독을 만드는 문을 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]합니다.  
  
3.  초기 데이터 집합은 일반적으로 스냅숏 에이전트에서 만들고 배포 에이전트에서 배포 및 적용한 스냅숏입니다. 초기 데이터 집합 제공할 수도 있습니다 백업 또는 다른 수단을 통해 같은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]합니다.  
  
#### 데이터 마이그레이션 시나리오  
  
1.  트랜잭션 복제를 사용 하 여 온-프레미스에서 데이터를 복제 하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]합니다.  
  
2.  업데이트 하려면 클라이언트 또는 중간 계층 응용 프로그램을 리디렉션하는 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 복사 합니다.  
  
3.  테이블의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전 업데이트를 중지하고 게시를 제거합니다.  
  
## 제한 사항  
 다음 옵션은 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 구독에서 지원되지 않습니다.  
  
-   파일 그룹 연결 복사  
  
-   테이블 파티션 구성표 복사  
  
-   인데스 파티션 구성표 복사  
  
-   사용자 정의 통계 복사  
  
-   기본 바인딩 복사  
  
-   규칙 바인딩 복사  
  
-   전체 텍스트 인덱스 복사  
  
-   XML XSD 복사  
  
-   XML 인덱스 복사  
  
-   사용 권한 복사  
  
-   공간 인덱스 복사  
  
-   필터링된 인덱스 복사  
  
-   데이터 압축 특성 복사  
  
-   스파스 column 특성 복사  
  
-   filestream을 MAX 데이터 형식으로 변환  
  
-   hierarchyId를 MAX 데이터 형식으로 변환  
  
-   공간을 MAX 데이터 형식으로 변환  
  
-   확장 속성 복사  
  
-   사용 권한 복사  
  
 결정해야 하는 제한 사항:  
  
-   데이터 정렬 복사  
  
-   SP의 직렬화된 트랜잭션에서 실행  
  
## 예  
 게시 및 밀어넣기 구독을 만듭니다. 참조 항목:  
  
-   [게시 만들기](../../relational-databases/replication/publish/create-a-publication.md)  
  
-   [밀어넣기 구독 만들기](../../relational-databases/replication/create-a-push-subscription.md) 를 사용 하 여는 [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] 구독자로 논리 서버 이름 (예를 들어 **N'azuresqldbdns.database.windows.net'**) 및 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 대상 데이터베이스 이름 (예를 들어 **AdventureWorks**).  
  
## 참고 항목  
 [게시 만들기](../../relational-databases/replication/publish/create-a-publication.md)   
 [밀어넣기 구독 만들기](../../relational-databases/replication/create-a-push-subscription.md)   
 [복제 유형](../../relational-databases/replication/types-of-replication.md)   
 [모니터링 및 #40입니다. 복제 및 #41;](../../relational-databases/replication/monitor/monitoring-replication.md)   
 [구독 초기화](../../relational-databases/replication/initialize-a-subscription.md)  
  
  