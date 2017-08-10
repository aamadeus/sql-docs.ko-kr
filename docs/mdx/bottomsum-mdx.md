---
title: BottomSum (MDX) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BOTTOMSUM
dev_langs:
- kbMDX
helpviewer_keywords:
- BottomSum function
ms.assetid: b3b10e68-2a36-4c38-85f4-3bb7917d5ae8
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 7d36c2567ab73b299cb528430b3ede7d81cf1bc5
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="bottomsum-mdx"></a>BottomSum(MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  지정된 집합을 오름차순으로 정렬하고 합계가 지정된 값 이하가 되는 하위 값 튜플 집합을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
BottomSum(Set_Expression, Value, Numeric_Expression)  
```  
  
## <a name="arguments"></a>인수  
 *Set_Expression*  
 집합을 반환하는 유효한 MDX 식입니다.  
  
 *Value*  
 각 튜플과 비교할 기준 값을 지정하는 유효한 숫자 식입니다.  
  
 *Numeric_Expression*  
 숫자를 반환하는 셀 좌표의 유효한 숫자 식으로서, 일반적으로 MDX 식입니다.  
  
## <a name="remarks"></a>주의  
 **BottomSum** 함수 집합을 오름차순 정렬, 지정 된 집합에 대해 특정된 측정값의 합계를 계산 합니다. 그런 다음 지정된 숫자 식의 합계가 지정된 값(합계) 이상이 되는 하위 값 요소를 반환합니다. 이 함수는 누적 합계가 지정된 값 이상이 되는 집합의 가장 작은 하위 집합을 반환합니다. 반환되는 요소는 가장 작은 값에서 가장 큰 값 순서로 정렬됩니다.  
  
> [!IMPORTANT]  
>  **BottomSum** 같은 함수는 [TopSum](../mdx/topsum-mdx.md) 함수, 계층을 항상 무시 합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 2003 회계 연도 동안 Bike 범주에서 Geography 차원의 Geography 계층에 속하는 City 수준의 멤버 집합 중 Reseller Sales Amount 측정값을 사용한 누적 합계가 50,000 이상이 되는 가능한 한 작은 집합을 반환합니다. 이 집합은 판매량이 가장 적은 멤버부터 정렬됩니다.  
  
 `SELECT`  
  
 `[Product].[Product Categories].Bikes ON 0,`  
  
 `BottomSum`  
  
 `({[Geography].[Geography].[City].Members}`  
  
 `, 50000`  
  
 `, ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)`  
  
 `) ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])`  
  
## <a name="see-also"></a>관련 항목:  
 [MDX 함수 참조 &#40; Mdx&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
