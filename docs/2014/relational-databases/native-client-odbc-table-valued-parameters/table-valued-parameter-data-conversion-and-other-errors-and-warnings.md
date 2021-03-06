---
title: 테이블 반환 매개 변수 데이터 변환과 기타 오류 및 경고 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e2fc0e9889c5872280ef4d5f0baf00f84b88ef99
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48176273"
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a>테이블 반환 매개 변수 데이터 변환과 기타 오류 및 경고
  다른 열 및 매개 변수 값과 동일한 방식으로 클라이언트와 서버 데이터 형식 간에 테이블 반환 매개 변수 열 값을 변환할 수 있습니다. 하지만 테이블 반환 매개 변수에는 다중 열과 다중 행이 포함될 수 있으므로 오류가 발생한 실제 값을 확인하는 것이 필요합니다.  
  
 테이블 반환 매개 변수 열에서 오류나 경고가 검색된 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client는 진단 레코드를 생성합니다. 오류 메시지에는 테이블 반환 매개 변수의 매개 변수 번호와 열 서수 및 행 번호가 들어 있습니다. 응용 프로그램에서는 진단 레코드의 진단 필드 SQL_DIAG_SS_TABLE_COLUMN_NUMBER 및 SQL_DIAG_SS_TABLE_ROW_NUMBER를 사용하여 오류 및 경고와 연관된 값을 확인할 수 있습니다. 이러한 진단 필드는 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 버전에서 사용 가능합니다.  
  
 진단 레코드의 SQLSTATE 및 메시지 구성 요소는 모든 측면에서 기존 ODBC 동작을 따릅니다. 즉, 매개 변수, 행 및 열 식별 정보를 제외하면 테이블 반환 매개 변수와 테이블 반환 매개 변수가 아닌 매개 변수에 대한 오류 메시지가 동일한 값을 갖습니다.  
  
## <a name="see-also"></a>관련 항목  
 [테이블 반환 매개 변수 &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
