---
title: 추적 속성 (이벤트 선택 탭) | Microsoft Docs
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
- sql12.pro.traceproperties.eventsselection.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: e1892f24-7272-4d5d-8926-6150cc82b2c3
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 627785dc9be7d6b2d270d82f1bc6797c98980779
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36172950"
---
# <a name="trace-properties-events-selection-tab"></a>추적 속성(이벤트 선택 탭)
  **추적 속성** 대화 상자의 **이벤트 선택** 탭을 사용하여 추적된 이벤트 및 데이터 열의 속성을 확인하거나 지정할 수 있습니다.  
  
## <a name="options"></a>변수  
 **Events** 열  
 이벤트 열에서 확인란을 선택하거나 선택 취소하여 추적된 이벤트를 지정합니다. **Events** 는 이벤트 범주별로 구성됩니다. 템플릿에 지정된 이벤트 클래스는 자동으로 선택됩니다. 자세한 내용은 [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md)를 참조하세요.  
  
 데이터 열  
 원하는 이벤트 및 데이터 열에 해당하는 확인란을 선택하여 추적된 데이터 열을 지정합니다. 추적에 포함된 각 이벤트와 관련된 모든 이벤트 열이 기본적으로 선택됩니다.  
  
 데이터 열 머리글을 클릭하고 필터 조건을 입력하여 필터를 지정합니다. 필터링된 데이터 열은 **필터 편집** 대화 상자에서 열 레이블 왼쪽에 있는 필터 아이콘으로 표시됩니다. 자세한 내용은 [SQL Server Profiler - 필터 편집](../../2014/database-engine/sql-server-profiler-edit-filter.md)을 참조하세요.  
  
 **모든 이벤트 표시**  
 사용할 수 있는 모든 이벤트를 표시합니다. 기본적으로 **이벤트 선택** 표에서 선택된 행만 표시됩니다. **이벤트 선택** 표에서 선택되지 않은 모든 이벤트를 숨기려면 이 확인란의 선택을 취소합니다.  
  
 **모든 열 표시**  
 사용할 수 있는 모든 데이터 열을 표시합니다. 기본적으로 선택된 데이터 열만 표시됩니다. **이벤트 선택** 표에서 선택되지 않은 모든 데이터 열을 숨기려면 이 확인란의 선택을 취소합니다.  
  
 **열 필터**  
 **필터 편집** 대화 상자를 시작합니다. 이 대화 상자를 사용하여 데이터 열 필터를 편집할 수 있습니다.  
  
 **열 구성**  
 추적의 열 순서를 변경하고 결과를 하나 이상의 열로 그룹화합니다.  
  
## <a name="see-also"></a>관련 항목  
 [추적 파일에 대 한 이벤트 및 데이터 열 지정 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [추적에 표시 된 열 구성 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)   
 [추적에서 이벤트를 필터링 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)   
 [필터 정보 보기&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)   
 [필터 수정 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)   
 [SQL Server Profiler 템플릿 및 권한](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server 프로파일러](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  