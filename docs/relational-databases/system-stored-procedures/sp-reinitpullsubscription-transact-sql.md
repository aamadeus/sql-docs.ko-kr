---
title: sp_reinitpullsubscription (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_reinitpullsubscription_TSQL
- sp_reinitpullsubscription
helpviewer_keywords: sp_reinitpullsubscription
ms.assetid: 7d9abe49-ce92-47f3-82c9-aea749518c91
caps.latest.revision: "24"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d9020182762ac7f74e888e64814cedcae6fedec2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="spreinitpullsubscription-transact-sql"></a>sp_reinitpullsubscription(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  다음 번 배포 에이전트가 실행될 때 트랜잭션 끌어오기 또는 익명 구독을 다시 초기화하도록 표시합니다. 이 저장 프로시저는 끌어오기 구독 데이터베이스의 구독자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_reinitpullsubscription [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>인수  
 [  **@publisher=**] **'***게시자***'**  
 게시자의 이름입니다. *게시자* 은 **sysname**, 기본값은 없습니다.  
  
 [  **@publisher_db=**] **'***publisher_db***'**  
 게시자 데이터베이스의 이름입니다. *publisher_db* 은 **sysname**, 기본값은 없습니다.  
  
 [  **@publication=**] **'***게시***'**  
 게시의 이름입니다. *게시* 은 **sysname**, 기본값은 all 이며 모든 구독을 다시 초기화 하도록 표시입니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>주의  
 **sp_reinitpullsubscription** 트랜잭션 복제에 사용 됩니다.  
  
 **sp_reinitpullsubscription** 피어 투 피어 트랜잭션 복제에 지원 되지 않습니다.  
  
 **sp_reinitpullsubscription** 배포 에이전트의 다음 실행 하는 동안 구독을 다시 초기화 하도록 구독자에서 호출할 수 있습니다.  
  
 값을 사용 하 여 만든 게시의 구독에 **false** 에 대 한  **@immediate_sync**  구독자에서 다시 초기화할 수 없습니다.  
  
 끌어오기 구독을 다시 초기화할 수 중 하나를 실행 하 여 **sp_reinitpullsubscription** 구독자에서 또는 **sp_reinitsubscription** 게시자에서 합니다.  
  
## <a name="example"></a>예제  
 [!code-sql[HowTo#sp_reinitpullsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitpullsubscriptio_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 구성원만는 **sysadmin** 고정된 서버 역할 또는 **db_owner** 고정된 데이터베이스 역할을 실행할 수 있는 **sp_reinitpullsubscription**합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [구독 다시 초기화](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [구독 다시 초기화](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  