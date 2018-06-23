---
title: 나누기(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- / (divide)
- divide operator (/)
ms.assetid: 5bde9223-872d-443e-8a27-57735e1d8f3d
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9a752a36cbe77c437dd7dbfd87bb8825237552d9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171994"
---
# <a name="divide-ssis-expression"></a>Divide (SSIS Expression)
  첫 번째 숫자 식을 두 번째 숫자 식으로 나눕니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
dividend / divisor  
  
```  
  
## <a name="arguments"></a>인수  
 *dividend*  
 나눌 숫자 식입니다. *dividend* 는 임의의 유효한 숫자 식일 수 있습니다. 자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.  
  
 *divisor*  
 피제수를 나눌 숫자 식입니다. *divisor* 는 0을 제외한 임의의 유효한 숫자 식일 수 있습니다.  
  
## <a name="result-types"></a>결과 형식  
 두 인수의 데이터 형식에 따라 결정됩니다. 자세한 내용은 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)을 참조하세요.  
  
## <a name="remarks"></a>Remarks  
 두 피연산자 중 하나가 Null이면 결과도 Null입니다.  
  
 0으로 나눌 수는 없습니다. *divisor* 하위 식의 계산 방법에 따라 다음 오류 중 하나가 발생합니다.  
  
-   계산 결과가 0인 *divisor* 하위 식이 상수이면 디자인 타임에 오류가 표시되어 식의 유효성 검사가 실패합니다.  
  
-   계산 결과가 0인 *divisor* 하위 식에 변수가 포함되어 있지만 입력 열이 없으면 해당 식이 속해 있는 구성 요소가 패키지 실행 전에 수행되는 실행 전 유효성 검사에 실패합니다.  
  
-   계산 결과가 0인 *divisor* 하위 식에 입력 열이 포함되어 있으면 런타임에 오류가 표시되고 데이터 흐름 구성 요소의 오류 흐름 규칙에 따라 처리됩니다.  
  
## <a name="expression-examples"></a>식 예  
 이 예에서는 두 개의 숫자 리터럴을 나눕니다.  
  
```  
25 / 5  
```  
  
 이 예에서는 **ListPrice** 열의 값을 **StandardCost** 열의 값으로 나눕니다.  
  
```  
ListPrice / StandardCost  
```  
  
## <a name="see-also"></a>관련 항목  
 [연산자 우선순위 및 결합성](operator-precedence-and-associativity.md)   
 [연산자 &#40;SSIS 식&#41;](operators-ssis-expression.md)  
  
  