---
title: MSSQLSERVER_11409 | Microsoft 문서
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 11409 (Database Engine error)
ms.assetid: 99b71a1c-a72d-4ca9-9d00-4230c9042ba5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8dcb8bba87d83f4127bc7358c45b5f5a7664d46b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600521"
---
# <a name="mssqlserver11409"></a>MSSQLSERVER_11409
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|11409|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|ALTERCOL_COLSET_DROP|  
|메시지 텍스트|테이블에 포함된 열 개수가 1,025개를 초과하므로 테이블 '%.\*ls'의 열 집합 '%.*ls'을(를) 삭제할 수 없습니다.|  
  
## <a name="explanation"></a>설명  
테이블은 스파스나 계산 열로 지정되지 않은 열을 최대 1,024개까지 포함할 수 있습니다. 스파스 열로 인해 테이블 열 개수가 1,024개를 초과하면 테이블에 대한 열 집합을 정의해야 합니다. 참조된 테이블의 열 개수가 1,024개를 초과한 상태에서 이 열 집합을 제거하려고 했습니다.  
  
## <a name="user-action"></a>사용자 동작  
테이블의 현재 열과 함께 열 집합을 유지해야 합니다.  
  
열 집합을 제거하려면 먼저 테이블의 열 개수가 1,024개 미만이 될 때까지 테이블에서 열을 제거해야 합니다. 그런 다음 열 집합을 제거할 수 있습니다.  
  
