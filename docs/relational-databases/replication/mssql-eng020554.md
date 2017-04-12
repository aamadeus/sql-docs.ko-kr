---
title: "MSSQL_ENG020554 | Microsoft Docs"
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
  - "MSSQL_ENG020554 오류"
ms.assetid: ef1a1b88-b2ab-43e8-99cd-163a973262d6
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# MSSQL_ENG020554
    
## 메시지 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|20554|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|심볼 이름||  
|메시지 텍스트|복제 에이전트가 %ld분 동안 진행률 메시지를 로깅하지 않았습니다. 이것은 에이전트가 응답하지 않거나 시스템 작업이 많음을 나타낼 수 있습니다. 레코드가 대상으로 복제되고 구독자, 게시자 및 배포자에 대한 연결이 여전히 활성 상태인지 확인하십시오.|  
  
## 설명  
  **복제 에이전트 점검** 작업이 실행 되어 지정된 된 간격 (기본적으로 10 분)으로 각 복제 에이전트의 상태를 확인 합니다. 에이전트 점검 작업이 마지막으로 실행된 후 에이전트가 진행 메시지를 기록하지 않은 경우 MSSQL_ENG020554 오류가 발생될 수 있습니다. 다른 복제 작업이 일어나지 않아도 에이전트에서는 최소한 기록 메시지를 기록합니다. 복제 에이전트가 예상대로 응답하지 않는다고 반드시 중지하거나 실패하지는 않습니다. 에이전트가 실패한 경우에는 MSSQL_ENG020536 오류가 발생합니다.  
  
 다음 문제로 인해 MSSQL_ENG020554 오류가 발생할 수 있습니다.  
  
-   에이전트에서 너무 많은 작업이 수행되고 있습니다.  
  
     에이전트 점검 작업으로 폴링할 때 에이전트에서 너무 많은 작업이 수행되고 있어 응답할 수 없으면 에이전트 점검 작업은 복제 에이전트가 제대로 작동하고 있는지 보고할 수 없습니다. 복제 중인 데이터가 많거나 응용 프로그램 디자인 또는 구성 문제로 인해 프로세스가 장시간 실행하게 되는 등 여러 가지 이유로 인해 복제 에이전트에서 많은 작업이 수행되고 있을 수 있습니다.  
  
-   에이전트가 토폴로지의 한 컴퓨터에 로그인할 수 없습니다.  
  
     모든 에이전트는 매개 변수가 **-LoginTimeOut** (15 초로 기본적으로 설정), 에이전트 기간을 제어 하에 로그인 하는 게시자에 로그인 하는 병합 에이전트 같은 복제 노드를 하려고 합니다. 하는 경우는 **-LoginTimeOut** 값이 복제 에이전트 점검 작업이 실행 되는 간격 보다 높게 설정 되 면 로그인 문제가 오류의 근본 원인을 수 없습니다: 해당 에이전트는 보다 구체적인 오류를 발생 시키기 전에 MSSQL_ENG020554 오류가 발생 합니다.  
  
## 사용자 동작  
 필요한 동작은 오류의 원인에 따라 다릅니다.  
  
-   이 오류가 발생된 모든 경우  
  
     복제 모니터에서 오류 정보를 확인한 다음 중지된 에이전트를 다시 시작합니다. 오류 정보에는 에이전트가 제대로 실행되지 않는 원인에 대한 추가 정보가 포함될 수 있습니다. 에이전트가 실행 중이면 에이전트를 중지했다가 다시 시작하지 마십시오. 이렇게 하면 문제를 악화시킬 수 있습니다. 복제 모니터에서 에이전트 상태 및 오류 정보를 보는 방법은 다음 항목을 참조하십시오.  
  
    -   스냅숏 에이전트, 로그 판독기 에이전트 및 큐 판독기 에이전트에 대 한 참조 [정보 보기 및 에이전트 관련 된는 게시 및 #40;에 대 한 작업 수행 복제 모니터 & #41;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md)합니다.  
  
    -   배포 에이전트 및 병합 에이전트에 대 한 참조 [정보 보기 및는 에이전트 구독 관련 & #40;에 대 한 작업 수행 복제 모니터 & #41;](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)합니다.  
  
-   에이전트에서 많은 작업이 수행되고 있어 이 오류가 자주 발생하는 경우  
  
     에이전트에서의 처리 시간을 줄이도록 응용 프로그램을 다시 설계해야 할 수 있습니다.  
  
     **작업 속성** 대화 상자를 사용하여 에이전트 상태의 점검 간격을 늘일 수 있습니다. 복제 작업에 대 한이 대화 상자에 액세스 하는 방법에 대 한 정보를 참조 하십시오. [정보 보기 및 게시자 및 #40;에 대 한 작업 수행 복제 모니터 & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)합니다.  
  
-   에이전트가 토폴로지의 한 컴퓨터에 로그인할 수 없는 경우  
  
     권장 사항은 **-LoginTimeOut** 값 복제 에이전트 점검 작업이 실행 되는 간격 보다 낮게 설정할 수 있습니다. 일부 경우에 대 한 값에 **-LoginTimeOut** 로그인 제한 시간 초과로 처리 하는 네트워크 문제 때문에 높게 설정 되어 있습니다. 하는 경우는 **-LoginTimeOut** 낮게 설정 되, 복제에 사용 권한, 네트워크 문제 또는 다른 문제로 인해 일어날 수 있는 로그인 문제를 해결할 수 있도록 하는 보다 구체적인 오류를 보고할 수 있습니다. 에이전트 프로필 및 명령줄에서 에이전트 매개 변수를 지정할 수 있습니다. 참조 항목:  
  
    -   [복제 에이전트 프로필 작업](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [보기 및 복제 에이전트 명령 프롬프트 매개 변수 & #40; 수정 SQL Server Management Studio & #41;](../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [복제 에이전트 실행 파일 개념](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)합니다.  
  
## 참고 항목  
 [복제 에이전트 관리](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [오류 및 이벤트 참조 & #40입니다. 복제 및 #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [복제 배포 에이전트](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [복제 로그 판독기 에이전트](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [복제 병합 에이전트](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [복제 큐 판독기 에이전트](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [복제 스냅숏 에이전트](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  