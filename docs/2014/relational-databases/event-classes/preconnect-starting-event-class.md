---
title: PreConnect:Starting 이벤트 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ae1972bde3d0d13a608f4583e88e2b649ab82be3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36089565"
---
# <a name="preconnectstarting-event-class"></a>PreConnect:Starting 이벤트 클래스
  PreConnect:Starting 이벤트 클래스는 LOGON 트리거나 리소스 관리자 분류자 함수가 언제 실행을 시작하는지 표시합니다.  
  
## <a name="preconnectstarting-event-class-data-columns"></a>PreConnect:Starting 이벤트 클래스 데이터 열  
  
|데이터 열 이름|데이터 형식|Description|열 ID|필터 가능|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|`int`|215|27|아니요|  
|SPID|`int`|이 이벤트를 발생시키는 서버 프로세스의 ID입니다.|12|예|  
|EventSubClass|`int`|사용자 정의 분류자 함수의 경우 1입니다.|21|예|  
|StartTime|`datetime`|사용자 정의 분류자 함수가 시작되는 시간입니다.|14|예|  
|ObjectID|`int`|사용자 정의 분류자 개체의 ID입니다.|22|예|  
|ObjectName|`nvarchar(256)`|분류자 사용자 정의 함수의 두 부분으로 이루어진 이름입니다(예: dbo.classifier).|34|예|  
  
## <a name="see-also"></a>관련 항목  
 [확장 이벤트](../extended-events/extended-events.md)   
 [PreConnect:Completed 이벤트 클래스](preconnect-completed-event-class.md)   
 [Resource Governor](../resource-governor/resource-governor.md)  
  
  