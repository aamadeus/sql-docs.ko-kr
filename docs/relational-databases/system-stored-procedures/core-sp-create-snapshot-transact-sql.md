---
title: core.sp_create_snapshot (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
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
- sp_create_snapshot
- sp_create_snapshot_TSQL
dev_langs: TSQL
helpviewer_keywords:
- management data warehouse, data collector stored procedures
- data collector [SQL Server], stored procedures
- core.sp_create_snapshot stored procedure
- sp_create_snapshot
ms.assetid: ff297bda-0ee2-4fda-91c8-7000377775e3
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 674968b7b981755ea0f67f8657116537d2a5791c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="corespcreatesnapshot-transact-sql"></a>core.sp_create_snapshot(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  관리 데이터 웨어하우스 core.snapshots 뷰에 행을 삽입합니다. 이 프로시저는 업로드 패키지가 관리 데이터 웨어하우스로 데이터를 업로드하기 시작할 때마다 호출됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
core.sp_create_snapshot [ @collection_set_uid = ] 'collection_set_uid'  
    , [ @collector_type_uid = ] 'collector_type_uid'  
    ,[ @machine_name = ] 'machine_name'  
    , [ @named_instance = ] 'named_instance'  
    , [ @log_id = ] log_id  
    , [ @snapshot_id = ] snapshot_id OUTPUT  
```  
  
## <a name="arguments"></a>인수  
 [ @collection_set_uid =] '*collection_set_uid*'  
 컬렉션 집합에 대한 GUID입니다. *collection_set_uid* 은 **uniqueidentifier** 기본값은 없습니다. GUID를 확인하려면 msdb 데이터베이스에서 dbo.syscollector_collection_sets 뷰를 쿼리합니다.  
  
 [ @collector_type_uid =] '*collector_type_uid*'  
 수집기 유형의 GUID입니다. *collector_type_uid* 은 **uniqueidentifier** 기본값은 없습니다. GUID를 확인하려면 msdb 데이터베이스에서 dbo.syscollector_collector_types 뷰를 쿼리합니다.  
  
 [ @machine_name=] '*이며 여기에서 machine_name*'  
 컬렉션 집합이 있는 서버의 이름입니다. *이며 여기에서 machine_name* 은 **sysname**, 기본값은 없습니다.  
  
 [ @named_instance=] '*named_instance*'  
 컬렉션 집합의 인스턴스 이름입니다. *named_instance* 은 **sysname**, 기본값은 없습니다.  
  
 [ @log_id =] *log_id*  
 데이터를 수집한 서버의 컬렉션 집합 이벤트 로그에 매핑되는 고유 식별자입니다. *log_id* 은 **bigint** 기본값은 없습니다. 에 대 한 값을 얻기 위해 *log_id*, msdb 데이터베이스에서 dbo.syscollector_execution_log 뷰를 쿼리 합니다.  
  
 [ @snapshot_id =] *snapshot_id*  
 core.snapshots 뷰에 삽입 된 행에 대 한 고유 식별자입니다. *snapshot_id* 은 **int** 이며 OUTPUT으로 반환 합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>주의  
 업로드 패키지가 관리 데이터 웨어하우스로 데이터 업로드를 시작할 때마다 데이터 수집기 런타임 구성 요소는 core.sp_create_snapshot을 호출합니다.  
  
 이 프로시저는 다음을 확인합니다.  
  
-   collection_set_uid가 core.source_info_internal 테이블의 기존 항목과 일치  
  
-   collector_type_uid가 core.supported_collector_types 뷰의 기존 항목과 일치  
  
 위 확인 중 하나라도 실패할 경우 프로시저가 실패하고 오류를 반환합니다.  
  
## <a name="permissions"></a>Permissions  
 멤버 자격이 필요는 **mdw_writer** (EXECUTE 권한 있음)와 고정된 데이터베이스 역할입니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 디스크 사용 컬렉션 집합의 스냅숏을 만들어 관리 데이터 웨어하우스에 추가한 다음 스냅숏 식별자를 반환합니다. 이 예에서는 기본 인스턴스가 사용됩니다.  
  
```  
USE <management_data_warehouse>;  
DECLARE @snapshot_id int;  
EXEC core.sp_create_snapshot   
    @collection_set_uid = '7B191952-8ECF-4E12-AEB2-EF646EF79FEF',   
    @collector_type_uid = '302E93D1-3424-4BE7-AA8E-84813ECF2419',  
    @machine_name = '<computername>',  
    @named_instance = 'MSSQLSERVER',  
    @log_id = 11, -- ID of the log for the collection set  
    @snapshot_id = @snapshot_id OUTPUT;  
```  
  
## <a name="see-also"></a>관련 항목:  
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [데이터 수집기 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [관리 데이터 웨어하우스](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  