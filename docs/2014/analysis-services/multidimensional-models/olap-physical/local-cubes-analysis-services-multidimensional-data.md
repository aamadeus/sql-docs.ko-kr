---
title: 로컬 큐브 (Analysis Services-다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], local
ms.assetid: e52e1515-35a7-4dc3-9bbf-736d176ba0c7
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bfb1b14d4dc540f13a98314d8cf299b78adf1550
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36092968"
---
# <a name="local-cubes-analysis-services---multidimensional-data"></a>로컬 큐브(Analysis Services - 다차원 데이터)
  로컬 큐브를 만들거나 업데이트하거나 삭제하려면 ASSL 스크립트나 AMO 프로그램을 작성하여 실행해야 합니다.  
  
 로컬 큐브와 로컬 마이닝 모델을 사용하면 네트워크에 연결되어 있지 않은 클라이언트 워크스테이션을 분석할 수 있습니다. 예를 들어 클라이언트 응용 프로그램은 다음 그림과 같이 로컬 큐브 엔진을 로드하여 로컬 큐브를 만들고 쿼리하는 OLAP 9.0 공급자(MSOLAP.3)용 OLE DB를 호출할 수 있습니다.  
  
 ![로컬 큐브 및 모델에 대 한 클라이언트 아키텍처](../../../analysis-services/dev-guide/media/as-localcubearch9.gif "로컬 큐브 및 모델에 대 한 클라이언트 아키텍처")  
  
 ADMOD.NET 및 AMO(Analysis Management Objects)도 로컬 큐브와 상호 작용할 때 로컬 큐브 엔진을 로드합니다. 로컬 큐브 엔진은 로컬 큐브에 연결할 때 로컬 큐브 파일을 배타적으로 잠그므로 단일 프로세스에서만 로컬 큐브 파일에 액세스할 수 있습니다. 단일 프로세스 내에서는 동시에 5개의 연결이 허용됩니다.  
  
 하나의 .cub 파일에는 두 개 이상의 큐브 또는 데이터 마이닝 모델이 있을 수 있습니다. 로컬 큐브 및 데이터 마이닝 모델에 대한 쿼리는 로컬 큐브 엔진에서 처리하므로 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스에 연결할 필요가 없습니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 및 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]를 사용하여 로컬 큐브를 관리할 수는 없습니다.  
  
## <a name="local-cubes"></a>로컬 큐브  
 로컬 큐브를 작성 및에 기존 큐브 채워진는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스 또는 관계형 데이터 원본입니다.  
  
|로컬 큐브 데이터의 원본|생성 방법|  
|------------------------------------|---------------------|  
|서버 기반 큐브|CREATE GLOBAL CUBE 문 중 하나를 사용할 수 있습니다 또는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ASSL (Scripting Language) 스크립트를 만들고 서버 기반 큐브에서 큐브를 채우는 합니다. 자세한 내용은 참조 [GLOBAL CUBE Statement 만들 &#40;MDX&#41; ](/sql/mdx/mdx-data-definition-create-global-cube) 또는 [Analysis Services Scripting Language &#40;ASSL&#41; 참조](../../scripting/analysis-services-scripting-language-assl-for-xmla.md)합니다.|  
|관계형 데이터 원본|ASSL 스크립트를 사용하여 OLE DB 관계형 데이터베이스에서 큐브를 만들고 채웁니다. ASSL을 사용하여 로컬 큐브를 만들려면 로컬 큐브 파일(*.cub)에 연결하고 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스에 대해 ASSL 스크립트를 실행하는 것과 같은 방식으로 ASSL 스크립트를 실행하여 서버 큐브를 만듭니다. 자세한 내용은 참조 [Analysis Services Scripting Language &#40;ASSL&#41; 참조](../../scripting/analysis-services-scripting-language-assl-for-xmla.md)합니다.|  
  
 REFRESH CUBE 문을 사용하여 로컬 큐브를 다시 생성하고 해당 데이터를 업데이트할 수 있습니다. 자세한 내용은 참조 [CUBE 문은 새로 고침 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-refresh-cube)합니다.  
  
### <a name="local-cubes-created-from-server-based-cubes"></a>서버 기반 큐브에서 만든 로컬 큐브  
 서버 기반 큐브에서 로컬 큐브를 만들 때는 다음과 같은 사항을 고려해야 합니다.  
  
-   고유 카운트 측정값이 지원되지 않습니다.  
  
-   측정값을 추가할 때 추가할 측정값과 관련된 하나 이상의 차원을 포함해야 합니다. 측정값 그룹 차원 관계에 대 한 자세한 내용은 참조 하십시오. [차원 관계](../../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)합니다.  
  
-   부모-자식 계층을 추가할 때 부모-자식 계층의 수준과 필터는 무시되고 전체 부모-자식 계층이 포함됩니다.  
  
-   멤버 속성이 생성되지 않습니다.  
  
-   반가산적 측정값을 포함할 때 계정 차원 및 시간 차원에 조각이 허용되지 않습니다.  
  
-   참조 차원이 항상 구체화됩니다.  
  
-   다 대 다 차원을 포함할 때는 다음과 같은 규칙이 적용됩니다.  
  
    -   다 대 다 차원을 조각화할 수 없습니다.  
  
    -   중간 측정값 그룹에서 측정값을 추가해야 합니다.  
  
    -   다 대 다 관계에 속한 두 측정값 그룹에 공통된 차원을 조각화할 수 없습니다.  
  
-   로컬 큐브에 추가된 측정값과 차원을 사용하는 계산 멤버, 명명된 집합 및 할당만 로컬 큐브에 나타납니다. 잘못된 계산 멤버, 명명된 집합 및 할당은 자동으로 제외됩니다.  
  
### <a name="security"></a>보안  
 서버 큐브에서 로컬 큐브를 만들려면 사용자에 대 한 순서로 사용자에 게 부여 해야 **드릴스루 및 로컬 큐브** 서버 큐브에 대 한 사용 권한입니다. 자세한 내용은 참조 [큐브 또는 모델 권한 부여 &#40;Analysis Services&#41;](../../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)합니다.  
  
 로컬 큐브는 서버 큐브와 같이 역할을 사용하여 보안이 설정되지 않습니다. 로컬 큐브 파일에 대한 파일 수준 액세스 권한이 있는 사용자는 누구나 해당 파일에 있는 큐브를 쿼리할 수 있습니다. 이를 방지하려면 로컬 큐브 파일의 `Encryption Password` 연결 속성을 사용하여 로컬 큐브 파일에 암호를 설정할 수 있습니다. 로컬 큐브 파일에 암호를 설정하면 로컬 큐브 파일을 쿼리하기 위해 해당 파일에 연결할 때 항상 이 암호를 입력해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [CREATE GLOBAL CUBE 문 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube)   
 [개발 analysis Services Scripting Language &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [REFRESH CUBE 문은 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-refresh-cube)  
  
  