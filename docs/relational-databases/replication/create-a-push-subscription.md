---
title: "밀어넣기 구독 만들기 | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "밀어넣기 구독 [SQL Server 복제], 만들기"
  - "병합 복제 구독 [SQL Server 복제], 밀어넣기 구독"
  - "구독 [SQL Server 복제], 밀어넣기"
  - "스냅숏 복제 [SQL Server], 구독"
  - "트랜잭션 복제, 구독"
ms.assetid: adfbbc61-58d1-4330-9ad6-b14ab1142e2b
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# 밀어넣기 구독 만들기
  이 항목에서 밀어넣기 구독을 만드는 방법에 설명 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용 하 여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], 또는 관리 개체 RMO (복제). 이외에 대 한 밀어넣기 구독을 만드는 방법에 대 한 내용은[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구독자 참조 [비-SQL Server 구독자에 대 한 구독을 만들](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)합니다.  
  
 
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
 새 구독 마법사를 사용하여 게시자 또는 구독자에서 밀어넣기 구독을 만듭니다. 마법사의 페이지에 따라 다음을 수행하세요.  
  
-   게시자와 게시를 지정합니다.  
  
-   복제 에이전트가 실행될 위치를 선택합니다. 밀어넣기 구독을 선택 **배포자 (밀어넣기 구독의 경우)에서 모든 에이전트 실행** 에 **배포 에이전트 위치** 페이지 또는 **병합 에이전트 위치** 게시의 유형에 따라 페이지입니다.  
  
-   구독자와 구독 데이터베이스를 지정합니다.  
  
-   복제 에이전트에서 설정한 연결에 사용할 로그인과 암호를 지정합니다.  
  
    -   스냅숏 및 트랜잭션 게시에 대한 구독의 경우 **배포 에이전트 보안** 페이지에서 자격 증명을 지정합니다.  
  
    -   병합 게시에 대한 구독의 경우 **병합 에이전트 보안** 페이지에서 자격 증명을 지정합니다.  
  
     각 에이전트에 필요한 사용 권한에 대 한 정보를 참조 하십시오. [복제 에이전트 보안 모델](../../relational-databases/replication/security/replication-agent-security-model.md)합니다.  
  
-   동기화 일정과 구독자의 초기화 시기를 지정합니다.  
  
-   게시 유형 및 매개 변수가 있는 필터링 값 등의 병합 게시에 대한 추가 옵션을 지정합니다.  
  
-   구독자가 게시자의 변경 내용을 즉시 커밋할지 아니면 큐에 쓸지 여부, 구독자에서 게시자로 연결하는 데 사용할 자격 증명 등, 트랜잭션 게시에 대해 구독 업데이트를 허용하는 추가 옵션을 지정합니다.  
  
-   경우에 따라 구독을 스크립팅합니다.  
  
#### 게시자에서 밀어넣기 구독을 만들려면  
  
1.   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.  
  
2.  **복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.  
  
3.  하나 이상의 구독을 만들고을 클릭 한 다음 원하는 게시를 마우스 오른쪽 단추로 클릭 **새 구독**합니다.  
  
4.  새 구독 마법사의 페이지를 완료합니다.  
  
#### 구독자에서 밀어넣기 구독을 만들려면  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 구독자에 연결한 다음 해당 서버 노드를 확장합니다.  
  
2.  **복제** 폴더를 확장합니다.  
  
3.  마우스 오른쪽 단추로 클릭는 **로컬 구독** 폴더를 마우스 클릭 한 다음 **새 구독**합니다.  
  
4.  에 **게시** 선택 새 구독 마법사의 페이지 **\< SQL Server 게시자 찾기>** 또는 **\< Oracle 게시자 찾기>** 에서 **게시자** 드롭 다운 목록입니다.  
  
5.  **서버에 연결** 대화 상자에서 게시자에 연결합니다.  
  
6.  **게시** 페이지에서 게시를 선택합니다.  
  
7.  새 구독 마법사의 페이지를 완료합니다.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
 밀어넣기 구독은 복제 저장 프로시저를 사용하여 프로그래밍 방식으로 만들 수 있습니다. 사용되는 저장 프로시저는 구독이 속한 게시 유형에 따라 달라집니다.  
  
> **중요!** 가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다. 자격 증명을 스크립트 파일에 저장해야 하는 경우에는 파일에 무단으로 액세스하지 못하도록 보안을 설정해야 합니다.  
  
#### 스냅숏 또는 트랜잭션 게시에 밀어넣기 구독을 만들려면  
  
1.  게시 데이터베이스의 게시자에서 게시를 실행 하 여 밀어넣기 구독을 지원 하는지 확인 [sp_helppublication](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)합니다.  
  
    -   하는 경우의 값 **allow_push** 는 **1**, 밀어넣기 구독을 지원 합니다.  
  
    -   하는 경우의 값 **allow_push** 는 **0**, 실행 [sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), 로 지정 하 여 **allow_push** 에 대 한 **@property** 및 **true** 에 대 한 **@value**합니다.  
  
2.  게시 데이터베이스의 게시자에서 실행 [sp_addsubscription](https://msdn.microsoft.com/library/ms181702.aspx)합니다. 지정 **@publication**, **@subscriber** 및 **@destination_db**합니다. 값을 지정 **푸시** 에 대 한 **@subscription_type**합니다. 구독을 업데이트 하는 방법에 대 한 정보를 참조 하십시오. [트랜잭션 게시에 업데이트할 수 있는 구독을 만들](https://msdn.microsoft.com/library/ms152769.aspx)합니다.  
  
3.  게시 데이터베이스의 게시자에서 실행 [sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)합니다. 다음을 지정합니다.  
  
    -    **@subscriber**, **@subscriber_db**, 및 **@publication** 매개 변수입니다.  
  
    -   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 자격 증명에 대 한 배포자에서 배포 에이전트가 실행 되는 **@job_login** 및 **@job_password**합니다.  
  
        > **참고:** 항상 Windows 통합 인증을 사용 하 여 만든 연결으로 지정 된 Windows 자격 증명을 사용 하 여 **@job_login** 및 **@job_password**합니다. 배포 에이전트는 항상 Windows 통합 인증을 사용하여 배포자에 대한 로컬 연결을 만듭니다. 기본적으로 에이전트는 Windows 통합 인증을 사용하여 구독자에 연결합니다.  
  
    -   (선택 사항) 값이 **0** 에 대 한 **@subscriber_security_mode** 및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 대 한 로그인 정보 **@subscriber_login** 및 **@subscriber_password**합니다. 구독자에 연결할 때 SQL Server 인증을 사용해야 하는 경우 이러한 매개 변수를 지정합니다.  
  
    -   이 구독에 대한 배포 에이전트 작업 일정. 자세한 내용은 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)을 참조하세요.  
  
    > **중요!!** 모든 매개 변수에 대해 제공 된 값 원격 배포자가 있는 게시자에서 밀어넣기 구독을 만드는 경우 포함 하 여 *job_login* 및 *job_password*, 를 일반 텍스트로 배포자에 보내집니다. 이 저장 프로시저를 실행하기 전에 게시자와 해당 원격 배포자 간 연결을 암호화해야 합니다. 자세한 내용은 [데이터베이스 엔진에 암호화 연결 사용&#40;SQL Server 구성 관리자&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)을 참조하세요.  
  
#### 병합 게시에 밀어넣기 구독을 만들려면  
  
1.  게시 데이터베이스의 게시자에서 게시를 실행 하 여 밀어넣기 구독을 지원 하는지 확인 [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)합니다.  
  
    -   하는 경우의 값 **allow_push** 는 **1**, 게시에서 밀어넣기 구독을 지원 합니다.  
  
    -   하는 경우의 값 **allow_push** 없는 **1**, 실행 [sp_changemergepublication](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), 로 지정 하 여 **allow_push** 에 대 한 **@property** 및 **true** 에 대 한 **@value**합니다.  
  
2.  게시 데이터베이스의 게시자에서 실행 [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md), 다음 매개 변수를 지정 합니다.  
  
    -   **@publication**- 게시의 이름입니다.  
  
    -   **@subscriber_type**합니다. 클라이언트 구독에 **local** 을 지정하고 서버 구독에 **global**을 지정합니다.  
  
    -   **@subscription_priority**합니다. 서버 구독에 대 한 구독에 대 한 우선 순위 지정 (**0.00** 에 **99.99**).  
  
         자세한 내용은 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)을 참조하세요.  
  
3.  게시 데이터베이스의 게시자에서 실행 [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md)합니다. 다음을 지정합니다.  
  
    -   **@subscriber**, **@subscriber_db**, 및 **@publication** 매개 변수입니다.  
  
    -   에 대 한 배포자에서 병합 에이전트가 실행 되는 Windows 자격 증명 **@job_login** 및 **@job_password**합니다.  
  
        > **참고:**  항상 Windows 통합 인증을 사용 하 여 만든 연결으로 지정 된 Windows 자격 증명을 사용 하 여 **@job_login** 및 **@job_password**합니다. 병합 에이전트는 항상 Windows 통합 인증을 사용하여 배포자에 로컬로 연결합니다. 기본적으로 에이전트는 Windows 통합 인증을 사용하여 구독자에 연결합니다.  
  
    -   (선택 사항) 값이 **0** 에 대 한 **@subscriber_security_mode** 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 대 한 로그인 정보 **@subscriber_login** 및 **@subscriber_password**합니다. 구독자에 연결할 때 SQL Server 인증을 사용해야 하는 경우 이러한 매개 변수를 지정합니다.  
  
    -   (선택 사항) 값이 **0** 에 대 한 **@publisher_security_mode** 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 대 한 로그인 정보 **@publisher_login** 및 **@publisher_password**합니다. 구독자에 연결할 때 SQL Server 인증을 사용해야 하는 경우 이러한 값을 지정합니다.  
  
    -   이 구독에 대한 병합 에이전트 작업 일정. 자세한 내용은 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)을 참조하세요.  
  
    > **중요!!** 모든 매개 변수에 대해 제공 된 값 원격 배포자가 있는 게시자에서 밀어넣기 구독을 만드는 경우 포함 하 여 *job_login* 및 *job_password*, 를 일반 텍스트로 배포자에 보내집니다. 이 저장 프로시저를 실행하기 전에 게시자와 해당 원격 배포자 간 연결을 암호화해야 합니다. 자세한 내용은 [데이터베이스 엔진에 암호화 연결 사용&#40;SQL Server 구성 관리자&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)을 참조하세요.  
  
###  <a name="TsqlExample"></a> 예(Transact-SQL)  
 다음은 트랜잭션 게시에 밀어넣기 구독을 만드는 예입니다. 로그인 및 암호 값은 **sqlcmd** 스크립팅 변수를 사용하여 런타임 시 제공됩니다.  
  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../relational-databases/replication/codesnippet/tsql/create-a-push-subscription_1.sql)]  
  
 다음은 병합 게시에 밀어넣기 구독을 만드는 예입니다. 로그인 및 암호 값은 **sqlcmd** 스크립팅 변수를 사용하여 런타임 시 제공됩니다.  
  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/create-a-push-subscription_2.sql)]  
  
##  <a name="RMOProcedure"></a> RMO(복제 관리 개체) 사용  
 RMO(복제 관리 개체)를 사용하여 프로그래밍 방식으로 밀어넣기 구독을 만들 수 있습니다. _밀어넣기 구독을 만들 때 사용하는 RMO 클래스는 구독을 만드는 게시 유형에 따라 달라집니다.  
  
> **중요!** 가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다. 자격 증명을 저장해야 하는 경우 [Windows .NET Framework에서 제공하는](http://go.microsoft.com/fwlink/?LinkId=34733) 암호화 서비스 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 를 사용합니다.  
  
#### 스냅숏 또는 트랜잭션 게시에 밀어넣기 구독을 만들려면  
  
1.  사용 하 여 게시자에 대 한 연결을 만들기는 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스입니다.  
  
2.  인스턴스를 만들고는 <xref:Microsoft.SqlServer.Replication.TransPublication> 1 단계에서 만든 게시자 연결을 사용 하 여 클래스입니다. 지정 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>, 및 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>합니다.  
  
3.  호출 된 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드. 이 메서드가 **false**를 반환하는 경우 2단계에서 지정한 속성이 올바르지 않거나 서버에 게시가 없습니다.  
  
4.  비트 논리 AND를 수행 (**&** Visual C# 및 **및** Visual basic에서) 간에 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 속성 및 <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. 결과가 <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, 설정, <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 비트 논리 OR 연산자의 결과를 (**|** Visual C# 및 **또는** Visual Basic의) 간의 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 및 <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. 그런 다음 호출 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 밀어넣기 구독을 사용 하도록 합니다.  
  
5.  구독 데이터베이스가 없는 경우 사용 하 여 만듭니다.는 <xref:Microsoft.SqlServer.Management.Smo.Database> 클래스입니다. 자세한 내용은 참조 [생성, 변경, 및 데이터베이스 제거](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md)합니다.  
  
6.  인스턴스를 만들고는 <xref:Microsoft.SqlServer.Replication.TransSubscription> 클래스입니다.  
  
7.  다음 구독 속성을 설정합니다.  
  
    -    <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 에 대해 1 단계에서 만든 게시자를 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>합니다.  
  
    -   에 대 한 구독 데이터베이스의 이름을 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>합니다.  
  
    -   에 대 한 구독자의 이름 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>합니다.  
  
    -   에 대 한 게시 데이터베이스의 이름 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>합니다.  
  
    -   에 대 한 게시의 이름 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>합니다.  
  
    -   <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> 및 <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> 또는 <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> 필드의 <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> 에 대 한 자격 증명을 제공 하는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 배포 에이전트가 배포자에서 실행 되는 Windows 계정입니다. 이 계정은 Windows 인증을 사용하여 배포자에 대한 로컬 연결 및 원격 연결을 만드는 데 사용됩니다.  
  
        > **그러나 참고:** 설정을 <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> 의 멤버에 의해 구독이 만들어질 때 필요 하지 않습니다는 **sysadmin** 고정 서버 역할, 것이 좋습니다. 이 경우 에이전트는 SQL Server 에이전트 계정을 가장합니다. 자세한 내용은 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)을(를) 참조하세요.  
  
    -   (선택 사항) 값이 **true** (기본값)에 대 한 <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> 구독을 동기화 하는 데 사용 되는 에이전트 작업을 만듭니다. **false**를 지정한 경우 구독은 프로그래밍 방식으로만 동기화할 수 있습니다.  
  
    -   (선택 사항) 설정의 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> 및 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> 또는 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> 필드의 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> SQL Server 인증을 사용 하 여 구독자에 연결할 때.  
  
8.  호출 된 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> 메서드.  
  
    > **중요 한!!**모든 속성에 제공 된 값 원격 배포자가 있는 게시자에서 밀어넣기 구독을 만드는 경우 포함 하 여 <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>, 를 일반 텍스트로 배포자에 보내집니다. 게시자와 호출 하기 전에 해당 원격 배포자 간 연결을 암호화 해야는 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> 메서드. 자세한 내용은 [데이터베이스 엔진에 암호화 연결 사용&#40;SQL Server 구성 관리자&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)을 참조하세요.  
  
#### 병합 게시에 밀어넣기 구독을 만들려면  
  
1.  사용 하 여 게시자에 대 한 연결을 만들기는 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스입니다.  
  
2.  인스턴스를 만들고는 <xref:Microsoft.SqlServer.Replication.MergePublication> 1 단계에서 만든 게시자 연결을 사용 하 여 클래스입니다. 지정 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>, 및 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>합니다.  
  
3.  호출 된 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드. 이 메서드가 **false**를 반환하는 경우 2단계에서 지정한 속성이 올바르지 않거나 서버에 게시가 없습니다.  
  
4.  비트 논리 AND를 수행 (**&** Visual C# 및 **및** Visual basic에서) 간에 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 속성 및 <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. 결과가 <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, 설정, <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 비트 논리 OR 연산자의 결과를 (**|** Visual C# 및 **또는** Visual Basic의) 간의 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 및 <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. 그런 다음 호출 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 밀어넣기 구독을 사용 하도록 합니다.  
  
5.  구독 데이터베이스가 없는 경우 사용 하 여 만듭니다.는 <xref:Microsoft.SqlServer.Management.Smo.Database> 클래스입니다. 자세한 내용은 참조 [생성, 변경, 및 데이터베이스 제거](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md)합니다.  
  
6.  인스턴스를 만들고는 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 클래스입니다.  
  
7.  다음 구독 속성을 설정합니다.  
  
    -    <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 에 대해 1 단계에서 만든 게시자를 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>합니다.  
  
    -   에 대 한 구독 데이터베이스의 이름을 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>합니다.  
  
    -   에 대 한 구독자의 이름 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>합니다.  
  
    -   에 대 한 게시 데이터베이스의 이름 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>합니다.  
  
    -   에 대 한 게시의 이름 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>합니다.  
  
    -   <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> 및 <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> 또는 <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> 필드의 <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> 에 대 한 자격 증명을 제공 하는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 병합 에이전트가 배포자에서 실행 되는 Windows 계정입니다. 이 계정은 Windows 인증을 사용하여 배포자에 대한 로컬 연결 및 원격 연결을 만드는 데 사용됩니다.  
  
        > **그러나 참고:** 설정을 <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> 의 멤버에 의해 구독이 만들어질 때 필요 하지 않습니다는 **sysadmin** 고정 서버 역할, 것이 좋습니다. 이 경우 에이전트는 SQL Server 에이전트 계정을 가장합니다. 자세한 내용은 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)을(를) 참조하세요.  
  
    -   (선택 사항) 값이 **true** (기본값)에 대 한 <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> 구독을 동기화 하는 데 사용 되는 에이전트 작업을 만듭니다. **false**를 지정한 경우 구독은 프로그래밍 방식으로만 동기화할 수 있습니다.  
  
    -   (선택 사항) 설정의 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> 및 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> 또는 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> 필드의 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> SQL Server 인증을 사용 하 여 구독자에 연결할 때.  
  
    -   (선택 사항) 설정의 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> 및 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> 또는 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> 필드의 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> SQL Server 인증을 사용 하 여 게시자에 연결할 때.  
  
8.  호출 된 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> 메서드.  
  
    > **중요!**  모든 속성에 제공 된 값 원격 배포자가 있는 게시자에서 밀어넣기 구독을 만드는 경우 포함 하 여 <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>, 를 일반 텍스트로 배포자에 보내집니다. 게시자와 호출 하기 전에 해당 원격 배포자 간 연결을 암호화 해야는 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> 메서드. 자세한 내용은 [데이터베이스 엔진에 암호화 연결 사용&#40;SQL Server 구성 관리자&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)을 참조하세요.  
  
###  <a name="PShellExample"></a> 예(RMO)  
 다음은 트랜잭션 게시에 _새 밀어넣기 구독을 만드는 예입니다. 배포 에이전트 작업을 실행하는 데 사용되는 Windows 계정 자격 증명은 런타임에 전달됩니다.  
  
 [!code-csharp[HowTo#rmo_CreateTranPushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranPushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranpushsub)]  
  
 다음은 병합 게시에 새 밀어넣기 구독을 만드는 예입니다. 병합 에이전트 작업을 실행하는 데 사용되는 Windows 계정 자격 증명은 런타임에 전달됩니다.  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## 관련 항목:  
 [밀어넣기 구독 속성 보기 및 수정](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [복제 보안을 위한 최선의 구현 방법](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [게시 만들기](../../relational-databases/replication/publish/create-a-publication.md)   
 [복제 관리 개체 개념](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [밀어넣기 구독 동기화](../../relational-databases/replication/synchronize-a-push-subscription.md)   
 [게시 구독](../../relational-databases/replication/subscribe-to-publications.md)   
 [스크립팅 변수와 함께 sqlcmd 사용](../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)  
  
  