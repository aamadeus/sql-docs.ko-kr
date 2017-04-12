---
title: "Deadlock Graph 이벤트 클래스 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Deadlock Graph 이벤트 클래스"
ms.assetid: 20f92233-c912-4382-8993-8e2e23d03fbe
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# Deadlock Graph 이벤트 클래스
  **Deadlock Graph** 이벤트 클래스는 교착 상태의 XML에 대해 설명합니다. 이 클래스는 **Lock:Deadlock** 이벤트 클래스와 동시에 발생합니다.  
  
## Deadlock Graph 이벤트 클래스 데이터 열  
  
|데이터 열 이름|데이터 형식|설명|열 ID|필터 가능|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**EventClass**|**int**|이벤트 유형 = 148|27|아니요|  
|**EventSequence**|**int**|요청 내에 지정된 이벤트 시퀀스입니다.|51|아니요|  
|**IsSystem**|**int**|이벤트가 시스템 프로세스에서 발생했는지 아니면 사용자 프로세스에서 발생했는지를 나타냅니다. 1 = 시스템, 0 = 사용자 이 값은 이 이벤트의 경우 항상 1입니다.|60|예|  
|**LoginName**|**nvarchar**|사용자 로그인 이름(DOMAIN\Username 형식의 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 로그인 자격 증명 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안 로그인)입니다. 이 값은 항상 이 이벤트의 시스템 사용자입니다.|11|예|  
|**LoginSid**|**image**|로그인한 사용자의 SID(보안 ID)입니다. 이 정보는 sys.server_principals 카탈로그 뷰에 있습니다. 각 SID는 서버의 각 로그인마다 고유합니다. 이 값은 항상 이 이벤트의 시스템 사용자 SID입니다.|41|예|  
|**ServerName**|**nvarchar**|추적 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.|26|아니요|  
|**SessionLoginName**|**nvarchar**|세션을 시작한 사용자의 로그인 이름입니다. 예를 들어 Login1을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결하고 Login2로 문을 실행할 경우 **SessionLoginName** 은 Login1을 표시하고 **LoginName** 은 Login2를 표시합니다. 이 열은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 Windows 로그인을 모두 표시합니다.|64|예|  
|**SPID**|**int**|이벤트가 발생한 세션의 ID입니다.|12|예|  
|**StartTime**|**datetime**|교착 상태가 감지된 시간입니다.|14|예|  
|**TextData**|**ntext**|교착 상태에 대한 XML 설명입니다.|1|예|  
|**TransactionID**|**bigint**|사용되지 않습니다.|4|예|  
  
## 참고 항목  
 [sp_trace_setevent&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Lock:Deadlock 이벤트 클래스](../../relational-databases/event-classes/lock-deadlock-event-class.md)  
  
  