---
title: ODBC 커서로 자동 인출 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 177de8fe974d3aa4970f21607693a73c3da0b70e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36079740"
---
# <a name="using-autofetch-with-odbc-cursors"></a>ODBC 커서로 자동 인출 사용
  인스턴스에 연결 하는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 모든 서버 커서 유형을 사용 하는 경우 자동 인출 옵션을 지원 합니다. 자동 인출을 사용는 **SQLExecute** 또는 **SQLExecDirect** 하면 커서 함수 역시 암시적 [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST) 함수도 있습니다. 문 실행의 일부로 첫 번째 행 집합을 구성하는 행이 바인딩된 응용 프로그램 변수에 반환되므로 네트워크를 통해 다시 서버로 왕복할 필요가 없습니다. [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) 때 지원 되지 않습니다 자동 인출 옵션을 사용할 수 있습니다; 결과 집합 열을 프로그램 변수에 바인딩해야 합니다.  
  
 응용 프로그램은 드라이버별 SQL_SOPT_SS_CURSOR_OPTIONS 문 특성을 SQL_CO_AF로 설정하여 자동 인출을 요청합니다.  
  
## <a name="see-also"></a>관련 항목  
 [커서 프로그래밍 정보 &#40;ODBC&#41;](cursor-programming-details-odbc.md)  
  
  