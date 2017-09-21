---
title: "커서 유형 및 동시성 조합 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], concurrency options
- cursors [ODBC], ODBC driver for Oracle
- concurrency options [ODBC]
- ODBC driver for Oracle [ODBC], cursor options
ms.assetid: db63d610-f86f-4029-9d66-fed616c8a818
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a20223e272ce2790a8959df3d9f7ed318e700aef
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="cursor-type-and-concurrency-combinations"></a>커서 유형 및 동시성 조합
> [!IMPORTANT]  
>  이 기능은 나중 버전의 Windows에서 제거 됩니다. 새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 응용 프로그램은 수정하세요. Oracle에서 제공 하는 ODBC 드라이버를 사용 하십시오.  
  
 사용자에 게 제공 하는 커서의 기능을 제어 하는 커서 유형. 동시성 옵션 업데이트 허용 여부 및 결과 집합의 잠금 동작을 제어합니다.  
  
|커서 유형|동시성 (허용 되는 값)|  
|-----------------|------------------------------------|  
|SQL_CURSOR_FORWARD_ONLY|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_STATIC|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_KEYSET_DRIVEN<sup>[1]</sup>|SQL_CONCUR_READ_ONLY SQL_CONCUR_LOCK<sup>[2]</sup> SQL_CONCUR_VALUES|  
  
 <sup>[1] </sup> 참조 [키 집합 커서를 사용 하 여 제한인](../../odbc/microsoft/limitations-of-using-keyset-driven-cursors.md)합니다.  
  
 <sup>[2] </sup> SQL_CONCUR_LOCK SQL_AUTOCOMMIT 연결 옵션을 SQL_AUTOCOMMIT_OFF로 설정한 경우에 지원 됩니다.  
  
## <a name="see-also"></a>관련 항목:  
 [연결 옵션](../../odbc/microsoft/connect-options.md)