---
title: Visual c + +에서 오류 처리 | Microsoft Docs
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- errors [ADO], Visual C++
- Visual C++ error handling [ADO]
ms.assetid: b7576f07-020a-45f7-9e79-b5756f33f7ab
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c584eda82a6a3f28b6eb78e1fd83046be31fe76
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="handling-errors-in-visual-c"></a>Visual c + +에서 오류 처리
COM, 대부분의 작업 함수 완료 되었는지 여부를 나타내는 HRESULT 반환 코드를 반환 합니다. #Import 지시문 주위 각 "원시" 메서드 또는 속성에 래퍼 코드를 생성 하 고 반환된 된 HRESULT를 확인 합니다. HRESULT 오류를 나타내는 래퍼 코드는 인수로 서 COM 오류를 HRESULT 반환 코드 _com_issue_errorex()를 호출 하 여 throw 합니다. COM 오류 개체에서 확인 수는 **try / catch** 블록입니다. (효율성의 찾았을 _com_error 개체에 대 한 참조를 catch).  
  
 ADO 오류입니다: ADO 작업이 실패에서 하 여 발생 합니다. 기본 공급자에서 반환한 오류로 표시 **오류** 개체에 **연결** 개체의 **오류** 컬렉션입니다.  
  
 #Import 지시문만 ADO.dll에 선언 된 메서드와 속성에 대 한 오류 처리 루틴을 만듭니다. 그러나 사용자 고유의 오류 검사 매크로 또는 인라인 함수를 작성 하 여이 동일한 오류 처리 메커니즘을 활용을 걸릴 수 있습니다. 예제 C++® Extensions 항목을 참조 하십시오.