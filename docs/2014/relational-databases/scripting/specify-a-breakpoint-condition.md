---
title: 중단점 조건 지정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.breakpt.condition
helpviewer_keywords:
- Transact-SQL debugger, breakpoint conditions
ms.assetid: b43d8a2b-99a3-4fb7-8848-99c042ea7ef7
caps.latest.revision: 6
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: c9f8d69cd320009562b81c4b33c0cbd3374f1498
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36186500"
---
# <a name="specify-a-breakpoint-condition"></a>중단점 조건 지정
  중단점 조건은 중단점에 도달할 때마다 디버거가 평가하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 식입니다. 지정한 조건을 만족하고 지정한 적중 횟수에 도달하면 디버거는 중단점에 대해 지정된 동작을 중단하거나 수행합니다.  
  
## <a name="specifying-conditions"></a>조건 지정  
 부울 값으로 평가되는 올바른 Transact-SQL 식을 지정해야 합니다. 자세한 내용은 [식&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql)을 참조하세요.  
  
 올바르지 않은 구문을 사용하여 중단점 조건을 지정하면 즉시 경고 메시지가 나타납니다. 구문은 올바르지만 의미 체계가 올바르지 않은 조건을 지정하면 처음 중단점에 도달할 때 경고 메시지가 표시됩니다. 두 경우 모두 올바르지 않은 중단점에 도달하면 디버거가 실행을 중지합니다.  
  
#### <a name="to-specify-a-condition"></a>조건을 지정하려면  
  
1.  편집기 창에서 중단점 문자 모양을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **조건** 을 클릭합니다.  
  
     -또는-  
  
     **중단점** 창에서 중단점 문자 모양을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **조건** 을 클릭합니다.  
  
2.  **중단점 조건** 대화 상자에서 **조건** 상자에 올바른 부울 식을 입력합니다.  
  
3.  선택 **참인** 식이 계산 되는 경우 중단 하려면 `true`, 선택 또는 **변경 된** 식의 값이 변경 되었을 때 중단 하려는 경우.  
  
    > [!NOTE]  
    >  중단점에 처음 도달할 때까지 디버거는 부울 식을 평가하지 않습니다. **이(가) 변경된 경우**를 선택한 경우 디버거는 첫 번째 평가를 변경으로 간주하지 않으므로 첫 번째 평가 시에는 중단하지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [적중 횟수 지정](specify-a-hit-count.md)   
 [중단점 동작 지정](specify-a-breakpoint-action.md)  
  
  