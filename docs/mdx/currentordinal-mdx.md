---
title: CurrentOrdinal (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d6fe956591b6bde0c5e6b074115fec8724995a59
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739342"
---
# <a name="currentordinal-mdx"></a>CurrentOrdinal(MDX)


  반복하는 동안 집합 내의 현재 반복 번호를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Set_Expression.CurrentOrdinal  
```  
  
## <a name="arguments"></a>인수  
 *Set_Expression*  
 집합을 반환하는 유효한 MDX 식입니다.  
  
## <a name="remarks"></a>Remarks  
 와 같은 집합을 통해 반복 하는 경우는 [Filter (MDX)](../mdx/filter-mdx.md) 또는 [Generate (MDX)](../mdx/generate-mdx.md) 함수는 **CurrentOrdinal** 함수 반복 번호를 반환 합니다.  
  
## <a name="examples"></a>예  
 간단한 예에서는 다음 방법을 **CurrentOrdinal** 함께 사용할 수 있습니다 **생성** 집합에서의 위치가 집합의 각 항목의 이름을 포함 하는 문자열을 반환 하려면:  
  
 `WITH SET MySet AS [Customer].[Customer Geography].[Country].MEMBERS`  
  
 `MEMBER MEASURES.CURRENTORDINALDEMO AS`  
  
 `GENERATE(MySet, CSTR(MySet.CURRENTORDINAL) + ") " + MySet.CURRENT.ITEM(0).NAME, ", ")`  
  
 `SELECT MEASURES.CURRENTORDINALDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
 CurrentOrdinal은 매우 복잡한 계산에서만 일반적으로 사용됩니다. 사용 하 여 고유한 집합에 제품의 수를 반환 하는 다음 예제는 **순서** 이용 하기 전에 먼저 비어 있지 않은 튜플을 정렬 하는 함수는 **필터** 함수입니다. **CurrentOrdinal** 함수를 비교 하 고 동률 제거를 사용 합니다.  
  
```  
WITH MEMBER [Measures].[PrdTies] AS Count  
   (Filter  
      (Order  
        (NonEmpty  
          ([Product].[Product].[Product].Members  
          , {[Measures].[Reseller Order Quantity]}  
          )  
       , [Measures].[Reseller Order Quantity]  
       , BDESC  
       ) AS OrdPrds  
    , NOT((OrdPrds.CurrentOrdinal < OrdPrds.Count   
       AND [Measures].[Reseller Order Quantity] =   
          ( [Measures].[Reseller Order Quantity]  
            , OrdPrds.Item  
               (OrdPrds.CurrentOrdinal  
               )  
            )  
         )  
         OR (OrdPrds.CurrentOrdinal > 1   
            AND [Measures].[Reseller Order Quantity] =   
               ([Measures].[Reseller Order Quantity]  
               , OrdPrds.Item  
                  (OrdPrds.CurrentOrdinal-2)  
                )  
             )  
          ))  
       )  
SELECT {[Measures].[PrdTies]} ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>관련 항목  
 [MDX 함수 참조 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
