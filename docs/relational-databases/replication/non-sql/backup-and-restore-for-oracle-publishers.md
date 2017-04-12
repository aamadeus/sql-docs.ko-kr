---
title: "Oracle 게시자 백업 및 복원 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "복구 [SQL Server 복제], Oracle 게시"
  - "백업 [SQL Server 복제], Oracle 게시"
  - "Oracle 게시 [SQL Server 복제], 백업 및 복원"
  - "복원 [SQL Server 복제], Oracle 게시"
ms.assetid: e5f181d0-cacf-442b-8b7a-202b3cfc358b
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# Oracle 게시자 백업 및 복원
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  백업 및 복원 시 다음 지침을 따릅니다.  
  
-   로그 판독기 에이전트가 실행되지 않아야 하며 게시자 백업 중 게시된 테이블에서 다른 데이터베이스 작업이 수행되지 않아야 합니다.  
  
-   게시자 및 배포자를 동시에 백업합니다.  
  
-   게시자 또는 배포자를 복원해야 할 경우 모든 구독을 다시 초기화합니다.  
  
-   구독을 다시 초기화할 필요 없이 백업에서 구독자를 복원하려면 마지막 구독 데이터베이스 백업이 완료된 후 배포 데이터베이스에 배달된 트랜잭션을 계속 사용할 수 있어야 합니다. 트랜잭션을 사용할 수 있는 시간은 배포 보존 설정에 따라 달라집니다. 이러한 설정에 대 한 정보를 참조 하십시오. [구독 만료 및 비활성화](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)합니다.  
  
-   데이터베이스 복원 후 게시자 또는 배포자가 동기화되지 않으면 복제 에이전트가 오류 메시지를 기록합니다. 이런 경우 모든 관련 게시 및 구독을 삭제하고 다시 만들어야 합니다.  
  
    1.  게시 및 구독의 정의를 스크립팅합니다. 자세한 내용은 [Scripting Replication](../../../relational-databases/replication/scripting-replication.md)를 참조하세요.  
  
         게시자 상태 버전과 배포자 상태 버전 간에 게시 정의가 변경된 경우에는 스크립트를 수정해야 합니다.  
  
    2.  게시 및 구독을 삭제합니다.  
  
    3.  1단계에서 만든 스크립트를 실행합니다.  
  
     게시자를 삭제하고 다시 구성해야 하는 경우 **CASCADE** 옵션으로 **MSSQLSERVERDISTRIBUTOR** 공용 동의어 및 구성된 Oracle 복제 사용자를 삭제하여 Oracle 게시자에서 모든 복제 개체를 제거합니다.  
  
## 참고 항목  
 [복제된 데이터베이스 백업 및 복원](../../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [Oracle 게시자 구성](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Oracle 게시 개요](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  