---
title: Max 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 61c4d6ff-6435-456a-9cbd-5113d2113e8a
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 3beb38625d5bfc754676745ee20de13f3d48a7a2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157793"
---
# <a name="max-function-report-builder-and-ssrs"></a>Max 함수(보고서 작성기 및 SSRS)
  지정된 범위의 컨텍스트에서 식으로 지정된 Null이 아닌 모든 숫자 값의 최대값을 반환합니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>구문  
  
```  
  
Max(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *expression*  
 (`Variant`) 집계를 수행 하는 식입니다.  
  
 *범위*  
 (`String`) 선택 사항입니다. 집계 함수를 적용할 보고서 항목을 포함하는 데이터 집합, 그룹 또는 데이터 영역의 이름입니다. *scope* 를 지정하지 않은 경우 현재 범위가 사용됩니다.  
  
 *재귀*  
 (**열거 형식**) 선택 사항입니다. `Simple` (기본값) 또는 `RdlRecursive`합니다. 집계를 재귀적으로 수행할지 여부를 지정합니다.  
  
## <a name="return-type"></a>반환 형식  
 식 유형에 따라 결정됩니다.  
  
## <a name="remarks"></a>Remarks  
 식에 지정한 데이터 집합은 동일한 데이터 형식으로 구성되어야 합니다. 같은 변환 함수를 사용 하 여 동일한 데이터 형식으로 여러 숫자 데이터 형식이 포함 된 데이터를 변환할 `CInt`하십시오 `CDbl` 또는 `CDec`합니다. 자세한 내용은 [형식 변환 함수](http://go.microsoft.com/fwlink/?LinkId=96142)를 참조하세요.  
  
 *scope* 의 값은 문자열 상수여야 하고 식일 수 없습니다. 외부 집계나 다른 집계를 지정하지 않는 집계의 경우 *scope* 는 현재 범위나 포함하는 범위를 참조해야 합니다. 집계의 집계의 경우 중첩 집계는 자식 범위를 지정할 수 있습니다.  
  
 *Expression* 에는 다음 예외와 조건이 있는 중첩 집계 함수에 대한 호출이 포함될 수 있습니다.  
  
-   중첩 집계의*Scope* 는 외부 집계의 범위와 동일하거나 외부 집계의 범위에 포함되어야 합니다. 식에 있는 모든 고유 범위의 경우 한 범위는 다른 모든 범위에 대한 자식 관계에 있어야 합니다.  
  
-   중첩 집계의*Scope* 는 데이터 집합의 이름일 수 없습니다.  
  
-   *식을* 없어야 `First`, `Last`, `Previous`, 또는 `RunningValue` 함수입니다.  
  
-   *Expression* 에는 *recursive*를 지정하는 중첩 집계가 포함되지 않아야 합니다.  
  
 자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.  
  
 재귀 집계에 대한 자세한 내용은 [재귀 계층 구조 그룹 만들기&#40;보고서 작성기 및 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)를 참조하세요.  
  
## <a name="example"></a>예제  
 다음 코드 예에서는 `Year` 그룹 또는 데이터 영역의 가장 높은 합계를 제공합니다.  
  
```  
=Max(Fields!OrderTotal.Value, "Year")  
```  
  
## <a name="see-also"></a>관련 항목  
 [보고서에 사용 되는 식 &#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [합계, 집계 및 기본 제공 컬렉션의 식 범위 &#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
