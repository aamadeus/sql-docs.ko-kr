---
title: 추적 실행을 위한 Transact-SQL 스크립트 만들기(SQL Server Profiler) | Microsoft Docs
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
- traces [SQL Server], running
- scripts [SQL Server], traces
ms.assetid: 6b0e2519-998d-40d5-b8ba-5e6a773f91a6
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cbddb6363999585403f47bc1660bf2b1a26b4b04
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36092792"
---
# <a name="create-a-transact-sql-script-for-running-a-trace-sql-server-profiler"></a>추적 실행을 위한 Transact-SQL 스크립트 만들기(SQL Server Profiler)
  이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 기존 추적 파일 또는 테이블에서 Transact-SQL 스크립트를 만드는 방법에 대해 설명합니다.  
  
### <a name="to-create-a-transact-sql-script-to-run-a-trace"></a>추적을 실행하도록 Transact-SQL 스크립트를 만들려면  
  
1.  추적 파일 또는 테이블을 엽니다. 자세한 내용은 [추적 파일 열기&#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) 또는 [추적 테이블 열기&#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)를 참조하세요.  
  
2.  **파일** 메뉴에서 **내보내기**, **추적 정의 스크립팅**을 차례로 가리킨 다음 추적할 서버에 해당하는 버전을 클릭합니다.  
  
3.  **다른 이름으로 저장** 대화 상자에서 스크립트 파일의 이름을 입력한 다음 **저장**을 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server Profiler 템플릿 및 권한](sql-server-profiler-templates-and-permissions.md)   
 [SQL Server 프로파일러](sql-server-profiler.md)  
  
  