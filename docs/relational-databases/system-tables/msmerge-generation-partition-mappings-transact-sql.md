---
title: MSmerge_generation_partition_mappings (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
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
- MSmerge_generation_partition_mappings_TSQL
- MSmerge_generation_partition_mappings
dev_langs: TSQL
helpviewer_keywords: MSmerge_generation_partition_mappings system table
ms.assetid: 443a4024-ce48-4772-9ee5-95bd6fb6476b
caps.latest.revision: "24"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e126b80c962aa80583d5fd0bf7bb265868a660f4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="msmergegenerationpartitionmappings-transact-sql"></a>MSmerge_generation_partition_mappings(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_generation_partition_mappings** 테이블은 병합 게시에서 파티션의 변경 내용을 추적 하는 데 사용 됩니다. 이 테이블은 게시 데이터베이스와 구독 데이터베이스에 저장됩니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**publication_number**|**smallint**|병합 게시를 식별합니다.|  
|**생성**|**bigint**|생성 값입니다.|  
|**partition_id**|**int**|파티션을 식별합니다.|  
|**changecount**|**int**|파티션이 변경된 횟수입니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [복제 테이블 &#40; Transact SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [복제 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  