---
title: "게시 속성, 일반 | Microsoft Docs"
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
  - "sql13.rep.newpubwizard.pubproperties.general.f1"
ms.assetid: 7912362f-c4d6-4f60-bd39-dee1f656ed18
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# 게시 속성, 일반
  **게시 속성** 대화 상자의 **일반** 페이지에는 이름, 설명 및 구독 만료 정책을 포함하여 게시에 대한 기본 정보가 들어 있습니다.  
  
## 옵션  
 **이름**  
 게시의 이름입니다(읽기 전용).  
  
 **데이터베이스**  
 게시 데이터베이스의 이름입니다(읽기 전용).  
  
 **설명**  
 게시에 대한 설명입니다.  
  
 **형식**  
 게시의 유형입니다(읽기 전용).  
  
 **구독 만료**  
 구독 만료에 대 한 옵션 중 하나를 선택: **구독이 만료 되지는** 또는 **구독이 만료**, 지정 된 시간에 마침표 (**간격**).  
  
 스냅숏 및 트랜잭션 게시의 경우 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 은 기본값인 **구독이 만료되지는 않지만 다시 초기화될 때까지 비활성화될 수 있습니다**를 사용하는 것을 권장합니다.  
  
 병합 게시의 경우 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 은 기본값인 **구독이 다음 시간 내에 동기화되지 않으면 만료되어 삭제될 수 있습니다** 를 사용하고 **간격**에 가능한 낮은 값을 설정하는 것을 권장합니다. 구독 만료 기간이 증가할수록 저장된 메타데이터의 양도 증가하므로 성능에 영향을 줄 수 있습니다. 연결을 끊거나 대량의 메타데이터를 저장 및 처리하는 잠재적 성능 문제에 대해 연장된 기간 동안 동기화하지 않는 간단한 방법으로 구독자 간에 균형을 유지합니다.  
  
 자세한 내용은 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)를 참조하세요.  
  
 **호환성 수준**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에 사용 합니다. 병합 게시에만 해당 합니다. 이 게시와 동기화하는 구독자에 필요한 가장 낮은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전을 선택합니다. 호환성 수준 결정과 관련된 여러 가지 규칙이 있습니다.  
  
## 참고 항목  
 [게시 만들기](../../relational-databases/replication/publish/create-a-publication.md)   
 [게시 속성 보기 및 수정](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [데이터 및 데이터베이스 개체 게시](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  