---
title: "MSSQL_REPL027183 | Microsoft Docs"
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
  - "MSSQL_REPL027183 오류"
ms.assetid: 52c271ac-1a0e-43d5-85d4-35886d1efd32
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_REPL027183
    
## 메시지 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|27183|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|심볼 이름||  
|메시지 텍스트|병합 프로세스에서 매개 변수가 있는 행 필터를 사용하여 아티클의 변경 내용을 열거하지 못했습니다. 이 오류가 계속되면 이 프로세스에 대한 쿼리 제한 시간을 늘리고 게시 보존 기간을 줄인 다음 게시된 테이블의 인덱스를 향상시키십시오.|  
  
## 설명  
 이 오류는 필터링된 게시에서 변경 내용을 처리하는 동안 병합 에이전트 제한 시간에 도달한 경우 발생합니다. 다음 문제 중 하나로 인해 제한 시간에 도달했을 수 있습니다.  
  
-   사전 계산 파티션 최적화를 사용하지 않았습니다.  
  
-   열의 인덱스 조각화가 필터링에 사용되었습니다.  
  
-   와 같은 큰 병합 메타 데이터 테이블, **MSmerge_tombstone**, **MSmerge_contents**, 및 **MSmerge_genhistory**합니다.  
  
-   필터링된 테이블이 고유 키에 조인되어 있지 않고 많은 테이블이 조인 필터와 관련되어 있습니다.  
  
## 사용자 동작  
 이 문제를 해결하려면  
  
-   값 늘리기는 **-QueryTimeOut** 처리를 허용 하도록 병합 에이전트에 대 한 매개 변수에 기본 해결 하는 동안 계속 실행 오류가 발생 합니다. 에이전트 프로필 및 명령줄에서 에이전트 매개 변수를 지정할 수 있습니다. 참조 항목:  
  
    -   [복제 에이전트 프로필 작업](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [보기 및 복제 에이전트 명령 프롬프트 매개 변수 & #40; 수정 SQL Server Management Studio & #41;](../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [복제 에이전트 실행 파일 개념](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)합니다.  
  
-   사전 계산 파티션 최적화를 사용합니다(가능한 경우). 많은 게시 요구 사항이 충족되면 이 최적화가 기본적으로 사용됩니다. 이러한 요구 사항에 대 한 자세한 내용은 참조 [사전 계산 파티션으로 매개 변수가 있는 필터 성능 최적화](../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md)합니다. 게시가 이러한 요구 사항을 충족하지 않는 경우 게시를 다시 디자인하십시오.  
  
-   복제는 보존 기간에 도달할 때까지 게시 및 구독 데이터베이스의 메타데이터를 정리할 수 없으므로 게시 보존 기간에 대해 가능한 가장 낮은 설정을 지정합니다. 자세한 내용은 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)를 참조하세요.  
  
-   병합 복제에 대 한 유지 관리의 일환으로, 병합 복제와 관련 된 시스템 테이블의 증가 확인 가끔: **MSmerge_contents**, **MSmerge_genhistory**, 및 **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, 및 **MSmerge_past_partition_mappings**합니다. 이러한 테이블의 인덱스를 주기적으로 다시 만듭니다. 자세한 내용은 참조 [다시 구성 및 인덱스 다시 작성](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)합니다.  
  
-   필터링에 사용된 열이 올바로 인덱싱되는지 확인하고 이러한 인덱스를 다시 작성합니다(필요한 경우). 자세한 내용은 참조 [다시 구성 및 인덱스 다시 작성](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)합니다.  
  
-   설정의 **join_unique_key** 고유 열을 기반으로 하는 조인 필터에 대 한 속성입니다. 자세한 내용은 [Join Filters](../../relational-databases/replication/merge/join-filters.md)를 참조하세요.  
  
-   조인 필터 계층에서 테이블의 수를 제한합니다. 5개 이상의 테이블을 가진 조인 필터를 생성하는 경우 다른 해결책을 고려하는 것이 좋습니다. 크기가 작거나, 변경될 가능성이 없거나, 기본적으로 조회 테이블에 해당하는 테이블은 필터링하지 마십시오. 구독 간에 분할해야 하는 테이블 사이에서만 조인 필터를 사용합니다.  
  
-   동기화 사이에 있는 필터링된 테이블에 대한 변경 횟수를 줄이거나 병합 에이전트를 더 자주 실행합니다. 동기화 일정 설정 방법은 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)을 참조하십시오.  
  
## 참고 항목  
 [오류 및 이벤트 참조 & #40입니다. 복제 및 #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  