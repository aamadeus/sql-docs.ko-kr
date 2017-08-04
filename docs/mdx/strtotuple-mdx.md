---
title: StrToTuple (MDX) | Microsoft Docs
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
- STRTOTUPLE
dev_langs:
- kbMDX
helpviewer_keywords:
- StrToTuple function
ms.assetid: e162cc01-cddd-4654-baab-d73abdc33b80
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e2ca9d105bf04c91fd2c65bea74f92a0d0ef1edd
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="strtotuple-mdx"></a>StrToTuple(MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  MDX(Multidimensional Expressions) 형식 문자열에 의해 지정된 튜플을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
StrToTuple(Tuple_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>인수  
 *Tuple_Specification*  
 직접 또는 간접적으로 튜플을 지정하는 유효한 문자열 식입니다.  
  
## <a name="remarks"></a>주의  
 **StrToTuple** 함수는 지정 된 집합을 반환 합니다. **StrToTuple** 함수는 대개에 MDX 문에 다시 외부 함수의 튜플 사양을 반환 사용자 정의 함수와 함께 사용 됩니다.  
  
-   CONSTRAINED 플래그를 사용할 경우 튜플 사양에는 정규화되거나 정규화되지 않은 멤버 이름을 포함해야 합니다. 이 플래그를 사용하면 지정한 문자열을 통한 삽입 공격 위험을 줄일 수 있습니다. 다음 오류가 표시 됩니다는 문자열이 직접 확인할 수 없는 정규화 되거나 정규화 되지 않은 멤버 이름이 아닌 경우 이면: "CONSTRAINED 설정한 제한을 STRTOTUPLE 함수에서 플래그 위반 했습니다."  
  
-   CONSTRAINED 플래그를 사용하지 않을 경우 지정한 튜플은 튜플을 반환하는 유효한 MDX 식으로 확인될 수 있습니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 2004년에 대한 Bayern 멤버의 Reseller Sales Amount 측정값을 반환합니다. 제공되는 튜플 사양에는 유효한 MDX 튜플 식이 포함됩니다.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].[CY 2004], [Measures].[Reseller Sales Amount])')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 다음 예에서는 2004년에 대한 Bayern 멤버의 Reseller Sales Amount 측정값을 반환합니다. 제공되는 튜플 사양에는 CONSTRAINED 플래그에 필요한 정규화된 멤버 이름이 포함됩니다.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].[CY 2004], [Measures].[Reseller Sales Amount])', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
  
```  
  
 다음 예에서는 2004년에 대한 Bayern 멤버의 Reseller Sales Amount 측정값을 반환합니다. 제공되는 튜플 사양에는 유효한 MDX 튜플 식이 포함됩니다.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].&[2003].NEXTMEMBER, [Measures].[Reseller Sales Amount])')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 다음 예에서는 CONSTRAINED 플래그로 인해 오류가 반환됩니다. 지정된 튜플 사양에 유효한 MDX 튜플 식이 들어 있지만 CONSTRAINED 플래그가 있으므로 튜플 사양에 정규화되거나 정규화되지 않은 멤버 이름이 필요합니다.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].&[2003].NEXTMEMBER, [Measures].[Reseller Sales Amount])', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>관련 항목:  
 [MDX 함수 참조 &#40; Mdx&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
