---
title: Children (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d61eb168b01e9b6d48c4c003ba28d0f977026906
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740102"
---
# <a name="children-mdx"></a>Children(MDX)


  지정된 멤버의 자식 집합을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Member_Expression.Children  
```  
  
## <a name="arguments"></a>인수  
 *Member_Expression*  
 멤버를 반환하는 유효한 MDX 식입니다.  
  
## <a name="remarks"></a>Remarks  
 **자식** 함수는 지정 된 멤버의 자식을 포함 하는 일반적인 순서로 정렬 된 집합을 반환 합니다. 지정된 멤버에 자식이 없는 경우 이 함수는 빈 집합을 반환합니다.  
  
## <a name="example"></a>예제  
 다음 예에서는 Geography 차원에서 Geography 계층에 있는 United States 멤버의 자식을 반환합니다.  
  
```  
SELECT [Geography].[Geography].[Country].&[United States].Children ON 0  
FROM [Adventure Works]  
```  
  
 모든 멤버를 반환 하는 다음 예제는 **측정값** 차원 열 축에 여기에 모든 계산된 멤버와의 모든 자식 항목 집합의 `[Product].[Model Name]` 특성 계층에서 행 축에는 **Adventure Works** 큐브.  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
  
```  
  
|릴리스|기록|  
|-------------|-------------|  
|[!INCLUDE[ssBOL2005_R03](../includes/ssbol2005-r03-md.md)]|**변경 된 내용**<br /> -구문 및 인수를 명확 하 게 업데이트 합니다.<br /><br /> — 업데이트 된 예제를 추가 합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [MDX 함수 참조 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
