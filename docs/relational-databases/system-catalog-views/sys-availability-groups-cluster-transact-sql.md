---
title: sys.availability_groups_cluster (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.availability_groups_cluster
- availability_groups_cluster
- availability_groups_cluster_TSQL
- sys.availability_groups_cluster_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_groups_cluster catalog view
- Availability Groups [SQL Server], WSFC clusters
ms.assetid: d0f4683f-cdf0-4227-8b68-720ffe58f158
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c06aa309da80d737bc422dd4f0726ed903cc24e1
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51656514"
---
# <a name="sysavailabilitygroupscluster-transact-sql"></a>sys.availability_groups_cluster(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Windows Server 장애 조치 클러스터링 (WSFC) 각 Always On 가용성 그룹에 대 한 행을 반환합니다. 각 행에는 WSFC 클러스터의 가용성 그룹 메타데이터가 포함됩니다.  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|가용성 그룹의 GUID(Globally Unique Identifier)입니다.|  
|**name**|**sysname**|가용성 그룹의 이름으로, WSFC(Windows Server 장애 조치(failover) 클러스터) 내에서 고유해야 하는 사용자 지정 이름입니다.|  
|**resource_id**|**nvarchar(40)**|WSFC 클러스터 리소스의 리소스 ID입니다.|  
|**resource_group_id**|**nvarchar(40)**|가용성 그룹의 WSFC 클러스터 리소스 그룹에 대한 리소스 그룹 ID입니다.|  
|**failure_condition_level**|**int**|자동 장애 조치(failover)가 트리거되어야 하는 사용자 정의 오류 상태 수준으로, 다음 정수 값 중 하나입니다.<br /><br /> 1: 자동 장애 조치를 시작 해야 되도록 지정 합니다. 다음의 경우: <br />- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 종료 되었습니다.<br />WSFC 장애 조치 클러스터에 연결 하기 위한 가용성 그룹의 임대가-서버 인스턴스로부터 ACK를 받지 때문에 만료 됩니다. 자세한 내용은 [작동 방법: SQL Server Always On 임대 시간 제한](https://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-Always%20On-lease-timeout.aspx)을 참조하세요.<br /><br /> 2: 자동 장애 조치를 시작 해야 되도록 지정 합니다. 다음의 경우:  <br />-인스턴스의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 지정 및 클러스터에 연결 하지 **health_check_timeout** 가용성 그룹의 임계값을 초과 합니다. <br />-가용성 복제본이 실패 상태입니다. <br />3: 심각한 자동 장애 조치를 시작 해야 되도록 지정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 분리 된 spinlock, 중대 한 쓰기 액세스 위반 또는 과다 한 덤핑 같은 내부 오류입니다. 이것은 기본값입니다. <br />4: 보통 자동 장애 조치가 시작 수 해야 하도록 지정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 지속적인 메모리 부족 상태와 같은 내부 오류는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 내부 리소스 풀입니다.<br />5: 정규화 된 오류 상태를 포함 하 여 자동 장애 조치가 시작 수 해야 하도록 지정 합니다.<br />-SQL 엔진 작업자 스레드가 소진 된 경우 <br />해결할 수 없는 교착 상태가 검색 합니다.<br /><br /> 오류 상태 수준(1–5)의 범위는 가장 낮은 제한 수준 1에서 가장 높은 제한 수준 5까지입니다. 특정 상태 수준은 그보다 낮은 모든 제한 수준을 포함합니다. 따라서 가장 엄격한 상태 수준 5에는 그보다 낮은 네 개의 제한 상태 수준(1~4)이 포함되고, 수준 4에는 수준 1~3이 포함됩니다.<br /><br /> 이 값을 변경 하려면 FAILURE_CONDITION_LEVEL 옵션을 사용 합니다 [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] 문입니다.|  
|**health_check_timeout**|**int**|에 대 한 대기 시간 (밀리초)을 [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) 시스템 저장 프로시저를 서버 상태 정보를 반환할 서버 인스턴스가 느리거나 중지로 간주 됩니다. 기본값은 30000밀리초(30초)입니다.<br /><br /> 이 값을 변경 하려면 HEALTH_CHECK_TIMEOUT 옵션을 사용 하 여 [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] 문입니다.|  
|**automated_backup_preference**|**tinyint**|이 가용성 그룹의 가용성 데이터베이스에서 백업을 수행하기 위한 기본 위치입니다. 다음 값 중 하나입니다.<br /><br /> 0: 기본입니다. 백업이 항상 주 복제본에서만 수행됩니다.<br />1: 보조만. 기본적으로 보조 복제본에서 백업을 수행합니다.<br />2: 보조 복제본을 선호 합니다. 기본적으로 보조 복제본에서 백업을 수행하지만, 보조 복제본을 백업 작업에 사용할 수 없는 경우에는 주 복제본에서 백업을 수행합니다. 이것이 기본 동작입니다.<br />3: 임의의 복제본. 백업이 주 복제본에서 수행되는지 보조 복제본에서 수행되는지에 대한 기본 설정이 없습니다.<br /><br /> 자세한 내용은 [활성 보조: 보조 복제본에 백업&#40;Always On 가용성 그룹&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)개념을 소개합니다.|  
|**automated_backup_preference_desc**|**nvarchar(60)**|에 대 한 설명을 **automated_backup_preference**하나씩입니다.<br /><br /> PRIMARY<br /><br /> SECONDARY_ONLY<br /><br /> SECONDARY<br /><br /> 없음|  
  
## <a name="security"></a>보안  
  
### <a name="permissions"></a>사용 권한  
 서버 인스턴스에 대한 VIEW  ANY  DEFINITION  권한이 필요합니다.  
  
## <a name="see-also"></a>관련 항목  
 [sys.availability_replicas&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [Always On 가용성 그룹&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [가용성 그룹 모니터링&#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [가용성 그룹 모니터링&#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
