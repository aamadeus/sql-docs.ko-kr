---
title: "2단원: 트랜잭션 게시에 구독 만들기 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "복제 [SQL Server], 자습서"
ms.assetid: 5995b7d2-7c06-46f5-b96c-2bee879bcda2
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# 2단원: 트랜잭션 게시에 구독 만들기
이 단원에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 구독을 만듭니다. 이 단원을 수행하려면 이전 단원인 [1단원: 트랜잭션 복제를 사용하여 데이터 게시](../../relational-databases/replication/lesson-1-publishing-data-using-transactional-replication.md)를 완료해야 합니다.  
  
### 구독을 만들려면  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결하고 해당 서버 노드를 확장한 다음 **복제** 폴더를 확장합니다.  
  
2.  **로컬 게시** 폴더에서 **AdvWorksProductTrans** 게시를 마우스 오른쪽 단추로 클릭한 다음 **새 구독**을 클릭합니다.  
  
    새 구독 마법사가 시작됩니다.  
  
3.  게시 페이지에서 **AdvWorksProductTrans**를 선택한 후 **다음**을 클릭합니다.  
  
4.  배포 에이전트 위치 페이지에서 **배포자에서 모든 에이전트 실행**을 선택한 후 **다음**을 클릭합니다.  
  
5.  구독자 페이지에서 구독자 인스턴스 이름이 표시되지 않는 경우 **구독자 추가**, **SQL Server 구독자 추가**를 차례로 클릭하고 **서버에 연결** 대화 상자에 구독자 인스턴스 이름을 입력한 다음 **연결**을 클릭합니다.  
  
6.  구독자 페이지에서 구독자 서버의 인스턴스 이름을 선택하고 **구독 데이터베이스**에서 **<New Database>**를 선택합니다.  
  
7.  **새 데이터베이스** 대화 상자에서 **데이터베이스 이름** 상자에 **ProductReplica** 를 입력하고 **확인**을 클릭한 후 **다음**을 클릭합니다.  
  
8.  **배포 에이전트 보안** 대화 상자에서 줄임표 단추(**…**)를 클릭하여 **프로세스 계정** 상자에 \<*Machine_Name>***\repl_distribution**을 입력하고 이 계정의 암호를 입력한 다음 **확인**을 클릭하고 **다음**을 클릭합니다.  
  
9. **마침** 을 클릭하여 나머지 페이지의 기본값을 적용하고 마법사를 완료합니다.  
  
### 구독자에서 데이터베이스 권한 설정  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 구독자에 연결하고 **데이터베이스**, **ProductReplica** 및 **보안**을 확장하고 **사용자**를 마우스 오른쪽 단추로 클릭한 다음 **새 사용자**를 선택합니다.  
  
2.  **일반** 페이지에 있는 **사용자 유형** 목록에서 **Windows 사용자**를 선택합니다.  
  
3.  **사용자 이름** 상자를 선택하고 줄임표 단추(...)를 클릭합니다. **선택할 개체 이름을 입력하십시오.** 상자에 <Machine_Name>**\repl_distribution**을 입력하고 **이름 확인**을 클릭한 다음 **확인**을 클릭합니다.  
  
4.  **멤버 자격** 페이지의 **데이터베이스 역할 멤버 자격** 영역에서 **db_owner**를 선택한 다음 **확인**을 클릭하여 사용자를 만듭니다.  
  
### 구독의 동기화 상태를 보려면  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결하고 해당 서버 노드를 확장한 다음 **복제** 폴더를 확장합니다.  
  
2.  **로컬 게시** 폴더에서 **AdvWorksProductTrans** 게시를 확장하고 **ProductReplica** 데이터베이스의 구독을 마우스 오른쪽 단추로 클릭한 다음 **동기화 상태 보기**를 클릭합니다.  
  
    구독의 현재 동기화 상태가 표시됩니다.  
  
3.  **AdvWorksProductTrans**에 해당 구독이 표시되지 않으면 F5 키를 눌러 목록을 새로 고칩니다.  
  
## 다음 단계  
트랜잭션 게시에 구독을 성공적으로 만들었습니다. 이 구독에 대한 배포 에이전트가 계속 실행되므로 구독은 생성될 때 초기화됩니다. 다음 단원에서는 추적 프로그램 토큰을 사용하여 변경 내용이 구독자에 복제되었는지 여부 및 대기 시간을 확인합니다. [Lesson 3: Validating the Subscription and Measuring Latency](../../relational-databases/replication/lesson-3-validating-the-subscription-and-measuring-latency.md)을 참조하세요.  
  
## 참고 항목  
[스냅숏으로 구독 초기화](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[밀어넣기 구독 만들기](../../relational-databases/replication/create-a-push-subscription.md)  
[게시 구독](../../relational-databases/replication/subscribe-to-publications.md)  
  