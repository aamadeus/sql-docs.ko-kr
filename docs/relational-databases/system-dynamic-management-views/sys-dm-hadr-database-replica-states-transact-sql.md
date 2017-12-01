---
title: sys.dm_hadr_database_replica_states (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 11/08/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_database_states_TSQL
- sys.dm_hadr_database_states
- dm_hadr_database_states
- dm_hadr_database_states_TSQL
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_database_replica_states dynamic management view
ms.assetid: 1a17b0c9-2535-4f3d-8013-cd0a6d08f773
caps.latest.revision: "84"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 4b57d7550f007eb4a85f7db698aae84f133726c9
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmhadrdatabasereplicastates-transact-sql"></a>sys.dm_hadr_database_replica_states(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  참여 하는 각 데이터베이스에 대 한 행 Always On 가용성 그룹에는 반환의 로컬 인스턴스에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가용성 복제본을 호스팅하는 합니다. 이 동적 관리 뷰는 주 복제본과 보조 복제본 모두에 대한 상태 정보를 표시합니다. 보조 복제본에서 이 뷰는 서버 인스턴스에 있는 모든 보조 데이터베이스에 대해 하나의 행을 반환합니다. 주 복제본에서 이 뷰는 각 주 데이터베이스에 대해 하나의 행과 해당 보조 데이터베이스에 대해 하나의 행을 반환합니다.  
  
> [!IMPORTANT]
> 동작과 상위 수준의 상태에 따라 데이터베이스 상태 정보가 사용할 수 없거나 만료될 수 있습니다. 또한 값은 로컬 관련성만 가집니다. 예를 들어 주 복제본의 값에는 **last_hardened_lsn** 주 복제본에 현재 사용할 수 있는 지정된 된 보조 데이터베이스에 대 한 정보를 반영 하는 열, 하지 실제 확정 된 LSN 값은 보조 복제본이 현재 가질 수 있습니다.  
   
|열 이름|데이터 형식|주 복제본에 대한 설명|  
|-----------------|---------------|----------------------------------------|  
|**database_id**|**int**|SQL Server 내에서 고유한 데이터베이스의 식별자입니다. 이 값은 동일한 값에 표시 된 대로 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) 카탈로그 뷰에 있습니다.|  
|**group_id**|**uniqueidentifier**|데이터베이스가 속한 가용성 그룹의 식별자입니다.|  
|**replica_id**|**uniqueidentifier**|가용성 그룹 내 가용성 복제본의 식별자입니다.|  
|**group_database_id**|**uniqueidentifier**|가용성 그룹 내 데이터베이스의 식별자입니다. 이 식별자는 이 데이터베이스가 조인되는 모든 복제본에서 동일합니다.|  
|**is_local**|**bit**|가용성 데이터베이스가 로컬인지 여부를 나타나며 다음 중 하나입니다.<br /><br /> 0 = 데이터베이스가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 로컬이 아닙니다.<br /><br /> 1 = 데이터베이스가 서버 인스턴스에 로컬입니다.|  
|**is_primary_replica**|**bit**|복제본이 기본이면 1을, 보조 복제본이면 0을 반환합니다. SQL Server 2014 이상 적용할 수 있습니다.|  
|**synchronization_state**|**tinyint**|데이터 이동 상태 이며 다음 값 중 하나입니다.<br /><br /> 0 = 동기화 되지 않음. 주 데이터베이스의 경우 데이터베이스에서 트랜잭션 로그를 해당 보조 데이터베이스와 동기화할 준비가 되지 않았음을 나타냅니다. 보조 데이터베이스의 경우 데이터베이스에서 연결 문제로 인해 로그 동기화를 시작하지 않았거나 데이터베이스가 일시 중지되었거나, 시작 중에 전환 상태를 진행하고 있거나 역할 전환 중임을 나타냅니다.<br /><br /> 1 = Synchronizing입니다. 주 데이터베이스의 경우 해당 데이터베이스가 보조 데이터베이스의 검색 요청을 받을 준비가 되었음을 나타냅니다. 보조 데이터베이스의 경우 데이터베이스에 대한 활성 데이터 이동이 수행되고 있음을 나타냅니다.<br /><br /> 2 = Synchronized 합니다. 주 데이터베이스는 동기화 중 대신 동기화됨으로 표시됩니다. 동기 커밋 보조 데이터베이스는 로컬 캐시에 데이터베이스가 장애 조치(failover) 준비되고 동기화 중일 때 동기화됨으로 표시됩니다.<br /><br /> 3 = Reverting 합니다. 보조 데이터베이스가 주 데이터베이스에서 페이지 가져오기를 현재 진행 중인 경우의 실행 취소 프로세스의 단계를 나타냅니다. **주의:** 보조 복제본의 데이터베이스가 REVERTING 상태에서 이면 보조 복제본으로 강제 장애 조치는 데이터베이스를 유지를 주 데이터베이스로 시작할 수 없습니다. 데이터베이스를 보조 데이터베이스로 다시 연결하거나 로그 백업에서 새 로그 레코드를 적용해야 합니다.<br /><br /> 4 = 초기화 합니다. 보조 데이터베이스에서 실행 취소 LSN을 catch하는 데 필요한 트랜잭션 로그가 보조 복제본에서 제공되고 확정 중인 경우의 실행 취소 단계를 나타냅니다. **주의:** 데이터베이스가 있는 경우 보조 복제본에서 INITIALIZING 상태일에서으로 강제 장애 조치 보조 복제본 leaves 상태에서 데이터베이스는 자신이 주 데이터베이스로 시작 합니다. 데이터베이스를 보조 데이터베이스로 다시 연결하거나 로그 백업에서 새 로그 레코드를 적용해야 합니다.|  
|**synchronization_state_desc**|**nvarchar (60)**|데이터 이동 상태에 대한 설명이며 다음 중 하나입니다.<br /><br /> NOT SYNCHRONIZING<br /><br /> SYNCHRONIZING<br /><br /> SYNCHRONIZED<br /><br /> REVERTING<br /><br /> INITIALIZING|  
|**is_commit_participant**|**bit**|0 = 트랜잭션 커밋이 이 데이터베이스에 대해 동기화되어 있지 않습니다.<br /><br /> 1 = 트랜잭션 커밋이 이 데이터베이스에 대해 동기화되어 있습니다.<br /><br /> 비동기 커밋 가용성 복제본의 데이터베이스에 대해서는 이 값이 항상 0입니다.<br /><br /> 동기 커밋 가용성 복제본의 데이터베이스에 대해서는 이 값이 주 데이터베이스에서만 정확합니다.|  
|**synchronization_health**|**tinyint**|가용성 복제본에서 가용성 그룹에 포함 된 데이터베이스의 동기화 상태 및 가용성 복제본 (동기 커밋 또는 비동기-커밋 모드) 중의 가용성 모드의 교집합을 반영 하며는 다음 값입니다.<br /><br /> 0 = 정상이 아님. **synchronization_state** 데이터베이스의은 0 (NOT SYNCHRONIZING)입니다.<br /><br /> 1 = 부분적으로 정상입니다. 동기-커밋 가용성 복제본의 데이터베이스에는 부분적으로 정상인 상태로 간주 됩니다 경우 **synchronization_state** 가 1 (SYNCHRONIZING)입니다.<br /><br /> 2 = 정상입니다. 동기-커밋 가용성 복제본의 데이터베이스에 정상인 상태로 간주 되는 경우 **synchronization_state** 가 2 (SYNCHRONIZED) 및 비동기-커밋 가용성 복제본의 데이터베이스에 정상인 상태로 간주 됩니다 경우 **synchronization_state** 가 1 (SYNCHRONIZING)입니다.|  
|**synchronization_health_desc**|**nvarchar (60)**|에 대 한 설명의 **synchronization_health** 가용성 데이터베이스의 합니다.<br /><br /> NOT_HEALTHY<br /><br /> PARTIALLY_HEALTHY<br /><br /> HEALTHY|  
|**database_state**|**tinyint**|0 = 온라인<br /><br /> 1 = 복원 중<br /><br /> 2 = 복구 중<br /><br /> 3 = 복구 보류 중<br /><br /> 4 = 주의 대상<br /><br /> 5 = 응급<br /><br /> 6 = 오프라인<br /><br /> **참고:** 동일 **상태** 하려면 sys.databases의 열입니다.|  
|**database_state_desc**|**nvarchar (60)**|에 대 한 설명의 **database_state** 가용성 복제본의 합니다.<br /><br /> ONLINE<br /><br /> RESTORING<br /><br /> RECOVERING<br /><br /> RECOVERY_PENDING<br /><br /> SUSPECT<br /><br /> EMERGENCY<br /><br /> OFFLINE<br /><br /> **참고:** 동일 **상태** 하려면 sys.databases의 열입니다.|  
|**is_suspended**|**bit**|데이터베이스 상태이며 다음 중 하나입니다.<br /><br /> 0 = 다시 시작됨<br /><br /> 1 = 일시 중지됨|  
|**suspend_reason**|**tinyint**|데이터베이스가 일시 중지된 경우 일시 중지된 상태의 원인이며 다음 중 하나입니다.<br /><br /> 0 = 사용자 동작<br /><br /> 1 = 파트너가 일시 중지<br /><br /> 2 = 다시 실행<br /><br /> 3 = 캡처<br /><br /> 4 = 적용<br /><br /> 5 = 다시 시작<br /><br /> 6 = 실행 취소<br /><br /> 7 = 유효성 재검사<br /><br /> 8 = 보조 복제본 동기화 지점 계산에서 오류 발생|  
|**suspend_reason_desc**|**nvarchar (60)**|데이터베이스가 일시 중지된 이유에 대한 설명이며 다음 중 하나입니다.<br /><br /> SUSPEND_FROM_USER = 사용자가 데이터 이동을 수동으로 일시 중지했습니다.<br /><br /> SUSPEND_FROM_PARTNER = 강제 장애 조치(Failover) 후 데이터베이스 복제본이 일시 중지되었습니다.<br /><br /> SUSPEND_FROM_REDO = 다시 실행 단계 중에 오류가 발생했습니다.<br /><br /> SUSPEND_FROM_APPLY = 로그를 파일에 쓰는 동안 오류가 발생했습니다(오류 로그 참조).<br /><br /> SUSPEND_FROM_CAPTURE = 로그를 주 복제본에 캡처하는 동안 오류가 발생했습니다.<br /><br /> SUSPEND_FROM_RESTART = 데이터베이스가 다시 시작하기 전에 데이터베이스 복제본이 일시 중지되었습니다(오류 로그 참조).<br /><br /> SUSPEND_FROM_UNDO = 다시 실행 단계 중에 오류가 발생했습니다(오류 로그 참조).<br /><br /> SUSPEND_FROM_REVALIDATION = 재연결 시 로그 변경 사항 불일치가 검색되었습니다(오류 로그 참조).<br /><br /> SUSPEND_FROM_XRF_UPDATE = 공통 로그 지점을 찾을 수 없습니다(오류 로그 참조).|  
|**recovery_lsn**|**numeric(25,0)**|주 복제본에서 주 데이터베이스가 복구 또는 장애 조치(failover) 후 새 로그 레코드를 쓰기 전의 트랜잭션 로그 끝입니다. 지정된 보조 데이터베이스에 대해 이 값이 현재 확정된 LSN(last_hardened_lsn)보다 작으면 recovery_lsn은 이 보조 데이터베이스에서 다시 동기화(즉, 되돌려서 다시 초기화)해야 하는 값입니다. 이 값이 현재 확정된 LSN보다 크거나 같으면 다시 동기화가 필요하지 않으며 발생하지 않습니다.<br /><br /> **recovery_lsn** 0으로 채워진 로그-블록 ID를 반영 합니다. 실제 LSN(로그 시퀀스 번호)이 아닙니다. 이 값은 파생 하는 방법에 대 한 정보를 참조 하십시오. [LSN 열 값 이해](#LSNcolumns)이 항목의 뒷부분에 나오는 합니다.|  
|**truncation_lsn**|**numeric(25,0)**|주 복제본의 주 데이터베이스의 경우 모든 해당 보조 데이터베이스에 최소 로그 잘림 LSN을 반영합니다. 백업 작업 등에 의해 로컬 로그 잘림이 차단되는 경우 이 LSN이 로컬 잘림 LSN보다 클 수 있습니다.<br /><br /> 지정된 보조 데이터베이스의 경우 해당 데이터베이스의 잘림 지점을 반영합니다.<br /><br /> **truncation_lsn** 0으로 채워진 로그-블록 ID를 반영 합니다. 실제 로그 시퀀스 번호가 아닙니다.|  
|**last_sent_lsn**|**numeric(25,0)**|모든 로그 블록이 주 복제본에 의해 전송된 지점을 나타내는 로그 블록 식별자입니다. 가장 최근에 전송된 로그 블록의 ID가 아니라 전송될 다음 로그 블록의 ID입니다.<br /><br /> **last_sent_lsn** 로그-블록 ID를 반영 합니다. 0으로 채워진 없는 실제 로그 시퀀스 번호입니다.|  
|**last_sent_time**|**datetime**|마지막 로그 블록이 전송된 시간입니다.|  
|**last_received_lsn**|**numeric(25,0)**|이 보조 데이터베이스를 호스팅하는 보조 복제본이 모든 로그 블록을 받은 지점을 식별하는 로그 블록 ID입니다.<br /><br /> **last_received_lsn** 0으로 채워진 로그-블록 ID를 반영 합니다. 실제 로그 시퀀스 번호가 아닙니다.|  
|**last_received_time**|**datetime**|보조 복제본에서 마지막으로 수신된 메시지의 로그 블록 ID를 읽은 시간입니다.|  
|**last_hardened_lsn**|**numeric(25,0)**|보조 데이터베이스에서 마지막으로 확정된 LSN의 로그 레코드를 포함하는 로그 블록의 시작입니다.<br /><br /> 현재 정책이 "지연"인 동기 커밋 데이터베이스 또는 비동기 커밋 주 데이터베이스에서 이 값은 NULL입니다. 다른 동기-커밋 주 데이터베이스에 대 한 **last_hardened_lsn** 모든 보조 데이터베이스에서 확정 된 LSN의 최소값을 나타냅니다.<br /><br /> **참고: last_hardened_lsn** 0으로 채워진 로그-블록 ID를 반영 합니다. 실제 로그 시퀀스 번호가 아닙니다. 자세한 내용은 참조 [LSN 열 값 이해](#LSNcolumns)이 항목의 뒷부분에 나오는 합니다.|  
|**last_hardened_time**|**datetime**|보조 데이터베이스에서 마지막에 대 한 로그 블록 식별자의 시간으로 확정 된 LSN (**last_hardened_lsn**). 주 데이터베이스에서 확정된 최소 LSN에 해당하는 시간을 반영합니다.|  
|**last_redone_lsn**|**numeric(25,0)**|보조 데이터베이스에서 마지막으로 다시 실행된 로그 레코드의 실제 로그 시퀀스 번호입니다. **last_redone_lsn** 은 항상 미만 **last_hardened_lsn**합니다.|  
|**last_redone_time**|**datetime**|보조 데이터베이스에서 마지막 로그 레코드가 다시 실행된 시간입니다.|  
|**log_send_queue_size**|**bigint**|주 데이터베이스의 로그 레코드 중 보조 데이터베이스로 전송되지 않은 레코드의 양(KB)입니다.|  
|**log_send_rate**|**bigint**|주 복제본 인스턴스 전송 데이터 비율 (kb) 마지막 활성 기간 중 평균/초입니다.|  
|**redo_queue_size**|**bigint**|보조 복제본의 로그 파일에 있는 로그 레코드 중 아직 다시 실행되지 않은 로그 레코드의 양(KB)입니다.|  
|**redo_rate**|**bigint**|지정된 보조 데이터베이스에서 로그 레코드가 다시 실행되는 속도(KB/초)입니다.|  
|**filestream_send_rate**|**bigint**|FILESTREAM 파일이 보조 복제본으로 전송되는 속도(KB/초)입니다.|  
|**end_of_log_lsn**|**numeric(25,0)**|로그 LSN의 로컬 끝입니다. 주 데이터베이스와 보조 데이터베이스의 로그 캐시에 있는 마지막 로그 레코드에 해당하는 실제 LSN입니다. 기본 복제본에서 보조 행은 보조 복제본이 주 복제본에 전송한 최근 진행 메시지의 로그 LSN의 끝을 반영합니다.<br /><br /> **end_of_log_lsn** 0으로 채워진 로그-블록 ID를 반영 합니다. 실제 로그 시퀀스 번호가 아닙니다. 자세한 내용은 참조 [LSN 열 값 이해](#LSNcolumns)이 항목의 뒷부분에 나오는 합니다.|  
|**last_commit_lsn**|**Numeric(25,0)**|트랜잭션 로그의 마지막 커밋 레코드에 해당하는 실제 로그 시퀀스 번호입니다.<br /><br /> 주 데이터베이스에서 처리된 마지막 커밋 레코드에 해당합니다. 보조 데이터베이스에 대한 행에 보조 복제본이 주 복제본에 전송한 로그 시퀀스 번호가 표시됩니다.<br /><br /> 보조 데이터베이스에서 다시 실행된 마지막 커밋 레코드입니다.|  
|**last_commit_time**|**datetime**|마지막 커밋 레코드에 해당하는 시간입니다.<br /><br /> 보조 데이터베이스에서 이 시간은 주 데이터베이스의 시간과 동일합니다.<br /><br /> 주 복제본에서 각 보조 데이터베이스 행에는 해당 보조 데이터베이스를 호스팅하는 보조 복제본이 주 복제본에 다시 보고된 시간이 표시됩니다. 다시 실행 프로세스가 처리되고 진행률이 보조 복제본에 의해 주 복제본에 다시 보고된다고 가정할 때 주 데이터베이스 행과 지정된 보조 데이터베이스 행에 표시되는 시간의 차이는 대략적인 RPO(복구 시간 목표)를 나타냅니다.|  
|**low_water_mark_for_ghosts**|**bigint**|주 데이터베이스에서 고스트 정리에 사용되는 하위 워터마크를 나타내는 데이터베이스에 대한 일정하게 증가하는 번호입니다. 시간이 지나도 이 번호가 증가하지 않으면 고스트 정리가 수행되지 않은 것을 의미합니다. 정리할 고스트 행을 결정하기 위해 주 복제본은 주 복제본을 포함한 모든 가용성 복제본에서 이 데이터베이스에 대한 이 열의 최소값을 사용합니다.|  
|**secondary_lag_seconds**|**bigint**|보조 복제본이 주 복제본 뒤 동기화 하는 동안이 시간 (초) 수입니다.|  
  
##  <a name="LSNcolumns"></a>LSN 열 값 이해  
 값은 **end_of_log_lsn**, **last_hardened_lsn**, **last_received_lsn**, **last_sent_lsn**, **복구 _lsn**, 및 **truncation_lsn** 열은 실제 로그 시퀀스 번호 (Lsn) 없습니다. 각 값은 0으로 채워진 로그-블록 ID를 반영합니다.  
  
 **end_of_log_lsn**, **last_hardened_lsn**, 및 **recovery_lsn** 은 플러시 Lsn입니다. 예를 들어 **last_hardened_lsn** 블록 뒤에 오는 이미 디스크에 있는 다음 블록의 시작을 나타냅니다.  따라서 모든 LSN < 값 **last_hardened_lsn** 디스크에 있습니다.  이 값보다 크거나 같은 LSN은 플러시되지 않습니다.  
  
 반환 되는 LSN 값 중 **sys.dm_hadr_database_replica_states**만 **last_redone_lsn** 실제 LSN입니다.  
  
## <a name="security"></a>보안  
  
### <a name="permissions"></a>Permissions  
 을 실행하려면 서버에 대해 VIEW SERVER STATE 권한이 필요합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [Always On 가용성 그룹&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [가용성 그룹 모니터링&#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  