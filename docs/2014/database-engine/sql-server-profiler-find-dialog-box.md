---
title: SQL Server 프로파일러-찾기 대화 상자 | Microsoft Docs
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
- sql12.pro.find.f1
helpviewer_keywords:
- Find dialog box
ms.assetid: dfaeec04-93d3-4214-9fc1-38b80179b36b
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 12c2fce80877fd14412558b673fa94662b712dba
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187463"
---
# <a name="sql-server-profiler---find-dialog-box"></a>SQL Server 프로파일러 - 찾기 대화 상자
  **찾기** 대화 상자를 사용하여 추적에서 특정 문자 또는 단어를 검색할 수 있습니다. 진행 중인 검색을 취소하려면 Esc 키를 누릅니다.  
  
 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]에서 이 대화 상자를 열려면 **편집** 메뉴에서 **찾기**를 클릭합니다.  
  
## <a name="options"></a>변수  
 **찾을 내용**  
 검색할 텍스트를 입력합니다. 검색은 지정한 문자열을 포함하는 모든 문자열과 일치합니다. 예를 들어 "Completed"에 대한 검색은 "SQL:BatchCompleted"와 일치합니다. 와일드카드 문자(*, ? 등)는 지원되지 않습니다.  
  
 **열에서 검색**  
 검색할 데이터 열을 클릭하거나 **\<All columns>** 를 클릭하여 추적에서 모든 데이터 열을 검색합니다.  
  
 **대/소문자 구분**  
 **찾을 내용** 상자에 입력한 텍스트와 대/소문자가 같은 텍스트를 찾습니다. 추적에서 대문자 및 소문자 텍스트로 이루어진 예를 모두 찾으려면 이 확인란의 선택을 취소합니다.  
  
 **단어 단위로**  
 전체 단어로 검색을 제한합니다. 단어 내의 문자 단위로 검색하려면 **단어 단위로** 확인란의 선택을 취소합니다.  
  
 **다음 찾기**  
 **다음 찾기** 상자에 입력한 문자의 다음 예를 찾습니다.  
  
 **이전 찾기**  
 추적에서 뒤로 검색하여 **다음 찾기** 상자에 입력한 문자의 이전 예를 찾습니다.  
  
## <a name="see-also"></a>관련 항목  
 [값 또는 추적 중에 데이터 열 찾기 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)   
 [추적 만들기 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)   
 [추적 테이블 열기&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)   
 [추적 파일 열기&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)   
 [SQL Server Profiler 템플릿 및 권한](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server 프로파일러](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  