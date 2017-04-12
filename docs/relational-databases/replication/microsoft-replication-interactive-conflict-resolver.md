---
title: "Microsoft 복제 상호 충돌 해결 프로그램 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.replconflictviewer.interactiveresolver.f1"
ms.assetid: d3d4a480-782b-4b1d-b839-565c8cf6cb24
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Microsoft 복제 상호 충돌 해결 프로그램
  상호 충돌 해결 프로그램은 Windows 동기화 관리자로 동기화하는 병합 구독에 사용할 수 있습니다. 상호 충돌 해결 프로그램을 사용하여 데이터 충돌 결과를 확인, 비교, 편집 및 선택할 수 있습니다. 또한 복제에는 충돌 결과를 커밋한 다음 충돌 결과를 보고 수정할 수 있는 충돌 뷰어가 포함되어 있습니다. 상호 충돌 해결 프로그램을 사용하여 동기화 중에 결과를 선택할 수 있습니다.  
  
> [!NOTE]  
>  논리적 레코드와 관련된 충돌은 대화형 해결 프로그램에 표시되지 않습니다. 이러한 충돌에 대한 정보를 보려면 복제 저장 프로시저를 사용합니다. 자세한 내용은 참조 [병합 게시 및 #40;에 대 한 충돌 정보 보기 복제 TRANSACT-SQL 프로그래밍 & #41;](../../relational-databases/replication/view conflict information for merge publications.md)합니다.  
  
## 옵션  
 **열 이름**  
 테이블에 있는 모든 열의 이름입니다. 하나 이상의 열에 충돌하는 데이터가 있을 수 있습니다. 충돌하는 열에 상관없이 적용되는 전체 행이 무시되는 전체 행을 덮어씁니다.  
  
 **권장 해결 방법**  
 해당 아티클에 대한 충돌 해결 프로그램에서 제공하는 권장 해결 방법입니다.  
  
 **게시자**  
 게시자의 데이터 값입니다.  
  
 **구독자**  
 구독자의 데이터 값입니다.  
  
 **제안 허용**, **게시자 허용**, 및 **구독자 허용**  
 충돌 시 게시자와 구독자 중 어떤 것을 무시하는지에 따라 게시자 또는 구독자에 적용되는 행을 허용하려면 클릭합니다. 충돌 시 게시자를 무시할 경우 다른 모든 구독자는 다음에 게시자와 동기화할 때 적용되는 행을 받습니다.  
  
 **남아 있는 충돌 자동 해결**  
 해당 아티클에 대한 충돌 해결 프로그램에서 제공하는 권장 해결 방법을 사용하여 남아 있는 충돌을 해결합니다.  
  
 **나중에 참조하도록 이 충돌 정보 기록**  
 시스템 테이블에 충돌 정보를 자세히 기록합니다.  
  
## 참고 항목  
 [대화형 충돌 해결](../../relational-databases/replication/merge/interactive-conflict-resolution.md)   
 [보기 및 병합 게시 및 #40;에 대 한 데이터 충돌 해결 SQL Server Management Studio & #41;](../../relational-databases/replication/view and resolve data conflicts for merge publications.md)   
 [Windows 동기화 관리자 & #40;를 사용 하 여 구독 동기화 Windows 동기화 관리자 & #41;](../../relational-databases/replication/synchronize a subscription using windows synchronization manager.md)   
 [고급 병합 복제 충돌 감지 및 해결](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  