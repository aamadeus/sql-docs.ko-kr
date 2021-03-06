---
title: 정방향 전용 커서 | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], forward-only
- forward-only cursors [ADO]
ms.assetid: 2b1e062f-3294-4a6f-8241-a17045c4df18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee3d8a80598e3f41bd6bfaf9a493639ee36cd3ee
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47802841"
---
# <a name="forward-only-cursors"></a>정방향 전용 커서
커서를 앞 으로만 이동 가능한 (또는 스크롤할 수 없는) 이라는 일반적인 기본 커서 유형을 결과 집합 앞 으로만 이동할 수 있습니다. 정방향 전용 커서 (결과 집합에서 앞으로 및 뒤로 이동 하는 기능); 스크롤을 지원 하지 않습니다. 결과 집합의 끝부터에서 행 인출만 지원 합니다. 일부 정방향 전용 커서를 사용 하 여 (같은 SQL Server 커서 라이브러리를 사용 하 여) 모든 insert, update 및 delete 문은 현재 사용자 (또는 다른 사용자가 커밋한) 결과 집합의 행에 영향을 행이 인출 하는 대로 표시 됩니다. 하지만 커서는 뒤로 스크롤할 수 없습니다, 행 변경 내용을 데이터베이스에 행이 인출 된 후 표시 되지 않습니다 커서를 통해.  
  
 현재 행에 대 한 데이터 처리 된 후 정방향 전용 커서는 데이터를 저장 하는 데 사용 된 리소스를 해제 합니다. 정방향 전용 커서는 기본적으로 모든 변경이 감지 되 면 현재 행이 처리 되는 동적입니다. 된다는 하며 기본 테이블에 대 한 업데이트를 표시 하도록 결과 집합을 사용 하도록 설정 합니다.  
  
 정방향 전용 커서는 뒤로 스크롤을 지원 하지 않습니다, 하지만 응용 프로그램은 커서를 닫았다가 하 여 결과 집합의 시작 부분에 반환할 수 있습니다. 이것이 적은 양의 데이터를 사용 하는 효과적인 방법입니다. 대신 응용 프로그램 수 결과 집합을 한 번 읽고, 데이터를 로컬로 캐시 및 다음 로컬 데이터 캐시를 찾습니다.  
  
 응용 프로그램은 결과 집합을 스크롤할 필요가 없으면, 정방향 전용 커서가 최소한의 오버 헤드를 사용 하 여 빠르게 데이터를 검색 하는 가장 좋은 방법은 있습니다. 사용 하 여는 **adOpenForwardOnly CursorTypeEnum** ado에서 정방향 전용 커서를 사용 하려는 나타냅니다.  
  
## <a name="see-also"></a>관련 항목  
 [정적 커서](../../../ado/guide/data/static-cursors.md)   
 [키 집합 커서](../../../ado/guide/data/keyset-cursors.md)   
 [동적 커서](../../../ado/guide/data/dynamic-cursors.md)
