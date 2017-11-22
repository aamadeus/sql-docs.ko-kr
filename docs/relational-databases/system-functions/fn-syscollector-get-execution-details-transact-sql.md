---
title: fn_syscollector_get_execution_details (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_syscollector_get_execution_details_TSQL
- fn_syscollector_get_execution_details
dev_langs: TSQL
helpviewer_keywords: fn_syscollector_get_execution_details function
ms.assetid: d59ddf0c-72c0-4c57-bc83-aef260e4e105
caps.latest.revision: "15"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bd44ed098f4dbf15e529df6cbe4026d065dfa2a5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="fnsyscollectorgetexecutiondetails-transact-sql"></a>fn_syscollector_get_execution_details(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  지정된 패키지에 대한 package_execution_id와 일치하는 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 로그(sysssislog) 부분을 반환합니다. 테이블은 런타임에 패키지나 패키지의 태스크 및 컨테이너에 의해 생성되는 각 로깅 항목에 대해 한 개의 행을 포함합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
fn_syscollector_get_execution_details ( log_id )  
```  
  
## <a name="arguments"></a>인수  
 *log_id*  
 실행 로그의 고유한 로컬 식별자입니다. *log_id* 은 **int**합니다.  
  
## <a name="table-returned"></a>반환된 테이블  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|id|**int**|로깅 항목의 고유 식별자입니다.|  
|이벤트|**sysname**|로깅 항목을 생성한 이벤트의 이름입니다.|  
|computer|**nvarchar**|로깅 항목이 생성될 때 패키지가 실행된 컴퓨터입니다.|  
|적용한 후|**nvarchar**|로깅 항목을 생성한 패키지를 실행한 사용자 또는 에이전트의 이름입니다.|  
|원본(source)|**nvarchar**|로깅 항목을 생성한 실행 파일의 이름입니다.|  
|sourceid|**uniqueidentifier**|로깅 항목을 생성한 실행 파일의 GUID입니다.|  
|executionid|**uniqueidentifier**|로깅 항목을 생성한 실행 파일의 실행 인스턴스 GUID입니다.|  
|starttime|**datetime**|패키지 실행이 시작된 시간입니다.|  
|endtime|**datetime**|패키지가 완료된 시간입니다.|  
|datacode|**int**|로그 항목에 연결된 이벤트를 식별하는 정수 값입니다. "0"은 이벤트가 식별자를 제공하지 않는다는 의미입니다.|  
|databytes|**image**|반환 값을 식별하는 바이트 배열입니다.|  
|message|**nvarchar**|이벤트에 대한 설명 및 이벤트 관련 정보입니다.|  
  
## <a name="permissions"></a>Permissions  
 에 대 한 SELECT 권한이 필요 **dc_operator**합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [에서 패키지 로깅 SQL Server 데이터 도구를 사용 하도록 설정](../../integration-services/performance/integration-services-ssis-logging.md#server_logging)   
 [데이터 컬렉션](../../relational-databases/data-collection/data-collection.md)  
  
  