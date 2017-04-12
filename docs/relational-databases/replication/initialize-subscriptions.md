---
title: "구독 초기화 | Microsoft Docs"
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
  - "sql13.rep.newsubwizard.initializesubscriptions.f1"
ms.assetid: 7b170e4e-470d-4828-a9ed-7435b0b03514
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# 구독 초기화
  구독자는 초기화되어야만 복제된 데이터를 받을 수 있습니다. 초기 데이터 집합은 필요 없지만 구독자에는 적어도 복제된 각 개체에 대한 스키마와 복제에 필요한 메타데이터 테이블 및 프로시저가 있어야 합니다.  
  
## 옵션  
 **구독 속성**  
 확인란을 선택 하면 **초기화** 초기 데이터 집합이 필요한 각 구독자에 대 한 열. 확인란 선택을 취소하면 복제 메타데이터 및 프로시저만 초기화됩니다. 스냅숏 없이 구독을 초기화 하는 방법에 대 한 자세한 내용은 참조 [트랜잭션 구독 없이 스냅숏 초기화](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 선택 **즉시** 에서 드롭 다운 목록 상자에서 해당 **초기화할 때** 열의 병합 에이전트 또는 배포 에이전트가 전송 스냅샷 구독자에 파일을이 마법사를 완료 한 후. 에이전트가 다음 실행 일정에 파일을 전송하게 하려면 **첫 번째 동기화 시** 를 선택합니다.  **즉시** 옵션은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]에 대한 끌어오기 구독에 사용할 수 없습니다. 병합 에이전트 및 배포 에이전트는 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]인스턴스에서 실행되지 않으므로 다른 방법으로 구독을 초기화해야 합니다.  
  
> [!NOTE]  
>  마법사에서 배포 에이전트 또는 병합 에이전트에 대해 해당 작업을 시작하려면 배포자에 연결하라는 메시지를 표시할 수 있습니다.  
  
## 참고 항목  
 [끌어오기 구독 만들기](../../relational-databases/replication/create-a-pull-subscription.md)   
 [밀어넣기 구독 만들기](../../relational-databases/replication/create-a-push-subscription.md)   
 [구독 초기화](../../relational-databases/replication/initialize-a-subscription.md)   
 [게시 구독](../../relational-databases/replication/subscribe-to-publications.md)  
  
  