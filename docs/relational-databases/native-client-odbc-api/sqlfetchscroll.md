---
title: SQLFetchScroll | Microsoft Docs
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a1f60dc7742e6b0df60390d56a6338b355a621f2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sqlfetchscroll"></a>SQLFetchScroll
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLFetchScroll** 응용 프로그램에 데이터의 한 행 집합을 반환 합니다. 행 집합의 크기를 사용 하 여 설정 됩니다 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 다음과 같은 제한 사항이 모든 정의 된 인출 명령 (예: SQL_FETCH_RELATIVE)를 지원 합니다.  
  
-   문에 대해 정방향 전용 커서가 정의된 경우 SQL_FETCH_NEXT가 필요하며, 다른 방식으로 인출을 시도하면 오류가 반환됩니다.  
  
-   SQL_FETCH_BOOKMARK는 정적 및 키 집합 커서에 대해서만 지원됩니다.  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a>향상된 날짜 및 시간 기능에 대한 SQLFetchScroll 지원  
 날짜/시간 형식의 결과 열 값에 설명 된 대로 변환 됩니다 [SQL에서 C로 변환을](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)합니다.  
  
 자세한 내용은 참조 [날짜 및 시간 기능 향상 &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)합니다.  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a>큰 CLR UDT에 대한 SQLFetchScroll 지원  
 **SQLFetchScroll** 큰 CLR 사용자 정의 형식 (Udt)을 지원 합니다. 자세한 내용은 참조 [Large CLR User-Defined 형식 &#40; ODBC &#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLFetchScroll 함수](http://go.microsoft.com/fwlink/?LinkId=59343)   
 [ODBC API 구현 정보](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  