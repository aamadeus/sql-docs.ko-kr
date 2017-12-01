---
title: syspolicy_policy_execution_history (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_execution_history_TSQL
- syspolicy_policy_execution_history
dev_langs: TSQL
helpviewer_keywords: syspolicy_policy_execution_history view
ms.assetid: b13c44a7-6d49-4d50-abe1-e657fc52bb05
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 90d0de71b9f93bb264dea3b9562a3d9bfa44669c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="syspolicypolicyexecutionhistory-transact-sql"></a>syspolicy_policy_execution_history(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  정책이 실행된 시간, 각 실행의 결과 및 오류가 있는 경우 오류에 대한 자세한 내용을 표시합니다. 다음 표에서는 syspolicy_policy_execution_history 뷰의 열을 설명합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|history_id|**bigint**|이 레코드의 ID입니다. 각 레코드는 정책과 시작된 시간을 하나씩 나타냅니다.|  
|policy_id|**int**|정책의 ID입니다.|  
|start_date|**datetime**|이 정책을 실행하려고 시도한 날짜와 시간입니다.|  
|end_date|**datetime**|이 정책이 실행을 마친 시간입니다.|  
|result|**bit**|정책의 성공 또는 실패를 나타냅니다. 0 = 실패, 1 = 성공입니다.|  
|exception_message|**nvarchar(max)**|예외가 발생한 경우 예외에서 생성한 메시지입니다.|  
|exception|**nvarchar(max)**|예외가 발생한 경우 예외에 대한 설명입니다.|  
  
## <a name="remarks"></a>주의  
 [syspolicy_policy_execution_history_details](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-details-transact-sql.md) 뷰는 정책 및 테스트 된 조건 식의 대상에 대 한 관련된 세부 정보를 포함 합니다.  
  
## <a name="permissions"></a>Permissions  
 msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [정책 기반 관리를 사용하여 서버 관리](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [정책 기반 관리 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  