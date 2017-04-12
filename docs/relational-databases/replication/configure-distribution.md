---
title: "배포 구성 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "복제 [SQL Server], 배포"
  - "배포 구성 [SQL Server 복제]"
  - "원격 배포자 [SQL Server 복제]"
  - "트랜잭션 복제, 배포 구성"
  - "배포 데이터베이스 [SQL Server 복제], 크기 조정"
  - "배포자 [SQL Server 복제], 구성"
  - "배포 데이터베이스 [SQL Server 복제], 배포 데이터베이스 정보"
  - "배포 데이터베이스 [SQL Server 복제]"
  - "병합 복제 [SQL Server 복제], 배포 구성"
ms.assetid: 94d52169-384e-4885-84eb-2304e967d9f7
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# 배포 구성
  배포자는 배포 데이터베이스를 포함하는 서버이며 배포 데이터베이스는 트랜잭션 복제에 대한 모든 유형의 복제 및 트랜잭션에 대한 메타데이터와 기록 데이터를 저장합니다. 복제를 설정하려면 배포자를 구성해야 합니다. 각 게시자는 하나의 배포자 인스턴스에만 할당될 수 있지만 여러 게시자가 하나의 배포자를 공유할 수 있습니다. 배포자가 있는 서버에는 다음과 같은 추가 리소스가 필요합니다.  
  
-   게시에 대한 스냅숏 파일이 배포자에 저장되어 있는 경우(일반적으로 배포자에 저장되어 있음) 추가 디스크 공간  
  
-   배포 데이터베이스를 저장할 추가 디스크 공간  
  
-   배포자에서 실행되는 밀어넣기 구독에 대해 복제 에이전트가 사용할 추가 프로세서  
  
 배포자로 선택된 서버는 복제 및 해당 서버의 다른 작업을 지원하기 위해 충분한 디스크 공간과 처리 성능이 있어야 합니다. 배포자를 구성할 때 다음과 같은 사항을 지정합니다.  
  
-   이 배포자를 사용하는 모든 게시자에 대해 기본적으로 사용되는 스냅숏 폴더. 이 폴더가 이미 공유되어 있고 적절한 권한 집합이 설정되어 있는지 확인합니다. 자세한 내용은 참조 [스냅숏 폴더 보안](../../relational-databases/replication/security/secure-the-snapshot-folder.md)합니다.  
  
-   배포 데이터베이스의 이름 및 파일 위치. 배포 데이터베이스를 만든 후에는 이름을 변경할 수 없습니다. 데이터베이스에 다른 이름을 사용하려면 배포를 해제하고 다시 구성해야 합니다.  
  
-   배포자 사용을 허가받은 게시자. 배포자가 실행되는 인스턴스 이외의 게시자를 지정하면 게시자가 원격 배포자에 연결할 때 사용할 암호도 지정해야 합니다.  
  
 트랜잭션 복제의 경우 배포를 구성한 후 다음을 수행하는 것이 좋습니다.  
  
-   배포 데이터베이스 크기를 적절히 조정합니다. 시스템에서 명령 저장에 필요한 공간을 결정할 수 있도록 일반적인 로드 상태에서 복제를 테스트합니다. 데이터베이스는 자주 자동 증가되지 않고도 명령을 저장할 수 있을 만큼 충분히 커야 합니다. 데이터베이스의 크기를 변경 하는 방법에 대 한 자세한 내용은 참조 [ALTER DATABASE & #40; TRANSACT-SQL & #41;](../../t-sql/statements/alter-database-transact-sql.md)합니다.  
  
-   배포 데이터베이스에 **sync with backup** 옵션을 설정합니다. 자세한 내용은 참조 [백업 및 복원 스냅숏 및 트랜잭션 복제에 대 한 전략](../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) 및 [트랜잭션 복제 및 #40;에 대 한 통합 백업을 사용 하도록 설정 복제 TRANSACT-SQL 프로그래밍 & #41;](../../relational-databases/replication/administration/enable coordinated backups for transactional replication.md)합니다.  
  
## 로컬 및 원격 배포자  
 기본적으로 배포자는 게시자와 같은 서버(로컬 배포자)이지만 게시자와는 다른 별도의 서버(원격 배포자)일 수도 있습니다. 일반적으로 다음 작업을 수행하려는 경우 원격 배포자를 사용합니다.  
  
-   게시자에 대한 복제의 영향을 최소화하기 위해(예: 게시자가 OLTP 서버인 경우) 처리를 다른 컴퓨터로 오프로드  
  
-   여러 게시자에 대해 중앙 집중식 배포자 구성  
  
 다음과 같은 두 가지 이유로 원격 배포자는 병합 복제보다 트랜잭션 복제에서 더 많이 사용됩니다.  
  
-   복제한 모든 트랜잭션은 배포 데이터베이스에 작성되고 배포 데이터베이스에서 읽어 오기 때문에 배포자는 트랜잭션 복제에서 더 큰 역할을 합니다.  
  
-   병합 복제 토폴로지는 일반적으로 끌어오기 구독을 사용하므로 에이전트는 배포자에서 모두 실행되기 보다는 각각의 구독자에서 실행됩니다. 자세한 내용은 참조 [게시를 구독할](../../relational-databases/replication/subscribe-to-publications.md)합니다. 대부분의 경우 병합 복제에 대해서는 로컬 배포자를 사용해야 합니다.  
  
 게시 및 배포를 구성하려면 [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)을 참조하십시오.  
  
 게시자 및 배포자 속성을 수정하려면 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)을 참조하십시오.  
  
## 참고 항목  
 [데이터 및 데이터베이스 개체 게시](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [배포자 보안 설정](../../relational-databases/replication/security/secure-the-distributor.md)  
  
  