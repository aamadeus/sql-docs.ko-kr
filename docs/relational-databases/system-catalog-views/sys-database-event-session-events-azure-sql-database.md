---
title: "sys.database_event_session_events (Azure SQL 데이터베이스) | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
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
ms.assetid: f4c9eb0a-173c-4c66-8dd8-6f7176b2657f
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: deb6b14739b47dda369c457ad7a2bddc70ca3fcc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdatabaseeventsessionevents-azure-sql-database"></a>sys.database_event_session_events (Azure SQL 데이터베이스)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  이벤트 세션의 각 이벤트에 대해 한 행을 반환합니다.  
  
||  
|-|  
|**적용 대상**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 및 모든 이후 버전입니다.|  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|이벤트 세션의 ID입니다. Null을 허용하지 않습니다.|  
|event_id|**int**|이벤트 ID입니다. 이 ID는 이벤트 세션 개체 내에서 고유합니다. Null을 허용하지 않습니다.|  
|name|**sysname**|이벤트의 이름입니다. Null을 허용하지 않습니다.|  
|패키지|**sysname**|이벤트가 포함된 이벤트 패키지의 이름입니다. Null을 허용하지 않습니다.|  
|module|**sysname**|이벤트가 포함된 모듈의 이름입니다. Null을 허용하지 않습니다.|  
|predicate|**nvarchar (3000)**|이벤트에 적용되는 조건자 식입니다. Null을 허용합니다.|  
|predicate_xml|**nvarchar (3000)**|이벤트에 적용되는 XML 조건자 식입니다. Null을 허용합니다.|  
  
## <a name="permissions"></a>Permissions  
 서버에 대한 VIEW DATABASE STATE 권한이 필요합니다.  
  
## <a name="remarks"></a>주의  
 이 뷰는 다음과 같은 관계 카디널리티를 가집니다.  
  
||||  
|-|-|-|  
|보낸 사람|수행할 작업|관계|  
|sys.database_event_session_events.event_session_id|sys.database_event_sessions.event_session_id|다 대 일|  
  
## <a name="see-also"></a>관련 항목:  
 [확장 이벤트](../../relational-databases/extended-events/extended-events.md)  
  
  