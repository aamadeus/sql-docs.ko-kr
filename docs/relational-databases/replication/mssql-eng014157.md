---
title: "MSSQL_ENG014157 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014157 오류"
ms.assetid: 1a0890cf-d977-43e0-a2ba-9c5ff1a8f856
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# MSSQL_ENG014157
    
## 메시지 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|14157|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|심볼 이름||  
|메시지 텍스트|구독자 '%s'이(가) 게시 '%s'에 대해 만든 구독이 만료되어 삭제되었습니다.|  
  
## 설명  
 구독자는 게시 보존 기간에 지정된 시간 내에 게시자와 동기화해야 합니다. 구독자가 이 기간 내에 동기화하지 않으면 구독이 만료됩니다. 자세한 내용은 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)을(를) 참조하세요.  
  
## 사용자 동작  
 구독자가 데이터 변경 내용을 다시 받을 수 있으려면 먼저 구독을 다시 만들고 초기화해야 합니다.  
  
-   구독을 만드는 방법에 대 한 정보를 참조 하십시오. [게시를 구독할](../../relational-databases/replication/subscribe-to-publications.md)합니다.  
  
-   구독을 초기화 하는 방법에 대 한 정보를 참조 하십시오. [구독을 초기화](../../relational-databases/replication/initialize-a-subscription.md)합니다.  
  
 구독 데이터베이스에 게시자와 동기화되지 않은 변경 내용이 있을 경우 [tablediff Utility](../../tools/tablediff-utility.md) 를 사용하여 게시 및 구독 데이터베이스에서 일치하지 않는 행을 확인할 수 있습니다.  
  
 게시 보존 기간을 늘려 구독이 만료되는 것을 방지할 수 있습니다. 높은 값을 설정할 경우 더 많은 데이터와 메타데이터가 저장되어 성능에 영향을 줄 수 있으므로 주의해야 합니다. 자세한 내용은 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)를 참조하세요.  
  
## 참고 항목  
 [오류 및 이벤트 참조 & #40입니다. 복제 및 #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  