---
title: sys.dm_continuous_copy_status (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_continuous_copy_status_TSQL
- dm_continuous_copy_status_TSQL
- dm_continuous_copy_status
- sys.dm_continuous_copy_status
dev_langs:
- TSQL
helpviewer_keywords:
- dm_continuous_copy_status
- sys.dm_continuous_copy_status
ms.assetid: 411b2e71-4421-4ef5-900d-5af068750899
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 9cbd0997a7d675c0c7630b730d6ba7514070ab8f
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51665942"
---
# <a name="sysdmcontinuouscopystatus-azure-sql-database"></a>sys.dm_continuous_copy_status(Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  현재 지역에서 복제 연속 복사 관계에 참여 하는 각 사용자 데이터베이스 (V11)에 대 한 행을 반환 합니다. 지정된 주 데이터베이스에 대해 둘 이상의 연속 복사 관계가 시작된 경우 이 테이블에는 각 활성 보조 데이터베이스에 대한 행이 하나씩 포함됩니다.  
  
SQL Database V12를 사용 하는 경우 사용 해야 [sys.dm_geo_replication_link_status](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md) (있으므로 *sys.dm_continuous_copy_status* V11에만 적용 됩니다).

  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|**copy_guid**|**uniqueidentifier**|복제본 데이터베이스의 고유 ID입니다.|  
|**partner_server**|**sysname**|연결된 SQL Database 서버의 이름입니다.|  
|**partner_database**|**sysname**|연결된 SQL Database 서버의 연결된 데이터베이스 이름입니다.|  
|**last_replication**|**datetimeoffset**|마지막으로 적용된 복제된 트랜잭션의 타임스탬프입니다.|  
|**replication_lag_sec**|**int**|현재 시간과 활성 보조 데이터베이스에서 승인되지 않은 주 데이터베이스에서 성공적으로 커밋된 마지막 트랜잭션의 타임스탬프 간의 시간 차이(초)입니다.|  
|**replication_state**|**tinyint**|이 데이터베이스에 대 한 연속 복사 복제의 상태입니다. 가능한 값 및 해당 설명을 보려면은 다음과 같습니다.<br /><br /> 1: 시드입니다. 복제 대상이 시드되고 있고 트랜잭션 측면에서 일관되지 않은 상태입니다. 시드가 완료될 때까지 활성 보조 데이터베이스에 연결할 수 없습니다. <br />2: 캐치 업 합니다. 활성 보조 데이터베이스가 주 데이터베이스를 현재 따라잡고 있고 트랜잭션 측면에서 일관된 상태입니다.<br />3: 다시 시드해야 합니다. 활성 보조 데이터베이스가 복구할 수 없는 복제 오류로 인해 자동으로 다시 시드되고 있습니다.<br />4: 일시 중단 합니다. 이는 활성 연속 복사 관계가 아닙니다. 일반적으로 이 상태는 상호 링크에 사용할 수 있는 대역폭이 주 데이터베이스의 트랜잭션 작업 수준에 충분하지 않음을 나타냅니다. 그러나 연속 복사 관계는 그대로 유지됩니다.|  
|**replication_state_desc**|**nvarchar(256)**|replication_state에 대한 설명으로, 다음 중 하나입니다.<br /><br /> SEEDING<br /><br /> CATCH_UP<br /><br /> RE_SEEDING<br /><br /> SUSPENDED|  
|**is_rpo_limit_reached**|**bit**|이 값은 항상 0으로 설정됩니다.|  
|**is_target_role**|**bit**|0 = 복사 관계의 원본<br /><br /> 1 = 복사 관계의 대상|  
|**is_interlink_connected**|**bit**|1 = 상호 링크가 연결되었습니다.<br /><br /> 0 = 상호 링크가 끊어졌습니다.|  
  
## <a name="permissions"></a>사용 권한  
 데이터를 검색 하려면의 멤버 자격이 필요 합니다 **db_owner** 데이터베이스 역할. 멤버, dbo 사용자는 **dbmanager** 데이터베이스 역할 및 sa 로그인을 모두 쿼리할 수이 보기도 있습니다.  
  
## <a name="remarks"></a>Remarks  
 **sys.dm_continuous_copy_status** 보기가 만들어집니다 합니다 **리소스** 데이터베이스 및 논리 마스터를 포함 한 모든 데이터베이스에 표시 됩니다. 그러나 논리 master에서 이 뷰를 쿼리하면 빈 집합이 반환됩니다.  
  
 데이터베이스에서 해당 데이터베이스에 대 한 행에서 연속 복사 관계 종료 되는 경우는 **sys.dm_continuous_copy_status** 뷰가 사라집니다.  
  
 같은 합니다 **sys.dm_database_copies** 뷰에서 **sys.dm_continuous_copy_status** 데이터베이스의 두 주 데이터베이스나 활성 보조 데이터베이스의 연속 복사 관계의 상태를 반영 . 와 달리 **sys.dm_database_copies**를 **sys.dm_continuous_copy_status** 작업 및 성능에 대 한 정보를 제공 하는 여러 열을 포함 합니다. 이러한 열에 포함 됩니다 **last_replication**, 및 **replication_lag_sec**...  
  
## <a name="see-also"></a>관련 항목  
 [sys.dm_database_copies &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)   
 [활성 지역 복제 저장 프로시저 &#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/81658ee4-4422-4d73-bf7a-86a07422cb0d)  
  
  
