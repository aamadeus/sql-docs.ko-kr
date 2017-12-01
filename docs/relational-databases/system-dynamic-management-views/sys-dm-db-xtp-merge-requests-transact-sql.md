---
title: sys.dm_db_xtp_merge_requests (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 02/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1224e88-af74-4c99-ae32-d5d2c552a1f5
caps.latest.revision: "2"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b068552f48544b8dc3a7f11dd8981008cb080bad
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbxtpmergerequests-transact-sql"></a>sys.dm_db_xtp_merge_requests(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]


데이터베이스 병합 요청을 추적합니다. SQL Server에서 병합 요청이 생성 또는 요청 내용을 적용할 수 있는 사용자가 [sys.sp_xtp_merge_checkpoint_files (Transact SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql.md)합니다.

> [!NOTE]
> 이 동적 관리 뷰 (DMV) sys.dm_db_xtp_merge_requests, Microsoft SQL Server 2014까지 존재 합니다.
> 
> 하지만이 DMV를 SQL Server 2016 부터는 더 이상 적용 됩니다.

## <a name="columns-in-the-report"></a>보고서의 열

| 열 이름 | 데이터 형식 | Description |
| :-- | :-- | :-- |
| request_state | tinyint | 병합 요청의 상태입니다.<br/>0 = 요청됨<br/>1 = 보류 중<br/>2 = 설치<br/>3 = 중단됨 |
| request_state_desc | nvarchar(60) | 요청의 현재 상태에 대 한 의미가 있습니다.<br/><br/>요청-병합 요청이 있습니다.<br/>-보류 중인 병합이 처리 되 고 있습니다.<br/>병합-설치 완료 되었습니다.<br/>중단-병합을 완료할 수 없음을 아마도 저장소 부족 합니다. |
| destination_file_id | GUID | 원본 파일 병합을 위한 대상 파일의 고유 식별자입니다. |
| lower_bound_tsn | bigint | 대상 병합 파일에 대한 최소 타임스탬프입니다. 병합할 모든 원본 파일의 최저 트랜잭션 타임스탬프입니다. |
| upper_bound_tsn | bigint | 대상 병합 파일에 대한 최대 타임스탬프입니다. 병합할 모든 원본 파일의 최고 트랜잭션 타임스탬프입니다. |
| collection_tsn | bigint | 현재 행을 수집할 수 있는 타임스탬프입니다.<br/><br/>checkpoint_tsn이 collection_tsn보다 크면 설치됨 상태의 행이 제거됩니다.<br/><br/>checkpoint_tsn이 collection_tsn보다 작으면 중단됨 상태의 행이 제거됩니다. |
| checkpoint_tsn | bigint | 검사점이 시작된 시간입니다.<br/><br/>이 값보다 작은 타임스탬프가 있는 트랜잭션에서 수행한 모든 삭제가 새로운 데이터 파일에서 반영됩니다. 나머지 삭제는 대상 델타 파일로 이동합니다. |
| sourcenumber_file_id | GUID | 병합의 원본 파일을 고유하게 식별하는 최대 16개의 내부 파일 ID입니다. |

## <a name="permissions"></a>Permissions

현재 데이터베이스에 대해 VIEW DATABASE STATE 권한이 필요합니다.

## <a name="see-also"></a>참고 항목

[메모리 액세스에 최적화 된 테이블 동적 관리 뷰 (Transact SQL)](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)

