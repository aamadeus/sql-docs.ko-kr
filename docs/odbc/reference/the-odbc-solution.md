---
title: ODBC 솔루션 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], using ODBC
ms.assetid: 34b80790-e010-4b90-8eaa-03189f5d8986
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30ced2aec9d7b91f5c3df55a7d6bf1f7e8a69d1c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47822561"
---
# <a name="the-odbc-solution"></a>ODBC 솔루션
그런 다음 질문 기능 ODBC는 데이터베이스 액세스를 표준화 하는 방법 두 아키텍처 요구 사항을 가지 있습니다.  
  
-   응용 프로그램은 여러 Dbms 같은 소스 코드를 사용 하 여 다시 컴파일하거나 다시 링크 하지 않고 액세스할 수 있어야 합니다.  
  
-   응용 프로그램은 여러 Dbms를 동시에 액세스할 수 있어야 합니다.  
  
 그리고 marketplace 실제로 인해 자세한 질문 중 하나:  
  
-   ODBC는 DBMS 기능을 노출 해야? 기능만 모든 Dbms 또는 모든 DBMS에서 사용할 수 있는 모든 기능에 공통 되는?  
  
 ODBC는 다음과 같은 방식으로 이러한 문제를 해결 합니다.  
  
-   **ODBC 호출 수준 인터페이스입니다.** 응용 프로그램에서 동일한 소스 코드를 사용 하 여 여러 Dbms를 액세스 하는 방법의 문제를 해결 하려면 ODBC 표준 CLI를 정의 합니다. 모든 함수에서 Open Group 및 ISO/IEC CLI 사양에 포함 되며 일반적으로 응용 프로그램에 필요한 추가 기능을 제공 합니다.  
  
     다른 라이브러리 또는 드라이버에는 ODBC를 지 원하는 각 DBMS에 대 한 필요 합니다. 드라이버는 ODBC API 함수를 구현합니다. 다른 드라이버를 사용 하려면 응용 프로그램을 하지 않아도 컴파일하거나 합니다. 대신 응용 프로그램 단순히 새 드라이버를 로드 하 고에 함수를 호출 합니다. 여러 Dbms에 동시에 액세스 하려면 응용 프로그램이 여러 드라이버를 로드 합니다. 운영 체제별 경우 드라이버는 지원 되는 방법 예를 들어, Microsoft® Windows® 운영 체제 드라이버에 동적 연결 라이브러리 (Dll).  
  
-   **ODBC 표준 SQL 문법을 정의합니다.** 표준 호출 수준 인터페이스 외에도 ODBC 표준 SQL 문법을 정의합니다. 이 문법과 열기 그룹 SQL CAE 사양을 기반으로 합니다. 두 문법 차이점 부 이며 필요 하 고 SQL 문법 간의 차이로 인해 주로 SQL (Open Group) 및 CLI (ODBC)를 포함 합니다. 다루지 않는 Open Group 문법 일반적으로 사용 가능한 언어 기능을 노출 하는 문법을 일부 확장도 있습니다.  
  
     응용 프로그램에는 ODBC 또는 DBMS 관련 문법을 사용 하 여 문을 제출할 수 있습니다. 문에 특정 DBMS 문법에서 다른 ODBC 문법에서는 드라이버 데이터 원본에 전송 하기 전에 변환 합니다. 그러나 대부분의 Dbms는 이미 표준 SQL 문법을 사용 하기 때문에 이러한 변환이 드뭅니다.  
  
-   **ODBC는 드라이버 관리자를 여러 Dbms에 대 한 동시 액세스 관리를 제공 합니다.** 드라이버를 사용할 여러 Dbms를 동시에 액세스 하는 문제를 해결 하지만이 작업을 수행 하는 코드는 복잡할 수 있습니다. 모든 드라이버와 함께 작동 하도록 설계 된 응용 프로그램은 모든 드라이버를 정적으로 연결할 수 없습니다. 대신 런타임에 드라이버를 로드 합니다. 및 함수 포인터의 테이블을 통해 함수를 호출 해야 합니다. 상황이 더 복잡해 집니다 응용 프로그램이 동시에 여러 명의 드라이버를 사용 하는 경우.  
  
     이렇게 하려면 각 응용 프로그램에서 요구 하는 대신 ODBC 드라이버 관리자를 제공 합니다. 드라이버 관리자를 구현 하는 모든 ODBC 함수가-통과 드라이버에서 ODBC 함수 호출으로 주로-및 정적으로 응용 프로그램에 연결 되었거나 런타임에 응용 프로그램에서 로드 합니다. 따라서 응용 프로그램이 아닌 각 드라이버에 대 한 포인터 드라이버 관리자의 이름으로 ODBC 함수를 호출합니다.  
  
     응용 프로그램에서 특정 드라이버를 필요한 경우 먼저 그 다음으로 드라이버는 드라이버 관리자 드라이버를 로드 하는 요청을 식별 하는 연결 핸들을 요청 합니다. 드라이버 관리자는 드라이버를 로드 하 고 드라이버에서 각 함수의 주소를 저장 합니다. 드라이버에서 ODBC 함수를 호출 하려면 응용 프로그램이 드라이버 관리자에서 해당 함수를 호출 하 고 드라이버에 대 한 연결 핸들을 전달 합니다. 드라이버 관리자는 다음 이전에 저장 하는 주소를 사용 하 여 함수를 호출 합니다.  
  
-   **ODBC 많은 DBMS 기능을 노출 하지만 이들 모두를 지원 하기 위해 드라이버를 필요 하지 않습니다.** ODBC 모든 Dbms에 공통 되는 기능만 노출 하는 경우는 것이 거의 사용; 결국 이유는 여러 다른 Dbms 오늘날 존재 하므로 있다는 점입니다 다양 한 기능입니다. ODBC는 DBMS에서 사용할 수 있는 모든 기능에 노출 하는 경우는 것이 불가능 구현 하는 드라이버에 대 한 합니다.  
  
     ODBC는 많은 기능을 노출 하는 대신-대부분의 Dbms에서 지 원하는 것 보다 더-하지만 해당 기능의 하위 집합만 구현 하는 드라이버가 필요 합니다. 드라이버 원본 DBMS에서 지원 되는 경우에 또는 에뮬레이트할를 선택 하는 경우 나머지 기능을 구현 합니다. 따라서를 모두 Dbms에서 사용 하는 기능만 사용 하거나 특정 기능 지원에 대 한 확인 하 고 그에 따라 반응 하는 DBMS에 대 한 드라이버에 의해 노출 되는 단일 dbms 기능을 활용 하기에 응용 프로그램을 작성할 수 있습니다.  
  
     응용 프로그램 드라이버 기능을 확인할 수 있습니다 하 고 DBMS 지원, ODBC 두 함수를 제공 하는 (**SQLGetInfo** 하 고 **SQLGetFunctions**) 드라이버 및 DBMS에 대 한 일반 정보를 반환 하는 기능 및 함수의 목록은 드라이버를 지원합니다. ODBC는 API 및 SQL 문법 규칙 수준, 드라이버에서 지원 되는 기능의 광범위 한 범위를 지정 하는 정의 합니다. 자세한 내용은 [적합성 수준](../../odbc/reference/develop-app/conformance-levels.md)합니다.  
  
     ODBC를 노출 하는 기능을 모두에 대 한 공용 인터페이스를 정의 하는 기억 하는 것이 반드시 합니다. 이 인해 응용 프로그램 DBMS 관련 코드가 아닌 기능별 코드를 포함 하 고 이러한 기능을 노출 하는 모든 드라이버를 사용할 수 있습니다. 이의 장점 중 하나는 응용 프로그램 DBMS에서 지 원하는 기능 향상 된; 때 업데이트할 필요가 없습니다. 대신 업데이트 된 드라이버를 설치 하면 응용 프로그램이 자동으로 기능을 사용 기능별, 드라이버 관련 않거나 DBMS 관련 코드 이므로 합니다.
