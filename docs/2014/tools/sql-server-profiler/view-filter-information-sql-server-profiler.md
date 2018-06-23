---
title: 필터 정보 (SQL Server Profiler) | Microsoft Docs
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
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7936ad4df64746697b5c9d0ff8f2be1c7a5cbef1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36090364"
---
# <a name="view-filter-information-sql-server-profiler"></a>필터 정보 보기(SQL Server Profiler)
  이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 이벤트 클래스의 데이터 열에서 필터를 보는 방법에 대해 설명합니다.  
  
### <a name="to-view-filter-information"></a>필터 정보를 보려면  
  
1.  추적 파일, 추적 테이블 또는 SQL 스크립트를 열고 **파일** 메뉴에서 **속성**을 클릭합니다. 추적 템플릿을 편집하거나 새 추적을 만들 경우에는 이 단계를 건너뛰십시오.  
  
2.  **이벤트 선택** 탭에서 보려는 필터의 데이터 열 이름을 마우스 오른쪽 단추로 클릭하고 **열 필터 편집**을 클릭합니다.  
  
3.  **필터 편집** 대화 상자에서 필터 비교 연산자를 확장하여 지정된 조건에 할당된 값을 확인합니다. 필터 정보를 보려는 모든 열에 대해 단계 2와 3을 반복합니다.  
  
> [!NOTE]  
>  할당 값이 있는 비교 연산자는 굵게 서식이 지정되어 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server 프로파일러](sql-server-profiler.md)  
  
  