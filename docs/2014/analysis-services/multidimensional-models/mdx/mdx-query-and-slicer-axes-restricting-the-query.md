---
title: 쿼리 및 Slicer 축 (MDX)으로 쿼리 제한 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], axes
- queries [MDX], axes
- axes [MDX]
- MDX [Analysis Services], axes
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e727b432afec1f42a6a111442c2263d6c48784de
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36183715"
---
# <a name="restricting-the-query-with-query-and-slicer-axes-mdx"></a>쿼리 및 Slicer 축으로 쿼리 제한(MDX)
  MDX(Multidimensional Expressions) SELECT 쿼리를 구성할 때 응용 프로그램에서는 일반적으로 큐브를 검토하고 계층 집합을 다음과 같이 두 개의 하위 집합으로 나눕니다.  
  
-   **Query 축**- 여러 멤버에 대해 데이터가 검색되는 계층 집합입니다. 쿼리 축에 대한 자세한 내용은 [쿼리 축의 내용 지정&#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)을 참조하세요.  
  
-   **Slicer 축**- 단일 멤버에 대해 데이터가 검색되는 계층 집합입니다. Slicer 축에 대한 자세한 내용은 [Slicer 축의 내용 지정&#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)을 참조하세요.  
  
 쿼리 및 slicer 축은 쿼리할 큐브의 여러 계층으로부터 구성될 수 있으므로, 이러한 용어는 MDX 쿼리로 반환된 큐브에서 생성되는 계층으로부터 쿼리할 큐브가 사용하는 계층을 구분하기 위해 사용됩니다.  
  
 쿼리 및 slicer 축을 사용하는 간단한 예제를 보려면 [간단한 예제에서 쿼리 및 Slicer 축 사용&#40;MDX&#41;](mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [멤버, 튜플 및 집합 작업 &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md)   
 [MDX 쿼리 기본 사항 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  