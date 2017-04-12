---
title: "구독 다시 초기화 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "구독 초기화 [SQL Server 복제], 다시 초기화"
  - "구독 [SQL Server 복제], 다시 초기화"
  - "구독 다시 초기화"
ms.assetid: fb13712b-e7ad-4f1f-b605-4554bad0cb60
caps.latest.revision: 51
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 51
---
# 구독 다시 초기화
  구독을 다시 초기화하면 아티클의 새 스냅숏이 구독자에 적용됩니다. 트랜잭션 및 스냅숏 복제를 사용하면 개별 아티클을 다시 초기화할 수 있으며 병합 복제를 사용하면 모든 아티클을 다시 초기화해야 합니다. 피어 투 피어 트랜잭션 복제 토폴로지의 노드는 다시 초기화할 수 없습니다. 노드에 새로운 데이터 복사본을 유지하려면 해당 노드에서 백업을 복원합니다. 다시 초기화는 다음 두 가지 이유로 인해 발생합니다.  
  
-   구독을 다시 초기화되도록 명시적으로 표시합니다.  
  
-   속성 변경과 같이 다시 초기화가 필요한 동작을 수행합니다. 작업을 다시 초기화 해야 하는 방법에 대 한 자세한 내용은 참조 [변경 게시 및 아티클 속성](../../relational-databases/replication/publish/change-publication-and-article-properties.md)합니다.  
  
 두 경우 모두 다음에 배포 에이전트 또는 병합 에이전트가 실행될 때 최신 스냅숏이 구독자에 적용됩니다. 스냅숏 및 트랜잭션 복제의 경우 다시 초기화가 발생할 때 구독자에서는 수행되었지만 아직 게시자와 동기화되지 않은 변경 내용은 새 스냅숏의 응용 프로그램에서 덮어씁니다.  
  
 병합 복제의 경우 스냅숏이 적용되기 전에 모든 데이터 변경 내용을 구독자에서 업로드하도록 선택할 수 있습니다. 게시자에서 보류 중인 스키마 변경이 구독자에 적용된 다음 스냅숏이 다시 적용되기 전에 마지막 동기화 이후 구독자에서 수행된 모든 업데이트가 게시자로 전파됩니다. 이 동작을 제어 하 여는 **upload_first** 및 **automatic_reinitialization_policy** 속성입니다; 자세한 내용은 참조 [구독 다시 초기화](../../relational-databases/replication/reinitialize-a-subscription.md). SQL Server Management Studio 또는 복제 모니터를 사용 하 여 다시 초기화에 대 한 구독을 표시 하는 경우 제공한 옵션는 **구독 다시 초기화** 먼저 변경 내용을 업로드 하려면 대화 상자입니다.  
  
> [!IMPORTANT]  
>  병합 게시에 매개 변수가 있는 필터를 추가, 삭제 또는 변경할 경우 보류 중인 구독자의 변경 내용을 다시 초기화 중에 게시자로 업로드할 수 없습니다. 보류 중인 변경 내용을 업로드하려면 필터를 변경하기 전에 모든 구독을 동기화하세요.  
  
 구독을 만들 때 구독자에 적용할 초기 스냅숏이 없는 것으로 지정한 후에 해당 구독을 다시 초기화로 표시할 경우 스냅숏이 적용되지 않습니다. 자세한 내용은 참조 [초기화는 Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)합니다.  
  
 **구독을 다시 초기화하려면**  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], 저장 프로시저 또는 RMO(복제 관리 개체)를 사용하여 구독의 모든 아티클을 다시 초기화할 수 있습니다. 스냅숏 및 트랜잭션 게시의 개별 아티클을 다시 초기화하려면 저장 프로시저를 사용해야 합니다. 자세한 내용은 [Reinitialize a Subscription](../../relational-databases/replication/reinitialize-a-subscription.md)을 참조하세요.  
  
## 참고 항목  
 [구독 초기화](../../relational-databases/replication/initialize-a-subscription.md)   
 [구독 만료 및 비활성화](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  