---
title: sp_delete_jobschedule (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_delete_jobschedule
- sp_delete_jobschedule_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_delete_jobschedule
ms.assetid: 82fbb48b-603a-4016-a7fb-1ce17fb76919
caps.latest.revision: "38"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0787326286ef9cccf6f7b7b771256d0bc4b1d2ad
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="spdeletejobschedule-transact-sql"></a>sp_delete_jobschedule(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  작업의 일정을 삭제합니다.  
  
 **sp_delete_jobschedule** 만 이전 버전과 호환성을 위해 제공 됩니다.  
  
  
## <a name="remarks"></a>주의  
 이제 작업 일정을 작업과 독립적으로 관리할 수 있습니다. 작업에서 일정을 제거 하려면 사용 하 여 **sp_detach_schedule**합니다. 일정을 삭제 하려면 사용 **sp_delete_schedule**합니다.  
  
> **참고:****sp_delete_jobschedule** 여러 작업에 연결 된 일정을 지원 하지 않습니다.   기존 스크립트를 호출 하는 경우 **sp_delete_jobschedule** 둘 이상의 작업에 연결 된 일정을 제거 하는 프로시저가 오류를 반환 합니다.  
  
## <a name="permissions"></a>Permissions  
 기본적으로 **sysadmin** 고정 서버 역할의 멤버는 이 저장 프로시저를 실행할 수 있습니다. 다른 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **데이터베이스의 다음** 에이전트 고정 데이터베이스 역할 중 하나를 부여 받아야 합니다.  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 이러한 역할의 사용 권한에 대한 자세한 내용은 [SQL Server 에이전트 고정 데이터베이스 역할](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)을 참조하세요.  
  
 멤버는 **sysadmin** 역할 모든 작업 일정을 삭제할 수 있습니다. 구성원 인 사용자의는 **sysadmin** 역할은 각자 소유한 작업 일정만 삭제할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목:  
 [sp_delete_schedule &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)   
 [작업 보기 또는 수정](http://msdn.microsoft.com/library/57f649b8-190c-4304-abd7-7ca5297deab7)   
 [sp_add_schedule&#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_help_jobschedule &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-jobschedule-transact-sql.md)   
 [sp_update_jobschedule &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-update-jobschedule-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  