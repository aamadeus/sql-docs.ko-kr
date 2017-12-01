---
title: sp_restoredbreplication (Transact SQL) | Microsoft Docs
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
- sp_restoredbreplication
- sp_restoredbreplication_TSQL
helpviewer_keywords: sp_restoredbreplication
ms.assetid: a2c5ee32-e6d9-46e9-8031-8ff13c20acf7
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a68228419fb71567c08291cd63a3a31bcc0d9f8a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="sprestoredbreplication-transact-sql"></a>sp_restoredbreplication(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  원본이 아닌 서버, 데이터베이스 또는 이렇게 하지 않으면 복제를 실행할 수 없는 시스템으로 데이터베이스를 복원할 때 복제 설정을 제거합니다. 복제된 데이터베이스를 백업을 실행했던 곳이 아닌 다른 서버 또는 데이터베이스로 복원할 때는 복제 설정을 보존할 수 없습니다. 서버 복원 시 호출 **sp_restoredbreplication** 복원된 된 데이터베이스에서 복제 메타 데이터를 자동으로 제거에 직접 합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_restoredbreplication [ @srv_orig = ] 'original_server_name'  
        , [ @db_orig = ] 'original_database_name'  
    [ , [ @keep_replication = ] keep_replication ]  
    [ , [ @perform_upgrade = ] perform_upgrade ]  
```  
  
## <a name="arguments"></a>인수  
 [  **@srv_orig =** ] **'***original_server_name***'**  
 백업이 생성된 서버의 이름입니다. *original_server_name* 은 **sysname**, 기본값은 없습니다.  
  
 [  **@db_orig =** ] **'***original_database_name***'**  
 백업한 데이터베이스 이름입니다. *original_database_name* 은 **sysname**, 기본값은 없습니다.  
  
 [  **@keep_replication =** ] *keep_replication*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@perform_upgrade=** ] *perform_upgrade*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>주의  
 **sp_restoredbreplication** 모든 유형의 복제에 사용 됩니다.  
  
## <a name="permissions"></a>Permissions  
 구성원만는 **sysadmin** 또는 **dbcreator** 고정된 서버 역할 또는 **dbo** 데이터베이스 스키마를 실행할 수 있습니다 **sp_restoredbreplication**.  
  
## <a name="see-also"></a>관련 항목:  
 [복제 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  