---
title: "sys.database_event_session_fields (Azure SQL 데이터베이스) | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.reviewer: 
ms.service: 
ms.component: system-catalog-views
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: Azure SQL Database
ms.assetid: 9b5c94d6-612c-4e0f-976d-ac6ba55da3ac
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 16d550e1a453b921eb0768ab758557192e9f0e16
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdatabaseeventsessionfields-azure-sql-database"></a>sys.database_event_session_fields (Azure SQL 데이터베이스)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  이벤트 및 대상에 명시적으로 설정된 각 사용자 지정 가능 열에 대해 한 행을 반환합니다.  
  
||  
|-|  
|**적용 대상**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 및 모든 이후 버전입니다.|  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|이벤트 세션의 ID입니다. Null을 허용하지 않습니다.|  
|object_id|**int**|이 필드와 관련된 개체의 ID입니다. Null을 허용하지 않습니다.|  
|name|**sysname**|필드 이름입니다. Null을 허용하지 않습니다.|  
|value|**sql_variant**|필드 값입니다. Null을 허용하지 않습니다.|  
  
## <a name="permissions"></a>Permissions  
 서버에 대한 VIEW DATABASE STATE 권한이 필요합니다.  
  
## <a name="remarks"></a>주의  
 이 뷰는 다음과 같은 관계 카디널리티를 가집니다.  
  
||||  
|-|-|-|  
|보낸 사람|수행할 작업|관계|  
|sys.database_event_session_actions.event_session_id|sys.database_event_sessions.event_session_id|다 대 일|  
|sys.database_event_session_actions.event_id<br /><br /> sys.database_event_session_actions.object_id<br /><br /> sys.database_event_session_actions.event_session_id|sys.database_event_session_events.event_session_id<br /><br /> sys.database_event_session_events.event_id|다 대 일|  
|sys.database_event_session_actions.event_session_id<br /><br /> sys.database_event_session_actions.object_id|sys.database_event_session_targets.event_session_id<br /><br /> sys.database_event_session_targets.target_id|다 대 일|  
  
## <a name="see-also"></a>관련 항목:  
 [확장 이벤트](../../relational-databases/extended-events/extended-events.md)  
  
  