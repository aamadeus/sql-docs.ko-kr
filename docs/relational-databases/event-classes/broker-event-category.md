---
title: "Broker 이벤트 범주 | Microsoft Docs"
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
  - "SQL Server 이벤트 클래스, Broker 이벤트 범주"
  - "Broker 이벤트 범주 [SQL Server]"
  - "이벤트 클래스 [SQL Server], Broker 이벤트 범주"
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
caps.latest.revision: 17
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 17
---
# Broker 이벤트 범주
  **Broker** 이벤트 범주에는 일반적인 Service Broker 이벤트가 포함됩니다.  
  
## 섹션 내용  
  
|항목|설명|  
|-----------|-----------------|  
|[Broker:Activation 이벤트 클래스](../../relational-databases/event-classes/broker-activation-event-class.md)|큐 모니터가 활성화 저장 프로시저를 시작하는 경우에 생성되는 이벤트입니다.|  
|[Broker:Connection 이벤트 클래스](../../relational-databases/event-classes/broker-connection-event-class.md)|Service Broker에서 관리하는 전송 연결 상태를 보고하기 위해 생성되는 이벤트입니다.|  
|[Broker:Conversation 이벤트 클래스](../../relational-databases/event-classes/broker-conversation-event-class.md)|대화 진행률을 보고하기 위해 생성되는 이벤트입니다.|  
|[Broker:Conversation Group 이벤트 클래스](../../relational-databases/event-classes/broker-conversation-group-event-class.md)|데이터베이스에서 대화 그룹을 만들거나 삭제하는 경우에 생성되는 이벤트입니다.|  
|[Broker:Corrupted Message 이벤트 클래스](../../relational-databases/event-classes/broker-corrupted-message-event-class.md)|데이터베이스에서 손상된 메시지를 받았음을 보고하기 위해 생성되는 이벤트입니다.|  
|[Broker:Forwarded Message Dropped 이벤트 클래스](../../relational-databases/event-classes/broker-forwarded-message-dropped-event-class.md)|전달되어야 하는 Service Broker 메시지가 SQL Server에서 삭제된 경우 생성되는 이벤트입니다.|  
|[Broker:Forwarded Message Sent 이벤트 클래스](../../relational-databases/event-classes/broker-forwarded-message-sent-event-class.md)|SQL Server가 Service Broker 메시지를 전달할 때 생성되는 이벤트입니다.|  
|[Broker:Message Classify 이벤트 클래스](../../relational-databases/event-classes/broker-message-classify-event-class.md)|Service Broker가 메시지 라우팅을 지정하는 경우에 생성되는 이벤트입니다.|  
|[Broker:Message Drop 이벤트 클래스](../../relational-databases/event-classes/broker-message-drop-event-class.md)|Service Broker가 받은 메시지를 유지할 수 없는 경우에 생성되는 이벤트입니다. 이 메시지는 이 인스턴스의 서비스로 배달되어야 합니다.|  
|[Broker:Remote Message Ack 이벤트 클래스](../../relational-databases/event-classes/broker-remote-message-ack-event-class.md)|Service Broker가 메시지 승인을 보내거나 받는 경우에 생성되는 이벤트입니다.|  
  
 두 개의 보안 감사 이벤트도 Service Broker에 제공됩니다. 이러한 이벤트에 대한 자세한 내용은 [Audit Broker Login 이벤트 클래스](../../relational-databases/event-classes/audit-broker-login-event-class.md) 및 [Audit Broker Conversation 이벤트 클래스](../../relational-databases/event-classes/audit-broker-conversation-event-class.md)를 참조하세요.  
  
## 참고 항목  
 [Security Audit 이벤트 범주](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  