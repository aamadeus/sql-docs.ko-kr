---
title: sys.dm_fts_fdhosts (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_fts_fdhosts
- dm_fts_fdhosts_TSQL
- sys.dm_fts_fdhosts
- sys.dm_fts_fdhosts_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.dm_fts_fdhosts dynamic management view
- troubleshooting [SQL Server], full-text search
ms.assetid: d42a6334-4362-4361-83da-f8324fe55ec7
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fef59b93c9f9c5694fe0b7ecd8404eeaffcaf380
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmftsfdhosts-transact-sql"></a>sys.dm_fts_fdhosts(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  서버 인스턴스에 있는 필터 데몬 호스트의 현재 작업에 대한 정보를 반환합니다.  
  
 
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**fdhost_id**|**int**|필터 데몬 호스트의 ID입니다.|  
|**fdhost_name**|**nvarchar(120)**|필터 데몬 호스트의 이름입니다.|  
|**fdhost_process_id**|**int**|필터 데몬 호스트의 Windows 프로세스 ID입니다.|  
|**fdhost_type**|**nvarchar(120)**|필터 데몬 호스트에서 처리 중인 문서 형식이며 다음 중 하나입니다.<br /><br /> 단일 스레드<br /><br /> 다중 스레드<br /><br /> 대용량 문서|  
|**max_thread**|**int**|필터 데몬 호스트의 최대 스레드 수입니다.|  
|**batch_count**|**int**|필터 데몬 호스트에서 처리 중인 일괄 처리 수입니다.|  
  
## <a name="permissions"></a>Permissions  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], 필요 `VIEW SERVER STATE` 권한.   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 프리미엄 계층 필요는 `VIEW DATABASE STATE` 데이터베이스에는 권한이 있습니다. [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 표준 및 기본 계층 필요는 **서버 관리자** 또는 **Azure Active Directory 관리자** 계정.  

## <a name="examples"></a>예  
 다음 예에서는 필터 데몬 호스트의 이름과 이 호스트의 최대 스레드 수를 반환합니다. 또한 필터 데몬 호스트에서 현재 처리되고 있는 일괄 처리 수를 모니터링합니다. 이 정보를 사용하여 성능 문제를 진단할 수 있습니다.  
  
```  
SELECT fdhost_name, batch_count, max_thread FROM sys.dm_fts_fdhosts;  
GO  
```  
  
## <a name="see-also"></a>관련 항목:  
 [전체 텍스트 검색 및 의미 체계 검색 동적 관리 뷰 및 함수 &#40; Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [전체 텍스트 검색](../../relational-databases/search/full-text-search.md)  
  
  