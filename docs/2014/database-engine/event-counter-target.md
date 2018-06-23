---
title: 이벤트 카운터 대상 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- synchronous event counter target [SQL Server extended events]
- targets [SQL Server extended events], synchronous event counter target
ms.assetid: 342e08d1-dcca-4a71-ae64-cb61b55b85bc
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 370835af2532a3602bbc5aa944b114ba8f7e61ac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36183084"
---
# <a name="event-counter-target"></a>이벤트 카운터 대상
  이벤트 카운터 대상은 확장 이벤트 세션 동안 발생하는 모든 이벤트를 계산합니다. 이벤트 카운터 대상을 사용하면 전체 이벤트 컬렉션의 오버헤드를 추가하지 않고도 작업 특성에 대한 정보를 얻을 수 있습니다. 이 대상에는 사용자 지정할 수 있는 매개 변수가 없습니다.  
  
## <a name="adding-the-target-to-a-session"></a>세션에 대상 추가  
 확장 이벤트 세션에 이벤트 카운터 대상을 추가하려면 이벤트 세션을 만들거나 변경할 때 다음 문을 포함해야 합니다.  
  
```  
ADD TARGET package0.event_counter  
```  
  
## <a name="reviewing-the-target-output"></a>대상 출력 검토  
 다음 쿼리를 사용하여 이벤트 카운터 대상의 출력을 검토할 수 있습니다. 쿼리에서 *session_name* 을 이벤트 세션의 이름으로 바꿉니다.  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 다음 예에서는 이벤트 카운터 대상의 출력 형식을 보여 줍니다.  
  
```  
<CounterTarget truncated = "0">  
  <Packages>  
    <Package name = "[package name]">  
      <Event name = "[event name]" count = "[number]" />  
    </Package>  
  </Packages>  
</CounterTarget>  
```  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server 확장 이벤트 대상](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [sys.dm_xe_session_targets&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)   
 [CREATE EVENT SESSION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  