---
title: MSreplication_options (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
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
- MSreplication_options
- MSreplication_options_TSQL
dev_langs: TSQL
helpviewer_keywords: MSreplication_options system table
ms.assetid: 23cf10d7-8bc1-4368-b5eb-e5576421e776
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5711a1f0de3f335867c3b5162a4ec77f52d79dfc
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="msreplicationoptions-transact-sql"></a>MSreplication_options(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSreplication_options** 테이블은 복제에 의해 내부적으로 사용 되는 메타 데이터를 저장 합니다. 이 테이블에 저장 되는 **마스터** 데이터베이스입니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**optname**|**sysname**|내부적으로만 사용됩니다.|  
|**값**|**bit**|내부적으로만 사용됩니다.|  
|**major_version**|**int**|내부적으로만 사용됩니다.|  
|**minor_version**|**int**|내부적으로만 사용됩니다.|  
|**수정 버전**|**int**|내부적으로만 사용됩니다.|  
|**install_failures**|**int**|내부적으로만 사용됩니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [복제 테이블&#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  