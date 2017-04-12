---
title: "아티클 정의 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "아티클 [SQL Server 복제], 정의"
  - "sp_addmergearticle"
  - "아티클 추가"
  - "sp_addarticle"
  - "아티클 [SQL Server 복제], 추가"
ms.assetid: 220584d8-b291-43ae-b036-fbba3cc07a2e
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# 아티클 정의
  이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 아티클을 정의하는 방법에 대해 설명합니다.  
  
 **항목 내용**  
  
-   **시작하기 전에:**  
  
     [제한 사항](#Restrictions)  
  
     [보안](#Security)  
  
-   **아티클을 정의하려면:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [RMO(복제 관리 개체)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전 주의 사항  
  
###  <a name="Restrictions"></a> 제한 사항  
  
-   아티클 이름에는 %, *, [,], |, :, ", ? 등의 문자를 포함할 수 없습니다. , ' , \ , / , \< , >. 이러한 문자를 포함하는 데이터베이스 개체를 복제하려면 개체 이름과 다른 아티클 이름을 지정해야 합니다.  
  
##  <a name="Security"></a> 보안  
 가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다. 자격 증명을 저장해야 하는 경우 [Windows .NET Framework에서 제공하는](http://go.microsoft.com/fwlink/?LinkId=34733) 암호화 서비스 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 를 사용합니다.  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
 새 게시 마법사를 사용하여 게시를 만들고 아티클을 정의할 수 있습니다. 게시를 만든 후 속성 보기 및 수정 게시에는 **게시 속성-\< 게시>** 대화 상자입니다. Oracle 데이터베이스에서 게시를 만드는 방법에 대 한 정보를 참조 하십시오. [Oracle 데이터베이스에서 게시를 만들](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)합니다.  
  
#### 게시를 만들고 아티클을 정의하려면  
  
1.   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.  
  
2.  확장 된 **복제** 폴더 및 마우스 오른쪽 단추로 **로컬 게시** 폴더입니다.  
  
3.  **새 게시**를 클릭합니다.  
  
4.  새 게시 마법사의 페이지에 따라 다음을 수행하세요.  
  
    -   서버에 배포가 구성되어 있지 않은 경우 배포자를 지정합니다. 배포를 구성 하는 방법에 대 한 자세한 내용은 참조 [게시 및 배포 구성](../../../relational-databases/replication/configure-publishing-and-distribution.md)합니다.  
  
         지정할 경우에 **배포자** 페이지입니다 (로컬 배포자) 자체 배포자로 게시자 서버는 역할 및 배포자, 새 게시 마법사는 서버를 구성 하는 대로 서버 구성 되지 않았습니다. **스냅숏 폴더** 페이지에서 배포자에 대해 기본 스냅숏 폴더를 지정하게 됩니다. 스냅숏 폴더는 공유하도록 지정된 디렉터리일 뿐이며 이 폴더에 읽기/쓰기 작업을 수행하려면 에이전트에게 충분한 액세스 권한이 있어야 합니다. 폴더를 적절 하 게 보호 하는 방법에 대 한 자세한 내용은 참조 [스냅숏 폴더 보안](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)합니다.  
  
         다른 서버가 배포자의 역할을 하도록 지정한 경우 게시자에서 배포자로 연결할 때 사용할 암호를 **관리 암호** 페이지에 입력해야 합니다. 이 암호는 원격 배포자에서 게시자를 설정할 때 지정한 암호와 일치해야 합니다.  
  
         자세한 내용은 참조 [배포 구성](../../../relational-databases/replication/configure-distribution.md)합니다.  
  
    -   게시 데이터베이스를 선택합니다.  
  
    -   보고서 유형을 선택합니다. 자세한 내용은 참조 [종류의 복제](../../../relational-databases/replication/types-of-replication.md)합니다.  
  
    -   게시할 데이터와 데이터베이스 개체를 지정합니다. 필요에 따라 테이블 아티클에서 열을 필터링하고 아티클 속성을 설정합니다.  
  
    -   필요에 따라 테이블 아티클에서 행을 필터링합니다. 자세한 내용은 참조 [데이터를 게시 하는 필터](../../../relational-databases/replication/publish/filter-published-data.md)합니다.  
  
    -   스냅숏 에이전트 일정을 설정합니다.  
  
    -   다음 복제 에이전트를 실행 및 연결하는 자격 증명을 지정합니다.  
  
         \- 모든 게시에 대 한 스냅숏 에이전트입니다.  
  
         \- 모든 트랜잭션 게시에 대 한 로그 판독기 에이전트입니다.  
  
         \- 구독 업데이트를 허용 하는 트랜잭션 게시에 대 한 큐 판독기 에이전트입니다.  
  
         자세한 내용은 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md) 및 [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md)를 참조하세요.  
  
    -   필요에 따라 게시를 스크립팅합니다. 자세한 내용은 [Scripting Replication](../../../relational-databases/replication/scripting-replication.md)을 참조하세요.  
  
    -   게시의 이름을 지정합니다.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
 게시를 만든 후에 복제 저장 프로시저를 사용하여 아티클을 프로그래밍 방식으로 만들 수 있습니다. 아티클을 만드는 데 사용되는 저장 프로시저는 정의하려는 아티클의 게시 유형에 따라 달라집니다. 자세한 내용은 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)을 참조하세요.  
  
#### 스냅숏 또는 트랜잭션 게시에 대한 아티클을 정의하려면  
  
1.  게시 데이터베이스의 게시자에서 실행 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)합니다. 이 문서에 속한 게시의 이름을 지정 **@publication**, 에 대 한 문서에 대 한 이름을 **@article**, 게시할 데이터베이스 개체 **@source_object**, 및 기타 선택적인 매개 변수입니다. 사용 하 여 **@source_owner** 그렇지 않은 경우 개체의 스키마 소유권을 지정 하려면 **dbo**합니다. 문서 로그 기반 테이블 아티클의 경우에 대 한 아티클 유형을 지정 **@type**; 자세한 내용은 참조 [문서 유형 지정 & #40; 복제 TRANSACT-SQL 프로그래밍 & #41;](../../../relational-databases/replication/publish/specify-article-types-replication-transact-sql-programming.md)합니다.  
  
2.  테이블에서 행을 필터링 하거나 아티클을 보려면 가로로,를 사용 하 여 [sp_articlefilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) 필터 절을 정의할 수 있습니다. 자세한 내용은 [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)을 참조하세요.  
  
3.  테이블의 열을 필터링 하거나 아티클을 보려면 세로로,를 사용 하 여 [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)합니다. 자세한 내용은 [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)을 참조하세요.  
  
4.  실행 [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) 문서를 필터링 합니다.  
  
5.  게시에 기존 구독이 있는 경우 및 [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) 의 값을 반환 **0** 에 **immediate_sync** 호출 해야 열 [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) 각각의 기존 구독에 아티클을 추가 하려면.  
  
6.  게시에 기존 끌어오기 구독이 있는 경우 실행 [sp_refreshsubscriptions](../../../relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql.md) 게시자 하기 위한 새 문서를 포함 하는 기존 끌어오기 구독에 대 한 새 스냅숏을 만듭니다.  
  
    > [!NOTE]  
    >  스냅숏을 사용 하 여 초기화 되지 않은 구독에 대 한 필요가 없습니다 실행할 [sp_refreshsubscriptions](../../../relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql.md) 에서이 프로시저를 실행 하는 대로 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)합니다.  
  
#### 병합 게시에 대한 아티클을 정의하려면  
  
1.  게시 데이터베이스의 게시자에서 실행 [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)합니다. 에 대 한 게시의 이름을 지정 **@publication**, 에 대 한 문서 이름에 대 한 이름을 **@article**, 및에 대 한 게시 되는 개체 **@source_object**합니다. 테이블 행을 행 필터링 하는 값을 지정 **@subset_filterclause**합니다. 자세한 내용은 [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) 및 [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)를 참조하세요. 테이블 아티클이 아니라면 **@type**에 아티클 유형을 지정합니다. 자세한 내용은 참조 [문서 유형 지정 & #40; 복제 TRANSACT-SQL 프로그래밍 & #41;](../../../relational-databases/replication/publish/specify-article-types-replication-transact-sql-programming.md)합니다.  
  
2.  (선택 사항) 게시 데이터베이스의 게시자에서 실행 [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) 두 아티클 간의 조인 필터를 정의할 수 있습니다. 자세한 내용은 [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)을 참조하세요.  
  
3.  (선택 사항) 게시 데이터베이스의 게시자에서 실행 [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) 를 테이블 열을 필터링 합니다. 자세한 내용은 [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)을 참조하세요.  
  
###  <a name="TsqlExample"></a> 예(Transact-SQL)  
 이 예에서는 `Product` 테이블을 기반으로 트랜잭션 게시에 대한 아티클을 정의합니다. 여기에서 아티클은 행 및 열 방향으로 필터링됩니다.  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../relational-databases/replication/codesnippet/tsql/define-an-article_1.sql)]  
  
 이 예에서는 병합 게시에 대한 아티클을 정의합니다. 여기에서 `SalesOrderHeader` 아티클은 **SalesPersonID**에 따라 정적으로 필터링되고 `SalesOrderDetail` 아티클은 `SalesOrderHeader`에 따라 조인 필터링됩니다.  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-an-article_2.sql)]  
  
##  <a name="RMOProcedure"></a> RMO(복제 관리 개체) 사용  
 RMO(복제 관리 개체)를 사용하여 프로그래밍 방식으로 아티클을 정의할 수 있습니다. 아티클을 정의하는 데 사용하는 RMO 클래스는 정의되는 아티클의 게시 유형에 따라 달라집니다.  
  
###  <a name="PShellExample"></a> 예(RMO)  
 다음 예에서는 행 및 열 필터가 포함된 아티클을 트랜잭션 게시에 추가합니다.  
  
 [!code-csharp[HowTo#rmo_CreateTranArticles](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranarticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranArticles](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranarticles)]  
  
 다음 예에서는 병합 게시에 세 개의 아티클을 추가합니다. 이 아티클에는 열 필터가 포함되며, 두 개의 조인 필터를 사용하여 매개 변수가 있는 행 필터를 다른 아티클에 전파합니다.  
  
 [!code-csharp[HowTo#rmo_CreateMergeArticles](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergearticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergeArticles](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergearticles)]  
  
## 참고 항목  
 [게시 만들기](../../../relational-databases/replication/publish/create-a-publication.md)   
 [복제 시스템 저장 프로시저 개념](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [기존 게시에 대한 아티클 추가 및 삭제](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [게시된 데이터 필터링](../../../relational-databases/replication/publish/filter-published-data.md)   
 [데이터 및 데이터베이스 개체 게시](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [복제 시스템 저장 프로시저 개념](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  