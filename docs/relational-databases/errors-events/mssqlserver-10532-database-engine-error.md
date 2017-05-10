---
title: "MSSQLSERVER_10532 | Microsoft 문서"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e105f17279de3903519435fdc4590431ea716158
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver10532"></a>MSSQLSERVER_10532
  
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|10532|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|PG_NO_ELIGIBLE_STMT|  
|메시지 텍스트|**@plan_handle**로 지정된 일괄 처리 또는 모듈이 계획 지침에 적합한 문을 포함하지 않으므로 계획 지침 '%.\*ls'을(를) 만들 수 없습니다. **@plan_handle**에 다른 값을 지정하세요.|  
  
## <a name="explanation"></a>설명  
**@plan_handle**로 지정된 일괄 처리 또는 모듈이 계획 지침에 적합한 문을 포함하지 않습니다.  
  
## <a name="user-action"></a>사용자 동작  
**@plan_handle**에 다른 값을 지정하세요.  
  
## <a name="see-also"></a>관련 항목:  
[계획 지침](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide&#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
