---
title: 게시자에 대한 정보 보기 및 태스크 수행(복제 모니터) | Microsoft 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Publishers [SQL Server replication], Replication Monitor tasks
- viewing Publisher information
- Publishers [SQL Server replication], viewing information
ms.assetid: 1e777e95-377a-4de3-b965-867464aadaaf
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2e86d1593d330abd5ae220d2d571abdbb1e08126
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758611"
---
# <a name="view-information-and-perform-tasks-for-a-publisher-replication-monitor"></a>게시자에 대한 정보 보기 및 태스크 수행(복제 모니터)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  복제 모니터는 선택한 게시자에 대한 정보를 표시하는 다음 탭을 제공합니다.  
  
-   **게시**  
  
     이 탭에는 선택한 게시자에 있는 모든 게시 정보가 표시됩니다.  
  
-   **구독 조사 목록**  
  
     이 탭에는 오류 또는 경고가 발생하거나 성능이 가장 낮은 선택된 게시자에서 사용 가능한 모든 게시의 구독에 대한 정보가 표시됩니다. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]이전 버전을 실행하는 배포자의 경우 이 탭이 표시되지 않습니다.  
  
-   **에이전트** 탭  
  
     이 탭에는 모든 복제 유형에 사용되는 에이전트 및 작업에 대한 세부 정보가 표시됩니다. 이 탭에서는 각 에이전트 및 작업을 시작하고 중지할 수 있습니다.  
  
 각 탭의 옵션에 대한 자세한 내용을 보려면 오른쪽 창에서 해당 탭을 클릭한 다음 메뉴 모음에서 **도움말** 을 클릭합니다. 복제 모니터를 시작하는 방법은 [복제 모니터 시작](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)을 참조하세요.  
  
### <a name="to-view-information-and-perform-tasks-for-a-publisher"></a>게시자에 대한 정보를 보고 태스크를 수행하려면  
  
1.  왼쪽 창에서 게시자 그룹을 확장한 다음 해당 게시자를 클릭합니다.  
  
2.  모든 게시에 대한 정보를 보려면 **게시** 탭을 클릭합니다.  
  
3.  구독에 대한 정보를 보려면 **구독 조사 목록** 탭을 클릭합니다. 다음과 같이 이 탭에서 자세한 정보에 액세스하고 태스크를 수행할 수도 있습니다.  
  
    -   구독과 연결된 에이전트에 대한 자세한 내용을 보려면 해당 구독을 마우스 오른쪽 단추로 클릭한 다음 **자세히 보기**를 클릭합니다.  
  
    -   구독 속성을 보려면 해당 구독을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
    -   밀어넣기 구독을 동기화하려면 해당 구독을 마우스 오른쪽 단추로 클릭한 다음 **동기화 시작**을 클릭합니다.  
  
    -   구독을 다시 초기화하려면 해당 구독을 마우스 오른쪽 단추로 클릭한 다음 **구독 다시 초기화**를 클릭합니다.  
  
4.  에이전트에 대한 정보를 보려면 **에이전트** 탭을 클릭합니다. 이 탭에서 다음과 같이 보다 자세한 정보에 액세스하고 태스크를 수행할 수도 있습니다.  
  
    -   에이전트에 대한 자세한 정보(예: 정보 메시지 및 오류 메시지)를 보려면 에이전트를 마우스 오른쪽 단추로 클릭한 다음 **자세히 보기**를 클릭합니다.  
  
    -   에이전트를 실행하는 작업에 대한 자세한 정보(예: 일정, 자세한 작업 단계 정보 등)를 보려면 에이전트를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
    -   에이전트에 대한 프로필을 관리하려면 에이전트를 마우스 오른쪽 단추로 클릭한 다음 **에이전트 프로필**을 클릭합니다. 자세한 내용은 [복제 에이전트 프로필 작업](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)을 참조하세요.  
  
    -   실행 중이지 않은 에이전트를 시작하려면 에이전트를 마우스 오른쪽 단추로 클릭한 다음 **에이전트 시작**을 클릭합니다.  
  
    -   실행 중인 에이전트를 중지하려면 에이전트를 마우스 오른쪽 단추로 클릭한 다음 **에이전트 중지**를 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [배포자 및 게시자 속성 보기 및 수정](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [복제 모니터링](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
