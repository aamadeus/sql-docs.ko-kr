---
title: "검색 결과 집합 정보 (ODBC) | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bd99d4fe84bf7ceb09b90d19dd5ec12b26c272c9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="processing-results---retrieve-result-set-information"></a>처리 결과-결과 집합 정보 검색
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
### <a name="to-get-information-about-a-result-set"></a>결과 집합에 대한 정보를 가져오려면  
  
1.  호출 [SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) 결과 집합의 열 개수를 가져올 수 있습니다.  
  
2.  결과 집합의 각 열에 대해 다음을 수행합니다.  
  
    -   호출 [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) 결과 열에 대 한 정보를 얻을 수 있습니다.  
  
     또는  
  
    -   호출 [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) 결과 열에 대 한 특정 설명자 정보를 가져올 수 있습니다.  
  
## <a name="see-also"></a>관련 항목:  
[처리 결과 &#40; ODBC &#41;](../../relational-databases/native-client-odbc-how-to/processing-results-process-results.md)

[특성은 결과 집합 &#40; ODBC &#41;를 결정합니다.](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  