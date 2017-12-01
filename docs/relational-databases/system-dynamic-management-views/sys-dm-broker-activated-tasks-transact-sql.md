---
title: sys.dm_broker_activated_tasks (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_broker_activated_tasks
- sys.dm_broker_activated_tasks_TSQL
- dm_broker_activated_tasks
- dm_broker_activated_tasks_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_broker_activated_tasks dynamic management view
ms.assetid: 17e6f87f-8f56-489d-9aed-216afc8ef310
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 39dead578b6c3e7c3943d707020dbdfdcdf7c310
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmbrokeractivatedtasks-transact-sql"></a>sys.dm_broker_activated_tasks(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Service Broker가 활성화한 각 저장 프로시저에 대한 행을 반환합니다.  
 

|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**spid**|**int**|활성화된 저장 프로시저 세션의 ID입니다. NULL을 허용합니다.|  
|**database_id**|**smallint**|큐가 정의된 데이터베이스의 ID입니다. NULL을 허용합니다.|  
|**queue_id**|**int**|저장 프로시저가 활성화된 큐 개체의 ID입니다. NULL을 허용합니다.|  
|**procedure_name**|**nvarchar(650)**|활성화된 저장 프로시저의 이름입니다. NULL을 허용합니다.|  
|**execute_as**|**int**|저장 프로시저가 실행되는 사용자의 ID입니다. NULL을 허용합니다.|  
  
## <a name="permissions"></a>Permissions  
 을 실행하려면 서버에 대해 VIEW SERVER STATE 권한이 필요합니다.  
  
## <a name="physical-joins"></a>물리적 조인  
 ![Sys.dm_broker_activated_tasks에 대 한 조인](../../relational-databases/system-dynamic-management-views/media/join-dm-broker-activated-tasks-1.gif "sys.dm_broker_activated_tasks에 대 한 조인")  
  
## <a name="relationship-cardinalities"></a>관계 카디널리티  
  
|원본|수행할 작업|관계|  
|----------|--------|------------------|  
|dm_broker_activated_tasks.spid|dm_exec_sessions.session_id|일 대 일|  
  
## <a name="see-also"></a>관련 항목:  
 [동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Service Broker 관련 동적 관리 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  
