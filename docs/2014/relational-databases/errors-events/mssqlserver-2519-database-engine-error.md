---
title: MSSQLSERVER_2519 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ec6663028f2c0e133996053a31acfc0e04b49738
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48169262"
---
# <a name="mssqlserver2519"></a>MSSQLSERVER_2519
    
## <a name="details"></a>설명  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|2519|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|DBCC_NO_EXPRESSION_EVALUATOR|  
|메시지 텍스트|내부 식 계산기를 초기화할 수 없으므로 개체 ID O_ID(개체 "O_NAME")에 대해 계산 열 및 사용자 정의 유형을 확인할 수 없습니다.|  
  
## <a name="explanation"></a>설명  
 이 정보 메시지는 쿼리 프로세서가 내부 개체와 DBCC를 제공할 수 없어 계산 열과 CLR(공통 언어 런타임) 사용자 정의 유형을 평가할 수 없음을 나타냅니다. 따라서 계산 열 및 CLR 사용자 정의 형식이 올바른지 확인하거나 DBCC에서 인덱스와 기본 테이블 간의 일관성을 확인할 때 사용할 수 없습니다.  
  
## <a name="user-action"></a>사용자 동작  
 없음  
  
## <a name="see-also"></a>관련 항목  
 [MSSQLSERVER_2518](mssqlserver-2518-database-engine-error.md)  
  
  
