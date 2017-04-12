---
title: "이벤트 알림에 대한 정보 가져오기 | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "이벤트 알림 [SQL Server], 메타데이터"
  - "상태 정보 [SQL Server], 이벤트 알림"
  - "메타데이터 [SQL Server], 이벤트 알림"
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# 이벤트 알림에 대한 정보 가져오기
  다음 카탈로그 뷰는 이벤트 알림에 대한 메타데이터를 쿼리하는 데 사용할 수 있습니다.  
  
 **비서버 수준 이벤트 알림에 대한 정보를 가져오려면**  
  
-   [sys.event_notifications&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  데이터베이스 수준에서 만든 **sys.event_notifications**에서 이벤트 알림에 대한 메타데이터를 보려면 최소한 데이터베이스에 대한 CONTROL, ALTER, TAKE OWNERSHIP 또는 VIEW DEFINITION 권한이 있거나, 이벤트 알림의 소유자이거나, ALTER ANY DATABASE EVENT NOTIFICATION 권한이 있어야 합니다. 특정 큐에서 만든 이벤트 알림의 경우 최소한 개체에 대한 CONTROL, ALTER, TAKE OWNERSHIP 또는 VIEW DEFINITION 권한이 있거나, 이벤트 알림의 소유자이거나, ALTER ANY DATABASE EVENT NOTIFICATION 권한이 있어야 합니다.  
  
 **서버 수준 이벤트 알림에 대한 정보를 가져오려면**  
  
-   [sys.server_event_notifications&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  최소한 서버에 대한 CONTROL 또는 VIEW ANY DEFINITION 권한이 있거나, 이벤트 알림의 로그온 또는 소유자이거나, **sys.server_event_notifications**에서 이벤트 알림에 대한 메타데이터를 볼 수 있는 ALTER ANY EVENT NOTIFICATION 권한이 있어야 합니다.  
  
 **이벤트 알림을 발생시킬 수 있는 모든 이벤트에 대한 정보를 가져오려면**  
  
-   [sys.event_notification_event_types&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql.md)  
  
> [!NOTE]  
>  이 카탈로그 뷰는 이벤트 그룹을 반환하지 않습니다.  
  
## 참고 항목  
 [이벤트 알림](../../relational-databases/service-broker/event-notifications.md)  
  
  