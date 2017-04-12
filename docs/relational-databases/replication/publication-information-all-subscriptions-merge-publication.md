---
title: "게시 정보, 모든 구독(병합 게시) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.publicationinfo.allsubscriptions.merge.f1"
ms.assetid: 0f4fa946-a0d9-4d3b-b90b-53503c40fba2
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# 게시 정보, 모든 구독(병합 게시)
  **모든 구독** 탭은 선택한 병합 게시에 대한 모든 구독 정보를 표시합니다.  
  
## 옵션  
 자세한 내용 및 구독과 관련된 태스크를 보려면 해당 구독에 대한 행을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 옵션을 클릭합니다. 표에서 데이터를 표시하는 방식을 변경하려면 표를 마우스 오른쪽 단추로 클릭한 후 다음 옵션 중 하나를 클릭합니다.  
  
-   **정렬**: **열 정렬** 대화 상자에서 한 개 이상의 열에 정렬합니다.  
  
-   **표시할 열 선택**: **열 선택** 대화 상자에서 표시할 열 및 해당 열이 표시되는 순서를 선택합니다.  
  
-   **필터**: **필터 설정** 대화 상자의 열 값에 따라 표의 행을 필터링합니다.  
  
-   **필터 지우기**: 표에 대한 모든 필터 설정을 지웁니다.  
  
 필터 설정은 각 표에 대해 지정됩니다. 열 선택 및 정렬은 각 게시자에 대한 게시 표와 같이 동일한 유형의 모든 표에 적용됩니다.  
  
 **표시**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당됩니다. 선택한 구독 유형에 대해 표시할 구독 상태를 선택합니다. 예를 들어 오류가 있는 구독만 표시하도록 선택할 수 있습니다.  
  
 **상태**  
 병합 에이전트의 상태에 의해 결정되는 각 구독의 상태입니다.  
  
 기본적으로 구독 정보가 포함 된 표는 기준으로 정렬 된 **상태** 열 (다음 기준으로 정렬 하 고는 **성능** 상태가 같은 구독에 대 한 열)입니다. 다음 목록에서는 가능한 상태 값 및 값 정렬 순서를 보여 줍니다. 예를 들어 오류는 항상 표의 맨 위에 표시됩니다.  
  
-   오류  
  
-   성능 심각([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전만 해당)  
  
-   장기 실행 트랜잭션 병합([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당)  
  
-   곧 만료됨/만료됨([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전만 해당)  
  
-   초기화되지 않은 구독([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당)  
  
-   실패한 명령 다시 시도 중  
  
-   동기화 중  
  
-   비동기화 중  
  
 정렬 순서는 지정한 구독의 상태가 두 가지 이상일 경우에 표시할 값도 결정합니다. 예를 들어 구독에 오류가 있고 곧 만료될 예정이면 **상태** 열에 **오류**가 표시됩니다.  
  
 상태 값은 **성능 심각**, **장기 실행 트랜잭션 병합**, **곧 만료 됨/만료 됨**, 및 **초기화 되지 않은 구독** 은 경고입니다. 경고를 표시할 때 **상태** 열은 에이전트가 동기화 중인지 여부도 표시합니다. 예를 들어 상태가 **동기화 중, 성능 심각**과 같이 표시될 수 있습니다.  
  
 상태 값은 **곧 만료 됨/만료 됨** 및 **장기 실행 트랜잭션 병합** 임계값이 설정 되어 있는 경우에 표시 될 수 있습니다. 상태 값 **성능 심각** 5 회 동기화 동일한 연결 유형 (전화 접속 또는 LAN) 사용 하 여 구독 한 후에 표시할 수 있습니다. 성능 측정 및 임계값 설정에 대 한 정보를 참조 하십시오. [복제 모니터로 성능 모니터링](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md) 및 [임계값 설정 및 복제 모니터에서 경고](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)합니다.  
  
 **구독**  
 양식에서 각 구독 이름:*SubscriberName: SubscriptionDatabaseName*합니다.  
  
 **이름**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당됩니다. 각 구독에 대한 설명입니다. 설명에 입력 되는 **구독 속성** 대화 상자 또는 지정 된는 **@description** 의 매개 변수 [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md) 또는 [sp_addmergepullsubscription](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)합니다. 설명을 구독의 "이름" 또는 애칭으로 사용하기도 합니다.  
  
 **성능**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당됩니다. 복제 모니터에서 측정한 가장 최근의 배달 속도 측정값을 기반으로 하는 각 구독의 성능 등급입니다. 등급은 개별 구독 성능과 게시에 대한 구독(연결 유형이 전화 접속 또는 LAN 등으로 동일한 구독)의 평균 기록 성능을 비교하여 결정됩니다. 복제 모니터는 같은 유형의 연결별로 50개 이상의 변경 사항을 5번 동기화한 후에 값을 표시합니다. 50개 이상의 변경 사항에 대해 동기화가 5번 미만으로 수행되었거나 가장 최근에 동기화가 수행된 변경 사항이 50개 미만인 경우에는 이 열이 비어 있습니다.  
  
> [!NOTE]  
>  성능 기반에 표시 되는 연결 유형에 **연결** 열에 따라서가 배달 속도가 느린 구독이 더 나은 성능 등급을 다른 구독 보다 느린 연결을 통해 첫 번째 구독이 동기화 되 면 표시를 사용 하 여 구독에 대 한 수입니다.  
  
 성능 등급은 다음 값 중 하나입니다.  
  
-   최고  
  
-   좋음  
  
-   보통  
  
-   나쁨  
  
 성능 등급 정의 방법 및 성능 임계값 설정 방법에 대 한 자세한 내용은 참조 하십시오. [복제 모니터로 성능 모니터링](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)합니다.  
  
 **배달 속도**  
 병합 에이전트에서 처리하는 초당 행 수입니다.  
  
 **마지막 동기화**  
 병합 에이전트가 마지막으로 실행된 시간입니다. 마지막 동기화 중에 변경 내용이 처리될 수도 있고 처리되지 않을 수도 있습니다. 동기화가 진행 중이면 백분율로 진행 상황을 표시합니다.  
  
 **기간**  
 마지막 동기화 중에 병합 에이전트가 실행된 시간입니다. 병합 에이전트가 현재 동기화 중이면 이 시간은 경과된 시간을 나타내고 병합 에이전트가 이전에 동기화된 경우에는 총 시간을 나타냅니다.  
  
 **연결**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당됩니다. 구독자와 게시자 간의 연결 유형입니다. 가능한 값은 **LAN**, **전화 접속**및 **인터넷**입니다. **인터넷** 값은 구독에서 웹 동기화를 사용하는 경우에 표시됩니다.  
  
## 참고 항목  
 [복제 모니터 시작](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [정보를 보고 가입 & #40;에 대 한 작업을 수행 합니다. 복제 모니터 & #41.](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [정보 보기 및 구독 & #40;와 관련 된 에이전트에 대 한 작업을 수행 합니다. 복제 모니터 & #41.](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)   
 [복제 모니터링](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [병합 복제에 대한 웹 동기화](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  