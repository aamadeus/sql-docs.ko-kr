---
title: "파생 계층(Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "파생 계층"
  - "계층 [Master Data Services], 파생 계층"
  - "파생 계층, 파생 계층 정보"
ms.assetid: a0fbd519-a10e-4cbd-92e6-5de9b8d3e3f0
caps.latest.revision: 13
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 13
---
# 파생 계층(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 파생 계층은 모델의 엔터티 간에 이미 있는 도메인 기반 특성 관계에서 파생됩니다.  
  
 파생 계층을 만들어 모델의 기존 도메인 기반 특성 관계를 강조 표시할 수 있습니다.  
  
## 리프 멤버가 다른 리프 멤버를 그룹화함  
 파생 계층에서 한 엔터티의 리프 멤버가 다른 엔터티의 리프 멤버를 그룹화하는 데 사용됩니다. 파생 계층은 이러한 엔터티 간의 관계를 기반으로 합니다. 반면, 명시적 계층은 단일 엔터티만의 멤버를 기반으로 하며 지정하는 방법으로 구조화됩니다.  
  
 기본 데이터에 영향을 주지 않고 파생 계층의 구조를 변경할 수 있습니다. 모델에 관계가 존재하는 한 파생 계층을 삭제해도 마스터 데이터에는 아무 영향이 없습니다.  
  
## 명시적 계층과 파생 계층  
 다음 표에서는 명시적 계층과 파생 계층의 몇 가지 차이점을 보여 줍니다.  
  
> [!NOTE]  
>  명시적 계층의이 릴리스에서 지원 되지 않습니다 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]합니다.  
  
|명시적 계층|파생 계층|  
|--------------------------|-------------------------|  
|구조가 사용자에 의해 정의됨|구조가 도메인 기반 특성 간의 관계에서 파생됨|  
|단일 엔터티 멤버 포함|여러 엔터티 멤버 포함|  
|통합 멤버를 사용하여 다른 멤버를 그룹화함|한 엔터티의 리프 멤버를 사용하여 다른 엔터티의 리프 멤버를 그룹화함|  
  
## 가변 깊이 계층 구조 만들기  
 가변 깊이 계층 구조를 만드는 두 가지 권장 방법은 다음과 같습니다.  
  
-   모든 수준에 동일한 특성을 지정해야 하는 경우, 단일 엔터티를 만든 후 이 엔터티를 기반으로 하는 도메인 기반 특성을 사용해서 이 엔터티에 대해 재귀적 계층 구조를 만듭니다.  
  
-   상위 수준에 리프 멤버에 대한 특성 집합 하나와 다른 특성 집합 하나를 설정해야 할 경우, 파생된 계층 구조에 대해 두 개의 엔터티를 만듭니다. 리프 엔터티에 대해 부모 엔터티를 기반으로 하는 도메인 기반 특성을 사용합니다. 부모 엔터티에 대해서는 해당 엔터티 자체를 기반으로 하는 도메인 기반 특성을 사용합니다.  
  
## 파생 계층 예  
 다음 예에서는 Product 엔터티의 리프 멤버가 Subcategory 엔터티의 리프 멤버로 그룹화된 후 Subcategory 엔터티의 리프 멤버가 Category 엔터티의 리프 멤버로 그룹화됩니다. 이 계층은 Product 엔터티에 Subcategory라는 도메인 기반 특성이 있고 Subcategory 엔터티에 Category라는 도메인 기반 특성이 있기 때문에 가능합니다.  
  
 계층 구조는 멤버가 어떻게 그룹화되는지를 보여 줍니다. 멤버 수가 가장 많은 엔터티가 맨 아래에 있습니다.  
  
 ![모델 구조에서 파생된 계층](../master-data-services/media/mds-conc-derived-hierarchy-structure.gif "모델 구조에서 파생된 계층")  
  
 파생 계층에서 Product와 Subcategory 간의 관계를 강조 표시한 다음 Subcategory와 Category 간의 관계를 강조 표시할 수 있습니다. 이 계층의 멤버를 보면 트리의 각 수준에 같은 엔터티의 멤버가 포함되어 있습니다.  
  
 ![Mountain Bike 파생 계층 예제](../master-data-services/media/mds-conc-derived-hierarchy-example.gif "Mountain Bike 파생 계층 예제")  
  
 이 유형의 계층에서는 유효하지 않은 수준으로 멤버를 이동할 수 없습니다. 예들 들어 하나의 Subcategory, Road Bikes에서 다른 Subcategory, Mountain Bikes로 Road-650 bike를 이동할 수 있지만 1 {Bikes}와 같은 Category 바로 아래로 Road-650을 이동할 수는 없습니다. 계층 트리에서 멤버를 이동할 때마다 이를 반영하여 해당 멤버의 도메인 기반 특성 값이 변경됩니다.  
  
## 참고  
 파생 계층 트리의 모든 멤버가 코드순으로 정렬됩니다. 정렬 순서는 변경할 수 없습니다.  
  
 멤버의 도메인 기반 특성이 비어 있거나 특성이 파생 계층에 사용되는 경우 해당 멤버는 계층에 표시되지 않습니다. 특성을 채워야 하는 비즈니스 규칙을 만드십시오. 자세한 내용은 참조 [특성 값 요구 & #40; Master Data Services & #41;](../master-data-services/require-attribute-values-master-data-services.md)합니다.  
  
## 관련 태스크  
  
|태스크 설명|항목|  
|----------------------|-----------|  
|새 파생 계층을 만듭니다.|[파생된 계층 및 #40; 만들기 Master Data Services & #41;](../master-data-services/create-a-derived-hierarchy-master-data-services.md)|  
|기존 파생 계층의 수준을 숨기거나 삭제합니다.|[파생된 계층 & #40; 수준 숨기기 또는 삭제 Master Data Services & #41;](../master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|  
|기존 파생 계층의 이름을 변경합니다.|[파생된 계층 이름 & #40; 변경 Master Data Services & #41;](../master-data-services/change-a-derived-hierarchy-name-master-data-services.md)|  
|기존 파생 계층을 삭제합니다.|[파생된 계층 & #40; 삭제 Master Data Services & #41;](../master-data-services/delete-a-derived-hierarchy-master-data-services.md)|  
  
## 관련 내용  
  
-   [도메인 기반 특성 & #40입니다. Master Data Services & #41;](../master-data-services/domain-based-attributes-master-data-services.md)  
  
-   [명시적 계층 및 #40입니다. Master Data Services & #41;](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [재귀 계층 구조 및 #40입니다. Master Data Services & #41;](../master-data-services/recursive-hierarchies-master-data-services.md)  
  
-   [명시적 캡 & #40; 포함 된 파생된 계층 Master Data Services & #41;](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)  
  
-   [파생된 계층 및 #40;에서 다 대 다 관계를 표시 합니다. Master Data Services & #41;](../master-data-services/show-many-to-many-relationships-in-derived-hierarchies-master-data-services.md)  
  
-   [컬렉션 및 #40입니다. Master Data Services & #41;](../master-data-services/collections-master-data-services.md)  
  
  