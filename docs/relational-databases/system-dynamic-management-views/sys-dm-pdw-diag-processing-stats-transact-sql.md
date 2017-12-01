---
title: sys.dm_pdw_diag_processing_stats (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: df659c55-4f63-45f8-8afe-ce300031bc5b
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 05dc9dc5854b970dd97227672f5f75eecbb34718
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwdiagprocessingstats-transact-sql"></a>sys.dm_pdw_diag_processing_stats (Transact SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  관리자가 정의한 진단 세션에 통합 될 수 있는 모든 내부 진단 이벤트와 관련 된 정보를 표시 합니다. 진단 및 이벤트 하위 시스템의 데이터로 통계 드라이브 다른 Dmv의 채우기 이해 하려면이 뷰를 쿼리 합니다. 그룹에 각 노드에 있는 각 프로세스에 대 한 큐에 있습니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|이 로그는 기기 노드입니다.|  
|**process_id**|**int**|이 통계를 제출 하는 실행 중인 프로세스의 식별자입니다.|  
|**target_name**|**nvarchar(255)**|큐의 이름입니다.|  
|**queue_size**|**int**|프로세스 큐에 있는 항목의 수입니다. 큐 크기는 일반적으로 0입니다. 양수 값에는 시스템 스트레스 상태 이며 이벤트의 백로그를 구성 하는 나타냅니다. 양수 다른 열에는 해당 큐에 대 한 손상 된 시스템 및 Dmv 관련 의미 합니다.|  
|**lost_events_count**|**bigint**|손실 되는 이벤트의 수입니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [SQL 데이터 웨어하우스 및 병렬 데이터 웨어하우스 동적 관리 뷰 &#40; Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  