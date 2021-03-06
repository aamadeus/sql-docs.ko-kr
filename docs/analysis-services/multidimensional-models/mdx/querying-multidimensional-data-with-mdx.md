---
title: MDX 사용 하 여 다차원 데이터 쿼리 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fe45a4f8fab7066ff3f606210774463f14559af7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34021696"
---
# <a name="querying-multidimensional-data-with-mdx"></a>MDX를 사용하여 다차원 데이터 쿼리
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  MDX(Multidimensional Expression)는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]에서 다차원 데이터를 처리하고 검색하는 데 사용하는 쿼리 언어입니다. MDX는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]를 위한 특정 확장이 포함된 XMLA(XML for Analysis) 사양을 기반으로 합니다. MDX에서 사용되는 식은 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 에서 집합 또는 멤버와 같은 개체나 문자열 또는 숫자와 같은 스칼라 값을 검색하기 위해 평가할 수 있는 식별자, 값, 문, 함수 및 연산자로 구성됩니다.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 의 MDX 쿼리 및 식을 사용하여 다음을 수행할 수 있습니다.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 큐브의 데이터를 클라이언트 응용 프로그램에 반환할 수 있습니다.  
  
-   쿼리 결과의 형식을 지정할 수 있습니다.  
  
-   계산 멤버, 명명된 집합, 범위 할당 및 KPI(핵심 성과 지표)의 정의를 비롯한 큐브 디자인 태스크를 수행할 수 있습니다.  
  
-   차원 및 셀 보안 등의 관리 태스크를 수행할 수 있습니다.  
  
 MDX는 외견상으로는 관계형 데이터베이스에서 일반적으로 사용되는 SQL 구문과 여러 면에서 비슷합니다. 그러나 MDX는 SQL 언어의 확장이 아니며 여러 면에서 SQL과는 다릅니다. 큐브를 디자인하거나 보호하는 데 사용되는 MDX 식을 만들거나 다차원 데이터를 반환하고 형식을 지정하기 위한 MDX 쿼리를 만들려면 MDX 및 차원 모델링의 기본 개념과 MDX 구문 요소, MDX 연산자, MDX 문, MDX 함수 등에 대해 이해하고 있어야 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
|항목|Description|  
|-----------|-----------------|  
|[MDX & #40;의 주요 개념 Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)|MDX(Multidimensional Expression)를 사용하여 다차원 데이터를 쿼리하거나 큐브 내에서 사용할 MDX 식을 만들 수 있습니다. 그러나 이를 위해서는 먼저 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 차원의 개념과 용어를 이해해야 합니다.|  
|[MDX 쿼리 기본 사항 & #40; Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)|MDX(Multidimensional Expressions)를 사용하면 큐브와 같은 다차원 개체를 쿼리하여 큐브의 데이터를 포함하는 다차원 셀 집합을 반환할 수 있습니다. 이 항목 및 하위 항목에서는 MDX 쿼리에 대한 개요를 제공합니다.|  
|[MDX 스크립팅 기본 사항 & #40; Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]에서 MDX(Multidimensional Expression) 스크립트는 계산으로 큐브를 채우는 한 개 이상의 MDX 식 또는 문으로 구성됩니다.<br /><br /> MDX 스크립트는 큐브의 계산 프로세스를 정의합니다. MDX 스크립트는 또한 큐브 자체의 일부로 간주됩니다. 따라서 큐브와 관련된 MDX 스크립트를 변경하면 해당 큐브의 계산 프로세스가 즉시 변경됩니다.<br /><br /> [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]의 큐브 디자이너에서 MDX 스크립트를 작성할 수 있습니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [MDX 구문 요소 & #40; Mdx& #41;](../../../mdx/mdx-syntax-elements-mdx.md)   
 [MDX 언어 참조 & #40; Mdx& #41;](../../../mdx/mdx-language-reference-mdx.md)  
  
  
