---
title: sp_help_peerconflictdetection (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
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
- sp_help_peerconflictdetection
- sp_help_peerconflictdetection_TSQL
helpviewer_keywords: sp_help_peerconflictdetection
ms.assetid: 59e04107-5eaa-44a1-beb6-ac4f2dbbcb28
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 43221792e6f2b29ac86fc6d4ef70376ba4896c49
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="sphelppeerconflictdetection-transact-sql"></a>sp_help_peerconflictdetection(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  피어 투 피어 트랜잭션 복제 토폴로지와 관련된 게시에 대한 충돌 검색 설정 정보를 반환합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_help_peerconflictdetection [ @publication = ] 'publication'  
    [ ,[ @timeout = ] timeout ]  
```  
  
## <a name="arguments"></a>인수  
 [ @publication=] '*게시*'  
 정보가 반환될 게시의 이름입니다. *게시* 은 **sysname**, 기본값은 없습니다.  
  
 [ @timeout=] *제한 시간*  
 토폴로지에 있는 모든 노드의 응답을 기다리는 동안 프로시저가 시간 초과되는 시간(초)을 지정합니다. 토폴로지에 읽기 전용 구독자가 있으면 시간 제한 값을 지정할 수 없습니다. 읽기 전용 구독자는 이 프로시저의 호출에 응답하지 않습니다. *제한 시간* 은 **int**, 기본값은 60입니다.  
  
## <a name="result-sets"></a>결과 집합  
 sp_help_peerconflictdetection은 3가지 결과 집합을 반환합니다. 이러한 결과에 대해서는 다음 항목에서 설명합니다.  
  
-   [MSpeer_conflictdetectionconfigrequest](../../relational-databases/system-tables/mspeer-conflictdetectionconfigrequest-transact-sql.md)  
  
-   [MSpeer_conflictdetectionconfigresponse](../../relational-databases/system-tables/mspeer-conflictdetectionconfigresponse-transact-sql.md)  
  
-   [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md)  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>주의  
 sp_help_peerconflictdetection은 피어 투 피어 트랜잭션 복제에 사용됩니다.  
  
## <a name="permissions"></a>Permissions  
 sysadmin 고정 서버 역할 또는 db_owner 고정 데이터베이스 역할의 멤버여야 합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [피어 투 피어 복제에서 충돌 검색](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)   
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [복제 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  