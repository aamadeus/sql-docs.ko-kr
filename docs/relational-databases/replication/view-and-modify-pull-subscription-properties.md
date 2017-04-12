---
title: "끌어오기 구독 속성 보기 및 수정 | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "구독 수정"
  - "복제 속성 보기"
  - "복제 속성 수정, 끌어오기 구독"
  - "끌어오기 구독 [SQL Server 복제], 수정"
  - "구독 [SQL Server 복제], 끌어오기"
  - "끌어오기 구독 [SQL Server 복제], 속성"
  - "구독 수정, SQL Server Management Studio"
ms.assetid: 1601e54f-86f0-49e8-b023-87a5d1def033
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# 끌어오기 구독 속성 보기 및 수정
  이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 끌어오기 구독 속성을 보고 수정하는 방법에 대해 설명합니다.  
  
 **항목 내용**  
  
-   **끌어오기 구독 속성을 보고 수정하려면:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [RMO(복제 관리 개체)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
 게시자 나 구독자에서 끌어오기 구독 속성 보기는 **구독 속성-\< 게시자>: \< PublicationDatabase>** 대화 상자에서 사용할 수 있는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 구독자에서 더 많은 속성을 볼 수 있으며 구독자에서 속성을 수정할 수 있습니다. 복제 모니터에서 사용 가능한 **모든 구독** 탭의 게시자에서 속성을 볼 수도 있습니다. 복제 모니터를 시작 하는 방법에 대 한 정보를 참조 하십시오. [복제 모니터 시작](../../relational-databases/replication/monitor/start-the-replication-monitor.md)합니다.  
  
#### Management Studio의 게시자에서 끌어오기 구독 속성을 보려면  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.  
  
2.  **복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.  
  
3.  적절 한 게시를 확장 하 고 구독을 마우스 오른쪽 단추로 클릭 한 다음 **속성이**.  
  
4.  속성을 점검한 다음 **확인**을 클릭합니다.  
  
#### Management Studio의 구독자에서 끌어오기 구독 속성을 보고 수정하려면  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 구독자에 연결한 다음 해당 서버 노드를 확장합니다.  
  
2.  **복제** 폴더를 확장한 다음 **로컬 구독** 폴더를 확장합니다.  
  
3.  구독을 마우스 오른쪽 단추로 클릭 하 고 누른 다음 **속성이**.  
  
4.  필요한 경우 속성을 수정한 다음 **확인**을 클릭합니다.  
  
#### 복제 모니터의 게시자에서 끌어오기 구독 속성을 보려면  
  
1.  복제 모니터에서 왼쪽 창의 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.  
  
2.  **모든 구독** 탭을 클릭합니다.  
  
3.  구독을 마우스 오른쪽 단추로 클릭 하 고 누른 다음 **속성이**.  
  
4.  속성을 점검한 다음 **확인**을 클릭합니다.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
 끌어오기 구독은 수정할 수 있으며 속성은 복제 저장 프로시저를 사용하여 프로그래밍 방식으로 액세스할 수 있습니다. 사용되는 저장 프로시저는 구독이 속한 게시 유형에 따라 달라집니다.  
  
#### 스냅숏 또는 트랜잭션 게시에 대한 끌어오기 구독의 속성을 보려면  
  
1.  구독자에서 실행 [sp_helppullsubscription](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md). 지정한 **@publisher**, **@publisher_db**, 및 **@publication**. 이렇게 하면 구독자의 시스템 테이블에 저장된 구독에 대한 정보가 반환됩니다.  
  
2.  구독자에서 실행 [sp_helpsubscription_properties](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md). 지정 **@publisher**, **@publisher_db**, **@publication**, 및 다음 중 하나에 대 한 값이 **@publication_type**.  
  
    -   **0** -구독이 트랜잭션 게시에 속합니다.  
  
    -   **1** -구독이 스냅숏 게시에 속합니다.  
  
3.  게시자에서 실행 [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md). **@publication** 및 **@subscriber**를 지정합니다.  
  
4.  게시자에서 실행 [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), 지정, **@subscriber**. 이렇게 하면 구독자에 대한 정보가 표시됩니다.  
  
#### 스냅숏 또는 트랜잭션 게시에 대한 끌어오기 구독의 속성을 변경하려면  
  
1.  구독자에서 실행 [sp_change_subscription_properties](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md), 지정, **@publisher**, **@publisher_db**, **@publication**, 의 값 **0** (트랜잭션) 또는 **1** (스냅샷)에 대 한 **@publication_type**, 구독 속성으로 변경 하 고, **@property**, 및 새 값으로 **@value**.  
  
2.  (선택 사항) 구독 데이터베이스의 구독자에서 실행 [sp_changesubscriptiondtsinfo](../../relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql.md). 에 대 한 배포 에이전트 작업의 ID를 지정 합니다. **@jobid**, 를 선택 하 고 다음 데이터 변환 서비스 (DTS) 패키지 속성:  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     이렇게 하면 구독의 DTS 패키지 속성이 변경됩니다.  
  
    > [!NOTE]  
    >  작업을 실행 하 여 ID를 가져올 수 [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md).  
  
#### 병합 게시에 대한 끌어오기 구독의 속성을 보려면  
  
1.  구독자에서 실행 [sp_helpmergepullsubscription](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md). 지정한 **@publisher**, **@publisher_db**, 및 **@publication**.  
  
2.  구독자에서 실행 [sp_helpsubscription_properties](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md). 지정한 **@publisher**, **@publisher_db**, **@publication**, 및 2에 대 한 **@publication_type**.  
  
3.  게시자에서 실행 [sp_helpmergesubscription](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md) 구독 정보를 표시 합니다. 특정 가입 정보를 반환 하려면 지정 해야 **@publication**, **@subscriber**, 의 값과 **풀** 에 **@subscription_type**.  
  
4.  게시자에서 실행 [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), 지정, **@subscriber**. 이렇게 하면 구독자에 대한 정보가 표시됩니다.  
  
#### 병합 게시에 대한 끌어오기 구독의 속성을 변경하려면  
  
1.  구독자에서 실행 [sp_changemergepullsubscription](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md). 지정 **@publication**, **@publisher**, **@publisher_db**, 로 변경 하 고 구독 속성, **@property**, 및 새 값으로 **@value**.  
  
##  <a name="RMOProcedure"></a> RMO(복제 관리 개체) 사용  
 끌어오기 구독 속성을 보거나 수정하는 데 사용되는 RMO 클래스는 끌어오기 구독을 구독하는 게시 유형에 따라 다릅니다.  
  
#### 스냅숏 또는 트랜잭션 게시에 대한 끌어오기 구독의 속성을 보거나 수정하려면  
  
1.  구독자에 대 한 연결을 사용 하 여 만들는 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스입니다.  
  
2.  인스턴스를 만들고 해당 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 클래스입니다.  
  
3.  설정 된 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, 및 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 속성입니다.  
  
4.  단계 1에 대 한 연결을 설정 하면 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성입니다.  
  
5.  호출 하면 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 개체의 속성을 가져오는 방법. 이 메서드가 **false**를 반환하는 경우 3단계에서 구독 속성이 잘못 정의되었거나 서버에 구독이 없는 것입니다.  
  
6.  (선택 사항) 중 하나의 속성을 변경 하려면 새 값을 설정는 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 속성을 설정할 수 있으며 다음 호출 하는 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 방법.  
  
7.  (선택 사항) 새로운 설정을 보려면 호출에서 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 문서에 대 한 속성을 다시 로드 하는 방법.  
  
8.  모든 연결을 닫습니다.  
  
#### 병합 게시에 대한 끌어오기 구독의 속성을 보거나 수정하려면  
  
1.  구독자에 대 한 연결을 사용 하 여 만들는 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스입니다.  
  
2.  인스턴스를 만들고 해당 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 클래스입니다.  
  
3.  설정 된 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, 및 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 속성입니다.  
  
4.  단계 1에 대 한 연결을 설정 하면 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성입니다.  
  
5.  호출 하면 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 개체의 속성을 가져오는 방법. 이 메서드가 **false**를 반환하는 경우 3단계에서 구독 속성이 잘못 정의되었거나 서버에 구독이 없는 것입니다.  
  
6.  (선택 사항) 중 하나의 속성을 변경 하려면 새 값을 설정는 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 속성을 설정할 수 있으며 다음 호출 하는 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 방법.  
  
7.  (선택 사항) 새로운 설정을 보려면 호출에서 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 문서에 대 한 속성을 다시 로드 하는 방법.  
  
8.  모든 연결을 닫습니다.  
  
## 참고 항목  
 [정보를 보고 가입 & #40;에 대 한 작업을 수행 합니다. 복제 모니터 & #41.](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [복제 보안을 위한 최선의 구현 방법](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [게시 구독](../../relational-databases/replication/subscribe-to-publications.md)  
  
  