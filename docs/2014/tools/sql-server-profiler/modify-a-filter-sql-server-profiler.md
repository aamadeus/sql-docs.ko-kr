---
title: (SQL Server Profiler) 필터를 수정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], modifying
- modifying filters, modifying
- filters [SQL Server], traces
ms.assetid: 8b317813-4918-4485-b930-77b1951aa00c
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cf53cb678e4069a6efe02719c3e03b47489b9e57
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36081725"
---
# <a name="modify-a-filter-sql-server-profiler"></a>필터 수정(SQL Server Profiler)
  추적 정의가 포함된 추적 템플릿에 필터를 추가하여 추적에서 수집하는 이벤트의 수를 제한할 수 있습니다. 수집된 이벤트의 수를 제한하면 추적의 성능 효과가 저하될 수 있습니다. 추적 템플릿에 필터를 설정했고 추적에서 필요한 유형의 정보를 수집하고 있지 않는 것을 확인하는 경우 해당 필터를 편집할 수 있습니다.  
  
### <a name="to-modify-a-filter"></a>필터를 수정하려면  
  
1.  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]에서 수정하려는 추적 필터에 대한 템플릿을 엽니다. **파일** 메뉴에서 **템플릿**을 클릭한 다음 **템플릿 편집**을 선택합니다.  
  
2.  **추적 템플릿 속성** 대화 상자의 **일반** 탭에 있는 **템플릿 이름 선택** 목록에서 템플릿을 선택합니다.  
  
3.  **이벤트 선택** 탭을 클릭합니다.  
  
     **이벤트 선택** 탭에는 표 형태 컨트롤이 있습니다. 표 형태 컨트롤은 추적 가능한 각 이벤트 클래스가 들어 있는 테이블입니다. 테이블에는 각 이벤트 클래스에 대한 행이 하나씩 포함되어 있습니다. 이벤트 클래스는 사용자가 연결된 서버의 유형 및 버전에 따라 약간 다를 수 있습니다. 이벤트 클래스는 표의 **이벤트**열에서 식별되며 이벤트 범주별로 그룹화됩니다. 나머지 열은 각 이벤트 클래스에 대해 반환할 수 있는 데이터 열을 나열합니다.  
  
4.  **열 필터**를 클릭합니다.  
  
5.  **필터 편집** 대화 상자에서 편집하려는 비교 연산자 옆에 있는 값을 클릭하고 새 값을 입력하거나 값을 삭제합니다. 다른 필터를 추가할 수도 있습니다.  
  
6.  **확인** 을 클릭하여 템플릿을 저장합니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server 프로파일러](sql-server-profiler.md)  
  
  