---
title: CEILING(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bb8882090de6302d6abeaa7ee8112ca31112e938
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084943"
---
# <a name="ceiling-ssis-expression"></a>CEILING(SSIS 식)
  숫자 식보다 크거나 같은 최소 정수를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
CEILING(numeric_expression)  
```  
  
## <a name="arguments"></a>인수  
 *numeric_expression*  
 유효한 숫자 식입니다.  
  
## <a name="result-types"></a>결과 형식  
 함수에 전달된 숫자 식의 데이터 형식입니다.  
  
## <a name="remarks"></a>Remarks  
 인수가 Null이면 CEILING 결과도 Null입니다.  
  
## <a name="expression-examples"></a>식 예  
 이 예에서는 양수, 음수 및 0 값에 CEILING 함수를 적용합니다.  
  
```  
CEILING(123.74)  
```  
  
 124.00을 반환합니다.  
  
```  
CEILING(-124.27)  
```  
  
 -124.00을 반환합니다.  
  
```  
CEILING(0.00)  
```  
  
 0.00을 반환합니다.  
  
## <a name="see-also"></a>관련 항목  
 [FLOOR &#40;SSIS 식&#41;](floor-ssis-expression.md)   
 [함수 &#40;SSIS 식&#41;](functions-ssis-expression.md)  
  
  
