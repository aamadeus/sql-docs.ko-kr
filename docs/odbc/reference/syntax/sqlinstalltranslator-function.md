---
title: "SQLInstallTranslator 함수 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLInstallTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallTranslator
helpviewer_keywords:
- SQLInstallTranslator function [ODBC]
ms.assetid: 453b21ff-3c2b-4069-8ff7-5c727f062d89
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2b7efa21691627c346b6d3798ade158e946071e6
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlinstalltranslator-function"></a>SQLInstallTranslator 함수
**규칙**  
 ODBC 버전에 도입 된: 2.5에서는 사용 되지 않음  
  
 **요약**  
 ODBC 3.0에서 **SQLInstallTranslator** 로 대체 되었습니다 [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)합니다. 에 대 한 호출이 **SQLInstallTranslator** 매핑됩니다 **SQLInstallTranslatorEx**합니다. 자세한 내용은 참조 **SQLInstallTranslatorEx**합니다.  
  
 **SQLInstallTranslator** 응용 프로그램이 ODBC 3에서 호출 하는 경우에 FALSE를 반환 합니다*.x* 와 드라이버 관리자는 *lpszInfFile* 인수는 NULL이 아닌 값으로 설정 합니다. ODBC 2에 사용 된 Odbc.inf 파일입니다. *x* ODBC 3에서 더 이상 지원*.x*이전 버전과 호환성에 대 한도입니다.