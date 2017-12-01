---
title: dbo.sysjobactivity (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/05/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysjobactivity_TSQL
- dbo.sysjobactivity
- sysjobactivity
- sysjobactivity_TSQL
dev_langs: TSQL
helpviewer_keywords: sysjobactivity system table
ms.assetid: fd17cac9-5d1f-4b44-b2dc-ee9346d8bf1e
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0b7991dfbe4aee731d436d725aba2081adf87e84
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysjobactivity-transact-sql"></a>dbo.sysjobactivity(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 활동 및 상태를 기록합니다.  이 테이블에 저장 되는 **msdb** 데이터베이스입니다.
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|에 저장 된 세션의 ID는 **syssessions** 테이블에 **msdb** 데이터베이스입니다.|  
|**job_id**|**uniqueidentifier**|작업의 ID입니다.|  
|**run_requested_date**|**datetime**|작업 실행을 요청한 날짜와 시간입니다.|  
|**run_requested_source**|**sysname(nvarchar(128))**|작업 실행을 요청한 사람입니다.<br /><br /> **1** SOURCE_SCHEDULER =<br /><br /> **2** SOURCE_ALERTER =<br /><br /> **3** SOURCE_BOOT =<br /><br /> **4** SOURCE_USER =<br /><br /> **6** SOURCE_ON_IDLE_SCHEDULE =|  
|**queued_date**|**datetime**|이 작업이 대기한 날짜와 시간입니다. 작업이 바로 실행된 경우 이 열은 NULL입니다.|  
|**start_execution_date**|**datetime**|작업을 실행하도록 예약된 날짜와 시간입니다.|  
|**last_executed_step_id**|**int**|마지막으로 실행된 작업 단계의 ID입니다.|  
|**last_executed_step_**<br /><br /> **date**|**datetime**|마지막 작업 단계가 실행되기 시작한 날짜와 시간입니다.|  
|**stop_execution_date**|**datetime**|작업 실행이 완료된 날짜와 시간입니다.|  
|**job_history_id**|**int**|행을 식별 하는 데 사용 된 **sysjobhistory** 테이블입니다.|  
|**next_scheduled_run_date**|**datetime**|작업을 실행하도록 예약된 다음 날짜와 시간입니다.|  

## <a name="example"></a>예제
이 예제에서는 모든 SQL Server 에이전트 작업에 대 한 런타임 상태를 반환 됩니다.  [!INCLUDE[tsql](../../includes/tsql-md.md)] 에서 다음 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]명령을 실행합니다.
```tsql
SELECT sj.Name, 
    CASE
        WHEN sja.start_execution_date IS NULL THEN 'Not running'
        WHEN sja.start_execution_date IS NOT NULL AND sja.stop_execution_date IS NULL THEN 'Running'
        WHEN sja.start_execution_date IS NOT NULL AND sja.stop_execution_date IS NOT NULL THEN 'Not running'
    END AS 'RunStatus'
FROM msdb.dbo.sysjobs sj
JOIN msdb.dbo.sysjobactivity sja
ON sj.job_id = sja.job_id
WHERE session_id = (
    SELECT MAX(session_id) FROM msdb.dbo.sysjobactivity); 
```
  
## <a name="see-also"></a>관련 항목:  
 [dbo.sysjobhistory &#40; Transact SQL &#41;](../../relational-databases/system-tables/dbo-sysjobhistory-transact-sql.md)  
  
  