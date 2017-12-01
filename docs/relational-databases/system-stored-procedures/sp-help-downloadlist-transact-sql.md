---
title: sp_help_downloadlist (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
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
- sp_help_downloadlist_TSQL
- sp_help_downloadlist
dev_langs: TSQL
helpviewer_keywords: sp_help_downloadlist
ms.assetid: 745b265b-86e8-4399-b928-c6969ca1a2c8
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ec580160321fa1e4581c25356492e461aeb0ac05
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpdownloadlist-transact-sql"></a>sp_help_downloadlist(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  모든 행을 나열는 **sysdownloadlist** 제공 된 작업 또는 없는 작업을 지정 하는 경우 모든 행에 대 한 시스템 테이블입니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_help_downloadlist { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }   
     [ , [ @operation = ] 'operation' ]   
     [ , [ @object_type = ] 'object_type' ]   
     [ , [ @object_name = ] 'object_name' ]   
     [ , [ @target_server = ] 'target_server' ]   
     [ , [ @has_error = ] has_error ]   
     [ , [ @status = ] status ]   
     [ , [ @date_posted = ] date_posted ]  
```  
  
## <a name="arguments"></a>인수  
 [  **@job_id=** ] *job_id*  
 정보를 반환할 작업의 ID입니다. *job_id* 은 **uniqueidentifier**, 기본값은 NULL입니다.  
  
 [  **@job_name=** ] **'***job_name***'**  
 작업의 이름입니다. *job_name* 은 **sysname**, 기본값은 NULL입니다.  
  
> [!NOTE]  
>  어느 *job_id* 또는 *job_name* 지정 해야 하지만 둘 다 지정할 수 없습니다.  
  
 [  **@operation=** ] **'***작업***'**  
 지정된 작업에 유효한 작업입니다. *작업* 은 **varchar(64)**, 기본값은 NULL 이며 다음이 값 중 하나일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**결함**|마스터 대상 서버 제거를 요청 하는 서버 작업 **SQLServerAgent** 서비스입니다.|  
|**DELETE**|전체 작업을 제거하는 작업의 수행입니다.|  
|**INSERT**|전체 작업을 추가하거나 기존 작업을 새로 고치는 작업의 수행입니다. 여기에는 적용되는 모든 작업 단계 및 일정이 포함됩니다.|  
|**다시 등록**|서버 작업이 대상 서버로 하여금 폴링 간격 및 다중 서버 도메인에 대한 표준 시간대를 포함하여 포함 정보를 다시 전달하도록 합니다. 대상 서버를 다시 다운로드도 **MSXOperator** 세부 정보입니다.|  
|**SET-POLL**|대상 서버가 다중 서버 도메인을 폴링하는 간격(초)을 설정하는 서버 작업입니다. 를 지정 하는 경우 *값* 필요한 간격 값으로 해석 되 고의 값 수 **10** 를 **28,800**합니다.|  
|**시작**|작업 실행 시작을 요청하는 작업의 수행입니다.|  
|**중지**|작업 실행 중지를 요청하는 작업의 수행입니다.|  
|**동기화 시간**|대상 서버로 하여금 시스템 시계와 다중 서버 도메인을 동기화하도록 하는 서버 작업입니다. 이 작업은 비용이 많이 필요하므로 자주 실행하지 않고 제한적으로 실행합니다.|  
|**UPDATE**|만 업데이트 하는 작업은 **sysjobs** 작업, 작업 단계 나 아닌 일정에 대 한 정보입니다. 자동으로 호출한 **sp_update_job**합니다.|  
  
 [  **@object_type=** ] **'***object_type***'**  
 지정된 작업에 대한 개체의 유형입니다. *object_type* 은 **varchar(64)**, 기본값은 NULL입니다. *object_type* JOB 이나 SERVER 일 수 있습니다. 유효한에 대 한 자세한 내용은 *object_type*값, 참조 [sp_add_category &#40; Transact SQL &#41; ](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md).  
  
 [  **@object_name=** ] **'***object_name***'**  
 개체 이름입니다. *object_name* 은 **sysname**, 기본값은 NULL입니다. 경우 *object_type* 이 JOB 인 *object_name*작업의 이름입니다. 경우 *object_type*서버인 경우 *object_name*서버 이름입니다.  
  
 [  **@target_server=** ] **'***target_server***'**  
 대상 서버의 이름입니다. *target_server* 은 **nvarchar (128)**, 기본값은 NULL입니다.  
  
 [  **@has_error=** ] *has_error*  
 작업이 오류를 승인해야 하는지 여부입니다. *has_error* 은 **tinyint**, 기본값은 NULL 나타내는입니다 없음 오류를 승인 해야 합니다. **1** 모든 오류를 승인 해야 있는지를 나타냅니다.  
  
 [  **@status=** ] *상태*  
 작업의 상태입니다. *상태* 은 **tinyint**, 기본값은 NULL입니다.  
  
 [  **@date_posted=** ] *date_posted*  
 모든 항목이 생성된 날짜와 시간 또는 결과 집합에 포함되어야 하는 이후에 지정된 날짜와 시간입니다. *date_posted* 은 **datetime**, 기본값은 NULL입니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|명령의 고유한 정수 ID입니다.|  
|**source_server**|**nvarchar (30)**|명령을 발생시킨 서버의 컴퓨터 이름입니다. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전 7.0,이 항상 마스터 (MSX) 서버의 컴퓨터 이름입니다.|  
|**operation_code**|**nvarchar(4000)**|명령의 작업 코드입니다.|  
|**object_name**|**sysname**|명령이 적용되는 개체입니다.|  
|**object_id**|**uniqueidentifier**|해당 명령에 의해 영향을 받는 개체의 id입니다 (**job_id** 작업 개체 또는 서버 개체에 대 한 0x00) 또는 해당 하는 데이터 값은 **operation_code**합니다.|  
|**target_server**|**nvarchar (30)**|해당 명령이 다운로드될 대상 서버입니다.|  
|**error_message**|**nvarchar (1024)**|명령을 처리하는 동안 문제가 발생하는 경우 대상 서버에서 발행되는 오류 메시지입니다.<br /><br /> 참고: 모든 오류 메시지 블록이 모든 추가 대상 서버에서 다운로드 합니다.|  
|**date_posted**|**datetime**|명령이 테이블에 게시된 날짜입니다.|  
|**date_downloaded**|**datetime**|대상 서버가 명령을 다운로드한 날짜입니다.|  
|**상태**|**tinyint**|작업의 상태입니다.<br /><br /> **0** = 아직 다운로드<br /><br /> **1** = 성공적으로 다운로드 합니다.|  
  
## <a name="permissions"></a>Permissions  
 이 프로시저를 실행할 수 있는 권한은 기본적으로 **sysadmin** 고정 서버 역할의 멤버로 설정됩니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 `sysdownloadlist` 작업에 대한 행을 `NightlyBackups`에 나열합니다.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_downloadlist  
    @job_name = N'NightlyBackups',  
    @operation = N'UPDATE',   
    @object_type = N'JOB',   
    @object_name = N'NightlyBackups',  
    @target_server = N'SEATTLE2',   
    @has_error = 1,   
    @status = NULL,   
    @date_posted = NULL ;  
GO  
```  
  
## <a name="see-also"></a>관련 항목:  
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  