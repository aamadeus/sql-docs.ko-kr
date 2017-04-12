---
title: "PreConnect:Completed 이벤트 클래스 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PreConnect:Completed 이벤트 클래스"
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
caps.latest.revision: 18
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 18
---
# PreConnect:Completed 이벤트 클래스
  PreConnect:Completed 이벤트 클래스는 LOGON 트리거나 리소스 관리자 분류자 함수가 언제 실행을 종료하는지 표시합니다.  
  
## PreConnect:Completed 이벤트 클래스 데이터 열  
  
|데이터 열 이름|데이터 형식|설명|열 ID|필터 가능|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|**int**|216|27|아니요|  
|SPID|**int**|이 이벤트를 발생시키는 서버 프로세스의 ID입니다.|12|예|  
|EventSubClass|**int**|사용자 정의 분류자 함수의 경우 1입니다.|21|예|  
|StartTime|**datetime**|사용자 정의 분류자 함수가 시작되는 시간입니다.|14|예|  
|EndTime|**datetime**|사용자 정의 분류자 함수가 시작되는 시간입니다.|15|예|  
|기간|**bigint**|분류자 함수에 의해 사용된 시간(마이크로초)입니다.|13|예|  
|ObjectID|**int**|사용자 정의 분류자 개체의 ID입니다.|22|예|  
|CPU|**int**|CPU 사용량(밀리초)입니다.|18|예|  
|Reads|**int**|논리적 읽기 수입니다.|16|예|  
|Writes|**int**|논리적 쓰기 수입니다.|17|예|  
|GroupID|**int**|분류된 작업 그룹의 ID입니다.|66|예|  
|오류|**int**|사용자 정의 분류자 함수를 실행하지 못할 경우 마지막 오류 번호입니다.|31|예|  
|State|**int**|마지막 오류의 상태입니다.|30|예|  
|TargetUserName|**sysname**|시스템에서 해당 활성 그룹을 찾을 수 없는 경우 사용자 정의 분류자 함수의 반환 값(작업 그룹 이름)입니다. 그렇지 않으면 이 열은 NULL로 설정됩니다.|39|예|  
|ObjectName|**nvarchar(256)**|분류자 사용자 정의 함수의 두 부분으로 이루어진 이름입니다(예: dbo.classifier).|34|예|  
  
## 참고 항목  
 [확장 이벤트](../../relational-databases/extended-events/extended-events.md)   
 [PreConnect:Starting 이벤트 클래스](../../relational-databases/event-classes/preconnect-starting-event-class.md)   
 [리소스 관리자](../../relational-databases/resource-governor/resource-governor.md)  
  
  