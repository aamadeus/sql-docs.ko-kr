---
title: Leaves (MDX) | Microsoft Docs
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
- LEAVES
dev_langs:
- kbMDX
helpviewer_keywords:
- Leaves function
ms.assetid: 09f908aa-1b2d-4af9-8c8d-c023915241b2
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0c6201939c5bfb6f5ad61c009aac5a7e4740af63
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="leaves-mdx"></a>Leaves(MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  모든 특성 또는 특정 차원에만 속하는 특성으로 구성된 집합을 반환합니다. 반환된 집합의 각 x 특성의 경우, x가 세분성 특성이거나 세분성 특성에 직접 또는 간접적으로 관련되어 있으면 해당 세분성은 조각에 영향을 주지 않고 x 특성에 대해 설정됩니다. **둡니다** 함수는 SCOPE 문 내에 또는 대입의 왼쪽에 사용 하기 위해 설계 되었습니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Leaves( [ Dimension_expression ] )  
```  
  
## <a name="arguments"></a>인수  
 *Dimension_Expression*  
 차원을 반환하는 유효한 MDX(Multidimensional Expressions) 식입니다.  
  
## <a name="remarks"></a>주의  
 리프 멤버는 모든 특성 계층에 대한 가장 낮은 수준의 크로스 조인으로 형성된 튜플입니다. 계산 멤버는 제외됩니다.  
  
-   차원 이름이 지정 되는 **둡니다** 함수는 지정 된 차원에 대 한 키 특성의 리프 멤버를 포함 하는 집합을 반환 합니다.  
  
-   차원이 여러 측정값 그룹과 연결된 경우 현재 범위의 측정값 차원이 사용됩니다.  
  
-   차원 이름이 지정되지 않은 경우 이 함수는 전체 큐브의 리프 멤버가 포함된 집합을 반환합니다.  
  
    > [!NOTE]  
    >  차원 식이 계층으로 확인되고 계층 고유 이름이 차원 고유 이름과 같은 경우, 즉 큐브 차원 속성 HierarchyUniqueNameStyle이 ExcludeDimensionName이고 계층 이름이 차원 이름과 같으면 해당 차원이 사용됩니다.  
  
    > [!IMPORTANT]  
    >  현재 범위의 측정값 그룹에서 일부 특성의 세분성이 같지 않으면 오류가 생성됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [MDX 함수 참조 &#40; Mdx&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
