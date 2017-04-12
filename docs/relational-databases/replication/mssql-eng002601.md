---
title: "MSSQL_ENG002601 | Microsoft Docs"
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
  - "MSSQL_ENG002601 오류"
ms.assetid: 657c3ae6-9e4b-4c60-becc-4caf7435c1dc
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_ENG002601
    
## 메시지 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|2601|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|심볼 이름|해당 사항 없음|  
|메시지 텍스트|개체에 중복 키 행을 삽입할 수 없습니다 ' %. * l s 고유 인덱스가 ' %.\*l s '입니다.|  
  
## 설명  
 이 오류는 데이터베이스의 복제 여부에 관계없이 발생할 수 있는 일반 오류입니다. 복제된 데이터베이스에서 이 오류는 일반적으로 토폴로지 내에서 기본 키가 제대로 관리되지 않았기 때문에 발생합니다. 분산 환경에서는 둘 이상의 노드에서 기본 키 열 또는 다른 고유 열에 동일한 값이 삽입되지 않도록 해야 합니다. 가능한 원인은 다음과 같습니다.  
  
-   둘 이상의 노드에서 행 삽입 및 업데이트가 발생합니다. 병합 복제 및 트랜잭션 복제에 대한 업데이트할 수 있는 구독은 둘 다 충돌 감지 및 해결 기능을 제공하지만 한 노드에서만 특정 행을 삽입 또는 업데이트하는 것이 좋습니다. 피어 투 피어 트랜잭션은 충돌 감지 및 해결 기능을 제공하지 않으므로 삽입과 업데이트를 분할해야 합니다.  
  
-   읽기 전용이어야 하는 구독자에서 행이 삽입되었습니다. 업데이트할 수 있는 구독 또는 피어 투 피어 트랜잭션 복제를 사용하는 경우가 아니면 트랜잭션 게시에 대한 구독자와 마찬가지로 스냅숏 게시에 대한 구독자는 읽기 전용으로 취급되어야 합니다.  
  
-   ID 열이 있는 테이블이 사용되지만 해당 열이 적절히 관리되지 않습니다.  
  
-   병합 복제에서이 오류도 발생할 수 있습니다 삽입 하는 동안 시스템 테이블에 **MSmerge_contents**; 오류가 발생 하는 것과 비슷합니다: 고유 인덱스가 'ucl1SycContents.' 개체 'm'에 중복 키 행을 삽입할 수 없습니다  
  
## 사용자 동작  
 필요한 동작은 오류 발생 원인에 따라 다릅니다.  
  
-   둘 이상의 노드에서 행 삽입 및 업데이트가 발생합니다.  
  
     사용된 복제 유형에 관계없이 가능한 경우 삽입 및 업데이트를 분할하는 것이 좋습니다. 이렇게 하면 충돌 감지 및 해결 과정이 간편해집니다. 피어 투 피어 트랜잭션 복제의 경우 삽입과 업데이트를 분할해야 합니다. 자세한 내용은 참조 [피어 투 피어 트랜잭션 복제](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)합니다.  
  
-   읽기 전용이어야 하는 구독자에서 행이 삽입되었습니다.  
  
     병합 복제, 업데이트할 수 있는 구독이 있는 트랜잭션 복제 또는 피어 투 피어 트랜잭션 복제를 사용하는 경우가 아니면 구독자에서 행을 삽입 또는 업데이트하지 마십시오.  
  
-   ID 열이 있는 테이블이 사용되지만 해당 열이 적절히 관리되지 않습니다.  
  
     병합 복제 및 업데이트할 수 있는 구독이 있는 트랜잭션 복제의 경우 ID 열은 복제에 의해 자동으로 관리됩니다. 피어 투 피어 트랜잭션 복제의 경우 ID 열을 수동으로 관리해야 합니다. 자세한 내용은 참조 [Id 열 복제](../../relational-databases/replication/publish/replicate-identity-columns.md)합니다.  
  
-   시스템 테이블에 삽입 하는 동안 오류가 발생 **MSmerge_contents**합니다.  
  
     이 오류는 조인 필터 속성에 잘못 된 값으로 인해 발생할 수 **join_unique_key**합니다. 부모 테이블의 조인된 열이 고유한 경우에만 이 속성을 TRUE로 설정해야 합니다. 속성이 TRUE로 설정되어 있지만 열이 고유하지 않은 경우에는 이 오류가 발생합니다. 이 속성을 설정하는 방법은 [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)을 참조하십시오.  
  
## 참고 항목  
 [오류 및 이벤트 참조 & #40입니다. 복제 및 #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  