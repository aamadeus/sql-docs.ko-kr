---
title: SIGN(SSIS 식) | Microsoft Docs
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
- positive values [Integration Services]
- SIGN function
- negative values
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a68d4a3879c173298b99c305702aaaf61d43a194
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36093354"
---
# <a name="sign-ssis-expression"></a>SIGN(SSIS 식)
  숫자 식의 양수(+1), 음수(-1) 또는 영(0) 부호를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
SIGN(numeric_expression)  
```  
  
## <a name="arguments"></a>인수  
 *numeric_expression*  
 유효한 부호 있는 숫자 식입니다. 자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.  
  
## <a name="result-types"></a>결과 형식  
 DT_I4  
  
## <a name="remarks"></a>Remarks  
 인수가 Null이면 SIGN 결과도 Null입니다.  
  
## <a name="expression-examples"></a>식 예  
 이 예에서는 숫자 리터럴의 부호가 반환됩니다. 반환 결과는 -1입니다.  
  
```  
SIGN(-123.45)  
```  
  
 이 예에서는 **DealerPrice** 열에서 **StandardCost** 열을 뺀 결과의 부호가 반환됩니다.  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## <a name="see-also"></a>관련 항목  
 [함수 &#40;SSIS 식&#41;](functions-ssis-expression.md)  
  
  