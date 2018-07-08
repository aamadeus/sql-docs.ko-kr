---
title: KPI 브라우저 (Kpi 탭, 큐브 디자이너) (Analysis Services-다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubeeditor.kpibrowserpane.f1
ms.assetid: 2f61bde6-e6ec-4511-8645-c272374014ad
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 32373127f72dae058a80712cec564af7dffca45e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180765"
---
# <a name="kpi-browser-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a>KPI 브라우저(KPI 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)
  큐브 디자이너의 **KPI** 탭에 있는 **KPI 브라우저** 창을 사용하여 KPI(핵심 성과 지표)의 결과를 보고 테스트할 수 있습니다. 검색하기 전에 먼저 KPI를 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 배포해야 합니다.  
  
> [!NOTE]  
>  이 창은 브라우저 보기에만 표시됩니다.  
  
## <a name="options"></a>변수  
 **하위 큐브 표**  
 하위 큐브를 정의하고 **결과** 창에 표시할 KPI 결과를 제한하려면 사용합니다. 표에는 다음 열이 있습니다.  
  
 **Dimension**  
 이 필터를 적용할 차원을 선택합니다.  
  
 **Hierarchy**  
 이 필터를 적용할 계층을 선택합니다.  
  
 **같음**  
 **필터 식** 의 식이 선택한 계층에 적용되는 방법을 정의하는 연산자를 선택합니다. 다음 표에서는 사용 가능한 연산자에 대해 설명합니다.  
  
|값|Description|  
|-----------|-----------------|  
|**같음**|**필터 식**에서 정의한 집합으로 결과가 제한됩니다.|  
|**같지 않음**|**필터 식**에서 정의한 집합에서 제외된 멤버로 결과가 제한됩니다.|  
|**입력**|**필터 식**에서 선택한 명명된 집합으로 결과가 제한됩니다.|  
|**안 함**|**필터 식**에서 선택한 명명된 집합에서 제외된 멤버로 결과가 제한됩니다.|  
|**포함**|이름에 **필터 식**의 문자열이 포함된 멤버로 결과가 제한됩니다.|  
|**로 시작**|이름이 **필터 식**의 문자열로 시작하는 멤버로 결과가 제한됩니다.|  
|**범위 (포함)**|**필터 식**에서 선택한 범위로 결과가 제한됩니다.|  
|**범위 (제외)**|**필터 식**에서 선택한 범위에서 제외된 멤버로 결과가 제한됩니다.|  
|**MDX**|**필터 식**에서 설정한 MDX(Multidimensional Expression) 식으로 결과가 제한됩니다.|  
  
 **필터 식**  
 **연산자**를 사용하여 계산할 식을 입력합니다. 이 식은 검색할 KPI를 제한합니다.  
  
> [!NOTE]  
>  이 필드는 선택한 연산자에 필요한 데이터 형식에 따라 모양이 변경되는 동적 데이터 입력 요소입니다.  
  
 **결과 표**  
 **필터 표**에 정의된 필터를 기준으로 평가한 KPI의 값, 목표, 상태 및 추세를 표시합니다. 표에는 다음 열이 있습니다.  
  
 **표시 구조**  
 큐브에 포함된 KPI를 각 KPI에 대한 **표시 폴더** 또는 **부모 KPI** 값에 따라 계층적으로 구성하여 표시합니다.  
  
 **Value**  
 KPI 값을 표시합니다.  
  
 **목표**  
 KPI의 목표 값을 표시합니다.  
  
 **상태**  
 KPI의 상태 그래픽을 표시합니다.  
  
 **추세**  
 KPI의 추세 그래픽을 표시합니다.  
  
 **Weight**  
 KPI의 가중치 요인을 표시합니다.  
  
 **(설명)**  
 KPI에 대한 설명이 제공된 경우 정보 아이콘을 표시합니다.  
  
 정보 아이콘을 마우스로 가리키면 KPI에 대한 설명이 포함된 도구 설명이 표시됩니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에서 KPI를 계산하는 동안 오류가 발생하면 이 옵션은 해당 오류와 관련된 정보를 표시합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Kpi &#40;큐브 디자이너&#41; &#40;Analysis Services-다차원 데이터&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md)  
  
  