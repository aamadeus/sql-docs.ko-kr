---
title: '! (논리적 Not)(SSIS 식) | Microsoft Docs'
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
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7de99bf9dc767c5f4f6e47abd88f66f874ebb1be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36080219"
---
# <a name="-logical-not-ssis-expression"></a>! (논리적 Not)(SSIS 식)
  부울 피연산자를 부정합니다.  
  
> [!NOTE]  
>  ! 연산자는 다른 연산자와 함께 사용할 수 없습니다. 예를 들어 ! 연산자와 > 연산자를 !> 연산자로 결합할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a>인수  
 *boolean_expression*  
 부울로 계산되는 유효한 식입니다. 자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.  
  
## <a name="result-types"></a>결과 형식  
 DT_BOOL  
  
## <a name="remarks"></a>Remarks  
 다음 표에서는 ! 연산의 결과를 지정합니다.  
  
|원래 부울 식|! 연산자를 적용한 후|  
|---------------------------------|------------------------------------|  
|TRUE|FALSE|  
|NULL|NULL|  
|FALSE|TRUE|  
  
## <a name="expression-examples"></a>식 예  
 이 예에서는 **Color** 열의 값이 "red"이면 FALSE가 됩니다.  
  
```  
!(Color == "red")  
```  
  
 이 예에서는 **MonthNumber** 변수 값이 현재 월을 나타내는 정수와 같으면 TRUE가 됩니다. 자세한 내용은 [MONTH&#40;SSIS 식&#41;](month-ssis-expression.md) 및 [GETDATE&#40;SSIS 식&#41;](getdate-ssis-expression.md)를 참조하세요.  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a>관련 항목  
 [연산자 우선순위 및 결합성](operator-precedence-and-associativity.md)   
 [연산자 &#40;SSIS 식&#41;](operators-ssis-expression.md)  
  
  