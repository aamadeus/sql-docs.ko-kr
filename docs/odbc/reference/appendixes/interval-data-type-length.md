---
title: "간격 데이터 형식 길이 | Microsoft Docs"
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
- data types [ODBC], interval data types
- length of data types [ODBC]
- interval data type [ODBC], length
ms.assetid: e9eb38d8-f9db-4401-8c62-aa394054cbbf
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e642685b670fa872c1a34d2d10fed815e5a6fa7e
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="interval-data-type-length"></a>간격 데이터 형식의 길이입니다.
다음 규칙은 문자에서 간격 데이터 형식의 길이 확인 하는 데 사용 됩니다. 길이 문자 수로 표시 됩니다. 바이트 수가 경우 문자 집합에 따라 달라 집니다. 길이 함께 추가 하는 다음 값에 포함 됩니다.  
  
-   선행 필드가 간격 내에 모든 필드에 대해 두 문자입니다.  
  
-   선행 필드에 대 한 명시적 또는 암시적 사용 되는 문자 수는 전체 자릿수를 유도 합니다. 선행 정밀도 지정 하지 않으면 기본값은 2입니다.  
  
-   필드 사이의 구분 기호에 대 한 문자입니다.  
  
-   1을 더한 명시적 또는 묵시적 초 전체 자릿수입니다. 초 전체 자릿수를 지정 하지 않으면 기본값은 6입니다.  
  
 각 간격 데이터 형식에 대 한 특정 열 길이 값에 포함 되어 [열 크기](../../../odbc/reference/appendixes/column-size.md)합니다.