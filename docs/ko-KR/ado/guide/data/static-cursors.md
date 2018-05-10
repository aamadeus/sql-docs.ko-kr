---
title: 정적 커서 | Microsoft Docs
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
helpviewer_keywords:
- cursors [ADO], static
- static cursors [ADO]
ms.assetid: cce93ace-c4ed-4c6c-940c-28a50ff2fd12
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 04ef88ca992498194feb4772045c6ada60fc1ea5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="static-cursors"></a>정적 커서
정적 커서는 결과 집합을 커서가 처음 열릴 때 항상 표시 합니다. 구현에 따라 정적 커서는 읽기 전용 또는 읽기/쓰기 및 앞으로 및 뒤로 스크롤을 제공 합니다. 정적 커서 일반적으로 변경 내용을 멤버 자격, 순서 또는 커서가 열린 후에 결과 집합의 값을 검색 하지 않습니다. 이렇게 하려면 필요 하지 않지만 정적 커서는 자신의 업데이트, 삭제 및 삽입을 검색할 수 있습니다.  
  
 정적 커서는 업데이트, 삭제 및 삽입 하는 다른 검색 하지 않습니다. 예를 들어 정적 커서를 행과 다른 응용 프로그램을 인출 합니다. 그런 다음 해당 행을 업데이트 합니다. 응용 프로그램 다시 정적 커서에서 행을 발견 하는 값에서 다른 응용 프로그램에서 변경한 내용을 불구 하 고 변경 된지 않습니다. 스크롤 하는 모든 유형의 지원 하지만 공급자 하거나 책갈피를 지원 하지 않을 수 있습니다.  
  
 응용 프로그램에 변경 데이터를 감지 하 스크롤 필요 필요가 없는 경우 정적 커서가 적합 하 고 있습니다. 사용 하 여는 **adOpenStatic CursorTypeEnum** ado에서 정적 커서를 사용 하도록 지정할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목:  
 [정방향 전용 커서](../../../ado/guide/data/forward-only-cursors.md)   
 [키 집합 커서](../../../ado/guide/data/keyset-cursors.md)   
 [동적 커서](../../../ado/guide/data/dynamic-cursors.md)