---
title: cdc.fn_cdc_get_all_changes_&lt;capture_instance&gt; (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server (starting with 2008)
dev_langs: TSQL
helpviewer_keywords:
- fn_cdc_get_all_changes_<capture_instance>
- change data capture [SQL Server], querying metadata
- cdc.fn_cdc_get_all_changes_<capture_instance>
ms.assetid: c6bad147-1449-4e20-a42e-b51aed76963c
caps.latest.revision: "31"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 111fab345e7679745e72ebe874dabcca3bed62fb
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2017
---
# <a name="cdcfncdcgetallchangesltcaptureinstancegt--transact-sql"></a>cdc.fn_cdc_get_all_changes_&lt;capture_instance&gt; (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  지정한 LSN(로그 시퀀스 번호) 내 원본 테이블에 적용된 각 변경에 대해 한 개의 행을 반환합니다. 해당 간격 동안 원본 행이 여러 번 변경된 경우에는 반환된 결과 집합에 각 변경이 표시됩니다. 변경 데이터를 반환하는 것 외에 4개의 메타데이터 열은 다른 데이터 원본에 해당 변경을 적용하는 데 필요한 정보를 제공합니다. 행 필터링 옵션은 결과 집합에 반환되는 행 및 메타데이터 열의 내용을 제어합니다. 행 필터 옵션이 'all'로 지정된 경우 각 변경에는 변경을 식별하기 위한 하나의 행이 있습니다. 'all update old' 옵션을 지정하면 업데이트 작업이 두 행으로 표시됩니다. 그 중 한 행에는 업데이트하기 전에 캡처한 열의 값이 포함되고 다른 행에는 업데이트한 후에 캡처한 열의 값이 포함됩니다.  
  
 이 열거 함수는 원본 테이블에 변경 데이터 캡처가 활성화될 때 생성됩니다. 함수 이름을 파생 및 형식을 사용 하 여 **cdc.fn_cdc_get_all_changes_***capture_instance* 여기서 *capture_instance* 캡처에 대 한 지정 된 값이 원본 테이블 변경 데이터 캡처가 활성화 될 때 인스턴스.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
cdc.fn_cdc_get_all_changes_capture_instance ( from_lsn , to_lsn , '<row_filter_option>' )  
  
<row_filter_option> ::=  
{ all  
 | all update old  
}  
```  
  
## <a name="arguments"></a>인수  
 *from_lsn*  
 결과 집합에 포함할 LSN 범위의 하위 끝점을 나타내는 LSN 값입니다. *from_lsn* 은 **binary (10)**합니다.  
  
 행만 [cdc. &#91; capture_instance& &#93; _CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md) 변경 테이블의 값이 있는 **__ $start_lsn** 보다 크거나 *from_lsn* 에 포함 된는 결과 집합입니다.  
  
 *to_lsn*  
 결과 집합에 포함할 LSN 범위의 상위 끝점을 나타내는 LSN 값입니다. *to_lsn* 은 **binary (10)**합니다.  
  
 행만 [cdc. &#91; capture_instance& &#93; _CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md) 변경 테이블의 값이 있는 **__ $start_lsn** 보다 작거나 *from_lsn* 같음*to_lsn* 결과 집합에 포함 됩니다.  
  
 <row_filter_option> ::= { all | all update old }  
 결과 집합에 반환되는 행과 메타데이터 열의 내용을 제어하는 옵션입니다.  
  
 다음 옵션 중 하나를 사용할 수 있습니다.  
  
 all  
 지정된 LSN 범위 내의 모든 변경을 반환합니다. 업데이트 작업으로 인한 변경의 경우 업데이트가 적용된 후 새 값을 포함하는 행만 반환합니다.  
  
 all update old  
 지정된 LSN 범위 내의 모든 변경을 반환합니다. 업데이트 작업으로 인한 변경의 경우 업데이트 전 열 값을 포함하는 행과 업데이트 후 열 값을 포함하는 행을 모두 반환합니다.  
  
## <a name="table-returned"></a>반환된 테이블  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**__$start_lsn**|**binary(10)**|변경의 커밋 순서를 유지하고 있는 변경과 관련된 LSN을 커밋합니다. 동일한 트랜잭션에서 커밋된 변경의 커밋 LSN 값은 동일합니다.|  
|**__$seqval**|**binary(10)**|트랜잭션 내 행 변경을 정렬하는 데 사용되는 시퀀스 값입니다.|  
|**__$operation**|**int**|변경 데이터의 행을 대상 데이터 원본에 적용하는 데 필요한 DML(데이터 조작 언어) 작업을 식별합니다. 다음 중 하나일 수 있습니다.<br /><br /> 1 = 삭제<br /><br /> 2 = 삽입<br /><br /> 3 = 업데이트(캡처된 열 값은 업데이트 작업 전의 값임) 이 값은 행 필터 옵션이 'all update old'로 지정된 경우에만 적용됩니다.<br /><br /> 4 = 업데이트(캡처된 열 값은 업데이트 작업 후의 값임)|  
|**__$update_mask**|**varbinary(128)**|캡처 인스턴스에 대해 식별된 각 캡처된 열에 해당하는 비트가 있는 비트 마스크입니다. 이 값이 모두 정의 하면 1로 설정 된 비트 **__ $operation** = 1 또는 2입니다. 때 **__ $operation** = 3 또는 4, 변경 된 열에 해당 하는 비트만 1로 설정 됩니다.|  
|**\<캡처된 원본 테이블 열 >**|다양함|함수에서 반환되는 나머지 열은 캡처 인스턴스가 생성될 때 식별된 캡처된 열입니다. 캡처된 열 목록에 아무 열도 지정하지 않으면 원본 테이블의 모든 열이 반환됩니다.|  
  
## <a name="permissions"></a>Permissions  
 멤버 자격이 필요는 **sysadmin** 고정된 서버 역할 또는 **db_owner** 고정된 데이터베이스 역할입니다. 다른 모든 사용자의 경우 원본 테이블에서 캡처된 모든 열에 대한 SELECT 권한이 필요하며 캡처 인스턴스에 대한 제어 역할이 정의된 경우 해당 데이터베이스 역할의 멤버 자격이 필요합니다. 호출자에 원본 데이터를 볼 수 있는 권한이 없으면 함수는 오류 229 반환 ("데이터베이스 개체 'fn_cdc_get_all_changes_...'에 대해 SELECT 권한이 거부 되었습니다 '\<데이터베이스 이름 >', 스키마 ''.").  
  
## <a name="remarks"></a>주의  
 지정된 LSN 범위가 캡처 인스턴스에 대한 변경 추적 시간대를 벗어나는 경우 함수는 오류 208("프로시저 또는 함수 cdc.fn_cdc_get_all_changes에 제공된 인수 개수가 부족합니다")을 반환합니다.  
  
 데이터 형식의 열 **이미지**, **텍스트**, 및 **ntext** 항상 NULL이 할당 된 경우이 값 **__ $operation** = 1 또는 **__ $ 작업** = 3입니다. 데이터 형식의 열 **varbinary (max)**, **varchar (max)**, 또는 **nvarchar (max)** NULL이 할당 된 경우이 값 **__ $operation** = 3 않으면 업데이트 하는 동안 해당 열이 변경 합니다. 때 **__ $operation** = 1, 이러한 열에는 삭제할 때 해당 값이 할당 됩니다. 캡처 인스턴스에 포함된 계산 열은 항상 NULL 값을 갖습니다.  
  
## <a name="examples"></a>예  
 여러 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 템플릿을 사용할 수 있습니다 하는 변경 데이터 캡처 쿼리 함수를 사용 하는 방법을 보여 줍니다. 이러한 서식 파일에서 사용할 수 있는 **보기** 메뉴 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]합니다. 자세한 내용은 참조 [템플릿 탐색기](http://msdn.microsoft.com/library/b9ee55c5-bb44-4f76-90ac-792d8d83b4c8)합니다.  
  
 이 예에서는 `Enumerate All Changes for Valid Range Template`을 보여 줍니다. 이 템플릿은 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스의 HumanResources.Department 원본 테이블에 대해 정의된 `cdc.fn_cdc_get_all_changes_HR_Department` 함수를 사용하여 `HR_Department` 캡처 인스턴스에서 현재 사용할 수 있는 모든 변경 내용을 보고합니다.  
  
```  
-- ========  
-- Enumerate All Changes for Valid Range Template  
-- ========  
USE AdventureWorks2012;  
GO  
  
DECLARE @from_lsn binary(10), @to_lsn binary(10);  
SET @from_lsn = sys.fn_cdc_get_min_lsn('HR_Department');  
SET @to_lsn   = sys.fn_cdc_get_max_lsn();  
SELECT * FROM cdc.fn_cdc_get_all_changes_HR_Department  
  (@from_lsn, @to_lsn, N'all');  
GO  
```  
  
## <a name="see-also"></a>관련 항목:  
 [cdc.fn_cdc_get_net_changes_&#60; capture_instance& &#62; &#40; Transact SQL &#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [sys.fn_cdc_map_time_to_lsn &#40; Transact SQL &#41;](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md)   
 [sys.sp_cdc_get_ddl_history &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md)   
 [sys.sp_cdc_get_captured_columns &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md)   
 [sys.sp_cdc_help_change_data_capture &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [변경 데이터 캡처 정보&#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  