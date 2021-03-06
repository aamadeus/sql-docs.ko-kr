---
title: 에이전트 프로필(단일 에이전트) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.perfprofileagentname.f1
helpviewer_keywords:
- Agent Profile dialog box
ms.assetid: 22713555-c496-4ce1-8ec7-4ae75cfadca8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4c95d4a8d47c65493fcb2e618a194f37fec9125e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48070939"
---
# <a name="agent-profiles-single-agent"></a>에이전트 프로필(단일 에이전트)
  **에이전트 프로필** 대화 상자를 사용하여 에이전트 프로필을 관리할 수 있습니다. 에이전트 프로필을 사용하면 각 에이전트의 런타임 매개 변수를 편리하게 관리할 수 있습니다. 각 에이전트에는 기본 프로필이 있으며 미리 정의된 프로필이 추가된 에이전트도 있습니다. 예를 들어 병합 에이전트에는 느린 대역폭 연결을 위한 "느린 연결" 프로필이 있습니다. 대부분의 응용 프로그램은 미리 정의된 프로필만으로 충분하지만 사용자 정의 프로필을 만들어 에이전트 동작을 사용자 지정할 수도 있습니다.  
  
## <a name="options"></a>변수  
 **새 에이전트에 대한 기본값**  
 지정한 유형의 에이전트에 대해 작업을 만들 때 사용할 프로필을 선택합니다. 예를 들어 병합 게시에 대한 구독을 여러 개 만들 경우 각 구독의 병합 에이전트 작업은 선택한 프로필을 사용합니다. 기존 작업의 프로필을 변경하려면 프로필을 선택하고 **기존 에이전트 변경**을 클릭합니다.  
  
 **이름**  
 프로필의 이름입니다.  
  
 **형식**  
 프로필 유형: **사용자** (사용자 정의 프로필) 또는 **시스템** (미리 정의된 프로필)입니다.  
  
 **속성 (...)**  
 에이전트 프로필의 각 매개 변수에 사용된 값을 보려면 클릭합니다.  
  
 **새로 만들기**  
 새 프로필을 만들려면 클릭합니다.  
  
 **Delete**  
 사용자 정의 프로필을 선택하고 **삭제** 를 클릭하여 해당 프로필을 삭제합니다. 미리 정의된 프로필은 삭제할 수 없습니다.  
  
 **기존 에이전트 변경**  
 프로필을 선택하고 **기존 에이전트 변경** 을 클릭하여 지정한 유형의 에이전트에 대한 모든 기존 작업에서 선택한 프로필을 사용하도록 지정합니다. 예를 들어 병합 게시에 대한 구독을 여러 개 만들었는데, 프로필을 변경하여 이러한 각 구독에 대한 병합 에이전트 작업에서 **느린 연결 에이전트 프로필**을 사용하도록 지정하려면 해당 프로필을 선택하고 **기존 에이전트 변경**을 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [복제 에이전트 프로필 작업](agents/work-with-replication-agent-profiles.md)   
 [복제 에이전트 개요](agents/replication-agents-overview.md)   
 [복제 에이전트 프로필](agents/replication-agent-profiles.md)  
  
  
