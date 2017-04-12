---
title: "다차원 모델의 큐브 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OLAP 개체 [Analysis Services], 큐브"
  - "큐브 [Analysis Services], 큐브 정보"
  - "큐브 [Analysis Services]"
  - "OLAP [Analysis Services], 큐브"
ms.assetid: e0f7acf3-4b07-41fc-a5fc-ac30b4a56c54
caps.latest.revision: 33
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 33
---
# 다차원 모델의 큐브
  큐브는 분석 목적의 정보를 포함하는 다차원 구조이며, 큐브의 주요 구성 요소는 차원과 측정값입니다. 차원은 조각화 및 분석에 사용할 큐브의 구조를 정의하고, 측정값은 최종 사용자에게 의미가 있는 집계된 숫자 값을 제공합니다. 논리적 구조인 큐브를 사용하면 클라이언트 응용 프로그램에서는 마치 값이 큐브의 셀에 포함되어 있고 가능한 모든 요약된 값에 대해 셀이 정의되어 있는 것처럼 측정값의 값을 검색할 수 있습니다. 큐브의 셀은 차원 멤버의 교차에 의해 정의되며 해당 특정 교차 지점에 있는 측정값의 집계된 값을 포함합니다.  
  
## 큐브 사용의 이점  
 큐브를 사용하면 분석을 위한 모든 관련 데이터를 한 곳에 저장할 수 있습니다.  
  
## 큐브의 구성 요소  
 큐브는 다음 요소로 구성됩니다.  
  
|요소|Description|  
|-------------|-----------------|  
|차원|[다차원 모델의 차원](../../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)|  
|측정값 및 측정값 그룹|[다차원 모델의 측정값 및 측정값 그룹 만들기](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)|  
|파티션|[다차원 모델의 파티션](../../analysis-services/multidimensional-models/partitions-in-multidimensional-models.md)|  
|큐브 뷰|[다차원 모델의 큐브 뷰](../../analysis-services/multidimensional-models/perspectives-in-multidimensional-models.md)|  
|계층 구조|[사용자 정의 계층 만들기](../../analysis-services/multidimensional-models/create-user-defined-hierarchies.md)|  
|작업|[다차원 모델의 동작](../../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)|  
|KPI(핵심 성과 지표)|[다차원 모델의 KPI&#40;핵심 성과 지표&#41;](../../analysis-services/multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)|  
|계산|[다차원 모델의 계산](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)|  
|번역|[다차원 모델의 번역&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)|  
  
## 관련 작업  
  
|항목|Description|  
|-----------|-----------------|  
|[큐브 마법사를 사용하여 큐브 만들기](../../analysis-services/multidimensional-models/create-a-cube-using-the-cube-wizard.md)|큐브 마법사를 사용하여 큐브, 차원, 차원 특성 및 사용자 정의 계층을 정의하는 방법에 대해 설명합니다.|  
|[다차원 모델의 측정값 및 측정값 그룹 만들기](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)|측정값 그룹을 정의하는 방법에 대해 설명합니다.|  
|[다차원 모델의 계산](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)|MDX 스크립트에서 계산을 정의 및 구성하는 방법에 대해 설명합니다.|  
|[다차원 모델의 동작](../../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)|동작을 정의 및 구성하는 방법에 대해 설명합니다.|  
|[다차원 모델의 큐브 뷰](../../analysis-services/multidimensional-models/perspectives-in-multidimensional-models.md)|큐브 뷰를 정의 및 구성하는 방법에 대해 설명합니다.|  
|[저장 프로시저 정의](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)|저장 프로시저 작업 방법에 대해 설명합니다.|  
  
  