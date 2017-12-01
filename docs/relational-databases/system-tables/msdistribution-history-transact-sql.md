---
title: MSdistribution_history (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSdistribution_history
- MSdistribution_history_TSQL
dev_langs: TSQL
helpviewer_keywords: MSdistribution_history system table
ms.assetid: 55665bd2-9e1d-4efc-8f60-c63a24f66b28
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fa93b984ecd15cc3c0629e0eaaf6310142943dfe
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="msdistributionhistory-transact-sql"></a>MSdistribution_history(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdistribution_history** 테이블은 로컬 배포자와 연결 된 배포 에이전트에 대 한 기록 행을 포함 합니다. 이 테이블은 배포 데이터베이스에 저장됩니다.  
  
## <a name="definition"></a>정의  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|배포 에이전트의 ID입니다.|  
|**runstatus**|**int**|실행 상태는 다음과 같습니다.<br /><br /> **1** = 시작 합니다.<br /><br /> **2** = 성공 합니다.<br /><br /> **3** = 진행 중입니다.<br /><br /> **4** = 유휴 상태입니다.<br /><br /> **5** = 다시 시도 합니다.<br /><br /> **6** = 실패.|  
|**start_time**|**datetime**|작업 실행을 시작할 시간입니다.|  
|**time**|**datetime**|메시지가 기록되는 시간입니다.|  
|**duration**|**int**|메시지 세션의 기간(초)입니다.|  
|**주석**|**nvarchar(4000)**|메시지 텍스트입니다.|  
|**xact_seqno**|**varbinary (16)**|마지막에 처리된 트랜잭션 시퀀스 번호입니다.|  
|**current_delivery_rate**|**float**|마지막 기록 항목 이후에 초당 전달된 평균 명령 수입니다.|  
|**current_delivery_latency**|**int**|마지막 기록 항목 이후 배포 데이터베이스를 시작하고 구독자에 적용될 때까지의 대기 시간입니다. 단위는 밀리초입니다.|  
|**delivered_transactions**|**int**|세션 중에 전달된 총 트랜잭션 수입니다.|  
|**delivered_commands**|**int**|세션 중에 전달된 총 명령 수입니다.|  
|**average_commands**|**int**|세션 중에 전달된 평균 명령 수입니다.|  
|**delivery_rate**|**float**|초당 전달된 평균 명령 수입니다.|  
|**delivery_latency**|**int**|배포 데이터베이스를 시작하고 구독자에 적용될 때까지의 대기 시간입니다. 단위는 밀리초입니다.|  
|**total_delivered_commands**|**bigint**|구독이 생성된 이후에 전달된 총 명령 수입니다.|  
|**error_id**|**int**|오류 메시지의 ID는 **MSrepl_error** 시스템 테이블입니다.|  
|**updateable_row**|**bit**|로 설정 **1** 기록 행을 덮어쓸 수 있는 경우.|  
|**timestamp**|**timestamp**|이 테이블의 타임스탬프 열입니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [복제 테이블 &#40; Transact SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [복제 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  