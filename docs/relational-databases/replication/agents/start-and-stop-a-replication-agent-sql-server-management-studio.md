---
title: "복제 에이전트 시작 및 중지(SQL Server Management Studio) | Microsoft Docs"
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
  - "에이전트 [SQL Server 복제], 중지"
  - "에이전트 [SQL Server 복제], 시작"
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# 복제 에이전트 시작 및 중지(SQL Server Management Studio)
  시작 및 중지에서 에이전트는 **작업** 폴더 및 **복제** 폴더에 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 및 복제 모니터에서. 다음 에이전트 및 작업을 시작하고 중지할 수 있습니다.  
  
-   스냅숏 에이전트 - 모든 게시에서 사용  
  
-   로그 판독기 에이전트 - 모든 트랜잭션 게시에서 사용  
  
-   큐 판독기 에이전트 - 지연 업데이트 구독이 활성화된 트랜잭션 게시에서 사용  
  
-   배포 에이전트 - 구독을 트랜잭션 및 스냅숏 게시와 동기화함  
  
-   병합 에이전트 - 구독을 병합 게시와 동기화함  
  
-   복제 유지 관리 작업  
  
 병합 에이전트 및 배포 에이전트를 시작 하는 방법에 대 한 자세한 내용은 참조 [밀어넣기 구독을 동기화](../../../relational-databases/replication/synchronize-a-push-subscription.md) 및 [끌어오기 구독을 동기화](../../../relational-databases/replication/synchronize-a-pull-subscription.md)합니다. 유지 관리 작업에 대 한 자세한 내용은 참조 [복제 유지 관리 작업을 실행 및 #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md)합니다.  
  
 복제 모니터를 시작 하는 방법에 대 한 정보를 참조 하십시오. [복제 모니터 시작](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)합니다.  
  
### Management Studio에서 스냅숏 에이전트 또는 로그 판독기 에이전트를 시작하고 중지하려면  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]에서 게시자에 연결한 다음 해당 서버 노드 및 **복제** 폴더를 확장합니다.  
  
2.  확장 된 **로컬 게시** 폴더를 만들고 게시를 마우스 오른쪽 단추로 합니다.  
  
3.  **스냅숏 에이전트 상태 보기** 또는 **로그 판독기 에이전트 상태 보기**를 클릭합니다.  
  
4.  **시작** 또는 **중지**를 클릭합니다.  
  
### Management Studio에서 큐 판독기 에이전트를 시작하고 중지하려면  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]에서 배포자에 연결한 다음 해당 서버 노드를 확장합니다.  
  
2.  **SQL Server 에이전트** 폴더를 확장한 다음 **작업** 폴더를 확장합니다.  
  
3.  에이전트에 대 한 작업을 마우스 오른쪽 단추로 누른 **작업 시작** 또는 **작업 중지**합니다. 폼에는 큐 판독기 에이전트에 대 한 작업의 이름 **[\< 배포자>]. \< 정수>**합니다.  
  
### 복제 모니터에서 스냅숏 에이전트, 로그 판독기 에이전트 또는 큐 판독기 에이전트를 시작하고 중지하려면  
  
1.  왼쪽 창에서 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.  
  
2.  **에이전트** 탭을 클릭합니다.  
  
3.  에이전트를 마우스 오른쪽 단추로 누른 **에이전트 시작** 또는 **에이전트 중지**합니다.  
  
## 참고 항목  
 [복제 모니터링](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [복제 에이전트 실행 파일 개념](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [복제 에이전트 개요](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  