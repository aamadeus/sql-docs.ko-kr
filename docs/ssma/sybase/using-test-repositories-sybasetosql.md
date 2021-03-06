---
title: 테스트 리포지토리 (SybaseToSQL)를 사용 하 여 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Test Repositories
ms.assetid: c359c25c-db2a-4a20-afa9-62d87a62df72
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: fc4d537901d0352725260fadf1cb4446cb764419
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731121"
---
# <a name="using-test-repositories-sybasetosql"></a>테스트 리포지토리 사용(SybaseToSQL)
SSMA 테스트 리포지토리 저장소 SSMA 테스터가 테스트 사례와 나중에 사용할 테스트 결과입니다. 리포지토리 데이터를 SQL Server 테이블에 저장 됩니다 **TestCaseRepository** 하 고 **RunTestCaseResultRepository** 스키마에서 **ssma_sybase_utilities** 의**ssmatesterdb_syb** 데이터베이스입니다.  
  
테스트 사례 저장소 대화 상자에서 다음 단추는 사용할 수 있습니다.  
  
-   클릭 합니다 **새로 고침** 테스트 사례 또는 테스트 결과 목록을 새로 고치려면 단추입니다.  
  
-   클릭 합니다 **닫습니다** 테스트 사례 저장소 대화 상자를 닫으려면 단추입니다.  
  
## <a name="test-cases-repository"></a>테스트 사례 리포지토리  
클릭 하 여 테스트 사례 저장소를 볼 수 있습니다 **테스트 사례는 중...** **테스터** 메뉴. SSMA 다음 표시는 **리포지토리의 테스트 사례** 에 저장 된 테스트 사례의 목록 사용 하 여 대화 상자 창 합니다 **테스트 사례** 페이지.  
  
표 형식으로 각 테스트 사례에 대 한 다음 정보를 표시 합니다.  
  
-   이름: 테스트 사례 이름입니다.  
  
-   작성: 테스트 사례 생성 날짜입니다.  
  
-   수정된: 테스트 사례를 마지막으로 수정한 날짜입니다.  
  
-   설명: 테스트 사례 설명입니다.  
  
다음 단추는 테스트 사례 페이지 에서도 다운로드 가능:  
  
-   클릭 합니다 **추가** 단추를 테스트 사례 마법사를 실행 하 고 새 테스트를 만듭니다.  
  
-   클릭 합니다 **제거** 리포지토리에서 선택한 테스트를 삭제 하려면 단추입니다. 테스트 사례를 삭제 하면 모든 관련된 테스트 결과 삭제 됩니다.  
  
-   클릭 합니다 **편집** 테스트 사례 마법사를 실행 하 고 선택한 테스트를 변경 하는 단추입니다.  
  
-   클릭는 **실행** 버튼을 클릭 하는 [테스트 사례 실행 &#40;SybaseToSQL&#41; ](../../ssma/sybase/running-test-cases-sybasetosql.md) 대화 하 고 선택한 테스트를 실행 합니다.  
  
## <a name="test-results-repository"></a>테스트 결과 리포지토리  
테스트 결과 리포지토리를 볼 수 있습니다 합니다 **테스트 결과** 페이지의 **저장소의 테스트 사례** 창. 클릭 하 여 열 **테스트 결과 중...** **테스터** 메뉴.  
  
두 개의 필터를 사용할 수 있습니다 **테스트 결과** 페이지:  
  
-   테스트 사례 이름 필터: 테스트 사례 이름으로 테스트 결과 선택 합니다. 이 필터 **모든 테스트 사례** 값을 사용 하면 모든 테스트 사례에 대 한 테스트 결과 표시 합니다.  
  
-   테스트 사례 실행 날짜 필터: 필터 테스트 결과 저장 하는 날짜입니다. 이 필터 **모든 기간** 값을 사용 하면 저장 하는 모든 날짜에 대 한 테스트 결과 표시 합니다.  
  
테스트 결과 대해 다음 정보는 표에 표시 됩니다.  
  
-   이름: 테스트 사례 이름입니다.  
  
-   시작: 테스트 실행의 경우 날짜입니다.  
  
-   결과: (이 셀의 도구 설명 전체 테스트 실행 요약을 표시 하는 데 사용) 테스트 실행에 대 한 짧은 요약 합니다.  
  
다음 단추는 테스트 결과 페이지에서 사용할 수 있습니다.  
  
-   클릭 합니다 **보기** 버튼을 클릭 하 [테스트 사례 보고서 보기 &#40;SybaseToSQL&#41; ](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md) 현재 테스트 사례 결과입니다.  
  
-   클릭 합니다 **삭제** 선택한 테스트 결과 삭제 하려면 단추  
  
## <a name="see-also"></a>관련 항목  
[테스트 사례 실행 &#40;SybaseToSQL&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[마이그레이션된 데이터베이스 개체 테스트 &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
