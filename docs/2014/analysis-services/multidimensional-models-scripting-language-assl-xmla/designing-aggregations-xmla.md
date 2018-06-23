---
title: 집계 디자인 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- statistical information [XML for Analysis]
- batches [XML for Analysis]
- aggregations [Analysis Services], XML for Analysis
- XMLA, aggregations
- queries [XMLA]
- XML for Analysis, aggregations
- iterative aggregation process [XMLA]
ms.assetid: 4dd27afa-10c7-408d-bc24-ca74217ddbcb
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e2e2d5be45ba679cfa0c0ea39928e5b43d30c3a1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36081003"
---
# <a name="designing-aggregations-xmla"></a>집계 디자인(XMLA)
  집계 디자인은 특정 측정값 그룹의 파티션과 연결되어 해당 파티션에서 집계를 저장할 때 동일한 구조를 사용하도록 합니다. 동일한 저장 구조를 사용 하 여 파티션에 대 한을 사용 하면 사용 하 여 나중에 병합할 수 있는 파티션을 쉽게 정의할 수는 [MergePartitions](../xmla/xml-elements-commands/mergepartitions-element-xmla.md) 명령입니다. 집계 디자인에 대 한 자세한 내용은 참조 [집계 및 집계 디자인](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)합니다.  
  
 집계 디자인에 대 한 집계를 정의 하려면 사용할 수 있습니다는 [DesignAggregations](../xmla/xml-elements-commands/designaggregations-element-xmla.md) xml for Analysis (XMLA) 명령입니다. `DesignAggregations` 명령에는 참조로 사용할 집계 디자인과 해당 참조에 따라 디자인 프로세스를 제어할 방법을 식별하는 속성이 있습니다. `DesignAggregations` 명령과 해당 속성을 사용하면 반복적으로 또는 일괄 처리로 집계를 디자인한 다음 결과 디자인 통계를 보고 디자인 프로세스를 평가할 수 있습니다.  
  
## <a name="specifying-an-aggregation-design"></a>집계 디자인 지정  
 [개체](../xmla/xml-elements-properties/object-element-xmla.md) 의 속성은 `DesignAggregations` 명령에는 기존 집계 디자인에 대 한 개체 참조를 포함 해야 합니다. 개체 참조는 데이터베이스 식별자, 큐브 식별자, 측정값 그룹 식별자 및 집계 디자인 식별자를 포함합니다. 집계 디자인이 아직 없으면 오류가 발생합니다.  
  
## <a name="controlling-the-design-process"></a>디자인 프로세스 제어  
 `DesignAggregations` 명령의 다음 속성을 사용하여 집계 디자인의 집계를 정의하는 데 사용되는 알고리즘을 제어할 수 있습니다.  
  
-   [단계](../xmla/xml-elements-properties/steps-element-xmla.md) 반복 횟수를 결정 하는 속성은 `DesignAggregations` 명령은 클라이언트 응용 프로그램에 제어를 반환 하기 전에 수행 해야 합니다.  
  
-   [시간](../xmla/xml-elements-properties/time-element-xmla.md) 속성을 밀리초 단위로 결정는 `DesignAggregations` 명령은 클라이언트 응용 프로그램에 제어를 반환 하기 전에 수행 해야 합니다.  
  
-   [최적화](../xmla/xml-elements-properties/optimization-element-xmla.md) 성능 향상의 예상된 백분율을 결정 하는 속성은 `DesignAggregations` 명령이 달성 하려는 합니다. 집계를 반복적으로 디자인할 경우 첫 번째 명령에서만 이 속성을 보내면 됩니다.  
  
-   [저장소](../xmla/xml-elements-properties/storage-element-xmla.md) 속성 결정에 사용 된 바이트의 디스크 저장소의 예상된 크기는 `DesignAggregations` 명령입니다. 집계를 반복적으로 디자인할 경우 첫 번째 명령에서만 이 속성을 보내면 됩니다.  
  
-   [구체화](../xmla/xml-elements-properties/materialize-element-xmla.md) 속성 결정 여부는 `DesignAggregations` 명령이 디자인 프로세스 중에 정의 된 집계를 만들어야 합니다. 집계를 반복적으로 디자인할 경우 디자인된 집계를 저장할 준비가 될 때까지 이 속성을 false로 설정해야 합니다. 이 속성을 true로 설정하면 현재 디자인 프로세스가 종료되고 정의된 집계가 지정된 집계 디자인에 추가됩니다.  
  
## <a name="specifying-queries"></a>쿼리 지정  
 DesignAggregations 명령은 하나 이상 포함 하 여 사용 빈도 기반 최적화 명령을 지원 `Query` 의 요소는 [쿼리](../xmla/xml-elements-properties/queries-element-xmla.md) 속성입니다. `Queries` 속성 하나 이상 포함할 수 있습니다 [쿼리](../xmla/xml-elements-properties/query-element-xmla.md) 요소입니다. `Queries` 속성에 `Query` 요소가 없는 경우 `Object` 요소에 지정된 집계 디자인은 일반적인 집계 집합을 포함하는 기본 구조를 사용합니다. 이 일반적인 집계 집합은 `Optimization` 명령의 `Storage` 및 `DesignAggregations` 속성에 지정된 조건을 충족하도록 디자인되었습니다.  
  
 각 `Query` 요소는 가장 자주 사용 되는 쿼리를 대상으로 집계 정의 하기 위해 디자인 프로세스에서 사용 하는 목표 쿼리를 나타냅니다. 인스턴스에서 저장 된 정보를 사용할 수 있습니다 또는 사용자 고유의 목표 쿼리를 지정 하거나 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 가장 자주에 대 한 정보를 검색 하는 쿼리 로그에 쿼리를 사용 합니다. 사용 빈도 기반 최적화 마법사는 `DesignAggregations` 명령을 보낼 때 쿼리 로그를 사용하여 시간, 사용 빈도 또는 지정된 사용자를 기준으로 목표 쿼리를 검색합니다. 자세한 내용은 참조 [사용 빈도 기반 최적화 마법사 F1 도움말](../usage-based-optimization-wizard-f1-help.md)합니다.  
  
 만 첫 번째 범위에서 목표 쿼리를 전달 해야 집계를 반복적으로 디자인 하는 경우 `DesignAggregations` 있기 때문에 명령을 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스가 이러한 목표 쿼리를 저장 하 고 이러한 쿼리를 사용 하 여 후속 하는 동안 `DesignAggregations` 명령입니다. 반복 프로세스의 첫 번째 `DesignAggregations` 명령에서 목표 쿼리를 전달하면 `DesignAggregations` 속성에 목표 쿼리를 포함하는 모든 후속 `Queries` 명령은 오류를 생성합니다.  
  
 `Query` 요소에는 다음 인수를 포함하는 쉼표로 구분된 값이 포함됩니다.  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *빈도*  
 쿼리가 이전에 실행된 횟수에 해당하는 가중 요인입니다. 경우는 `Query` 요소가 새 쿼리를 나타내는 *주파수* 값은 쿼리를 평가 하는 디자인 프로세스에서 사용 하는 중 요인을 나타냅니다. 빈도 값이 증가하면서 디자인 프로세스 중 쿼리에 적용되는 가중치도 증가합니다.  
  
 *데이터 집합*  
 쿼리에 포함될 차원 특성을 지정하는 숫자 문자열입니다. 이 문자열에는 차원의 특성 수와 같은 문자 수가 있어야 합니다. 영(0)은 지정된 서수 위치의 특성이 지정된 차원의 쿼리에 포함되지 않음을 나타내고 일(1)은 지정된 서수 위치의 특성이 지정된 차원의 쿼리에 포함됨을 나타냅니다.  
  
 예를 들어 문자열 "011"은 세 개의 특성이 있는 차원을 사용하는 쿼리를 참조하며 여기서 두 번째 및 세 번째 특성이 쿼리에 포함됩니다.  
  
> [!NOTE]  
>  일부 특성은 데이터 집합에서 고려되지 않습니다. 제외 된 특성에 대 한 자세한 내용은 참조 [쿼리 요소 &#40;XMLA&#41;](../xmla/xml-elements-properties/query-element-xmla.md)합니다.  
  
 집계 디자인을 포함 하는 측정값 그룹의 각 차원으로 표시 됩니다는 *Dataset* 값에 `Query` 요소입니다. *Dataset* 값의 순서는 측정값 그룹에 포함된 차원의 순서와 일치해야 합니다.  
  
## <a name="designing-aggregations-using-iterative-or-batch-processes"></a>반복 또는 일괄 처리를 사용하여 집계 디자인  
 디자인 프로세스에 필요한 상호 작용에 따라 반복 처리나 일괄 처리의 일부로 `DesignAggregations` 명령을 사용할 수 있습니다.  
  
### <a name="designing-aggregations-using-an-iterative-process"></a>반복 처리를 사용하여 집계 디자인  
 집계를 반복적으로 디자인하려면 여러 개의 `DesignAggregations` 명령을 보내 디자인 프로세스를 세부적으로 제어할 수 있도록 합니다. 집계 디자인 마법사에서는 이와 동일한 방법을 사용하여 디자인 프로세스를 세부적으로 제어할 수 있습니다. 자세한 내용은 참조 [집계 디자인 마법사 F1 도움말](../aggregation-design-wizard-f1-help.md)합니다.  
  
> [!NOTE]  
>  집계를 반복적으로 디자인하려면 명시적 세션이 필요합니다. 명시적 세션에 대 한 자세한 내용은 참조 [관리 연결 및 세션 &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md)합니다.  
  
 반복 처리를 시작하려면 먼저 다음 정보가 포함된 `DesignAggregations` 명령을 보냅니다.  
  
-   디자인 프로세스 전체를 대상으로 하는 `Storage` 및 `Optimization` 속성 값  
  
-   디자인 프로세스의 첫 번째 단계를 제한하는 `Steps` 및 `Time` 속성 값  
  
-   디자인 프로세스 전체를 대상으로 하는 목표 쿼리가 들어 있는 `Queries` 속성 값(사용 빈도 기반 최적화를 수행하려는 경우)  
  
-   false로 설정된 `Materialize` 속성. 이 속성을 false로 설정하면 디자인 프로세스에서는 명령이 완료되었을 때 정의된 집계를 집계 디자인에 저장하지 않습니다.  
  
 첫 번째 `DesignAggregations` 명령이 완료되면 디자인 통계가 들어 있는 행 집합이 반환됩니다. 이러한 디자인 통계를 평가하여 디자인 프로세스를 계속할지 여부나 디자인 프로세스가 완료되었는지 여부를 결정할 수 있습니다. 프로세스를 계속해야 하는 경우에는 디자인 프로세스의 이 단계를 제한하는 `DesignAggregations` 및 `Steps` 값이 들어 있는 다른 `Time` 명령을 보냅니다. 결과 통계를 평가한 다음 디자인 프로세스를 계속할지 여부를 결정합니다. `DesignAggregations` 명령을 보내고 결과를 평가하는 이 반복적 처리는 목표에 도달하고 적절한 집계 집합이 정의될 때까지 계속됩니다.  
  
 원하는 집계 집합에 도달한 후에는 최종 `DesignAggregations` 명령을 하나 보냅니다. 이 최종 `DesignAggregations` 명령의 `Steps` 속성은 1로 설정하고, `Materialize` 속성은 true로 설정해야 합니다. 이러한 설정을 사용하면 이 최종 `DesignAggregations` 명령이 디자인 프로세스를 완료하고 정의된 집계를 집계 디자인에 저장합니다.  
  
### <a name="designing-aggregations-using-a-batch-process"></a>일괄 처리를 사용하여 집계 디자인  
 디자인 프로세스 전체를 대상으로 하며 이를 제한하는 `DesignAggregations`, `Steps`, `Time` 및 `Storage` 속성이 포함된 단일 `Optimization` 명령을 보내 일괄 처리로 집계를 디자인할 수도 있습니다. 또한 사용 빈도 기반 최적화를 수행하려면 디자인 프로세스를 대상으로 하는 목표 쿼리를 `Queries` 속성에 포함해야 합니다. `Materialize` 속성은 true로 설정하여 명령이 완료되었을 때 디자인 프로세스에서 정의된 집계를 집계 디자인에 저장하도록 해야 합니다.  
  
 암시적 세션이나 명시적 세션에서 일괄 처리를 사용하여 집계를 디자인할 수 있습니다. 암시적 세션과 명시적 세션에 대 한 자세한 내용은 참조 [관리 연결 및 세션 &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md)합니다.  
  
## <a name="returning-design-statistics"></a>디자인 통계 반환  
 `DesignAggregations` 명령은 클라이언트 응용 프로그램에 제어를 반환할 때 해당 명령에 대한 디자인 통계를 나타내는 단일 행이 들어 있는 행 집합을 반환합니다. 행 집합에는 다음 표에 나열된 열이 들어 있습니다.  
  
|Column|데이터 형식|Description|  
|------------|---------------|-----------------|  
|단계|정수|클라이언트 응용 프로그램에 제어를 반환하기 전에 해당 명령에서 수행하는 단계 수입니다.|  
|Time|정수(Long)|클라이언트 응용 프로그램에 제어를 반환하기 전에 해당 명령에서 소요되는 시간(밀리초)입니다.|  
|Optimization|Double|클라이언트 응용 프로그램에 제어를 반환하기 전에 해당 명령에 의해 달성되는 예상 성능 향상률입니다.|  
|저장소|정수(Long)|클라이언트 응용 프로그램에 제어를 반환하기 전에 해당 명령에서 사용하는 예상 바이트 수입니다.|  
|Aggregations|정수(Long)|클라이언트 응용 프로그램에 제어를 반환하기 전에 해당 명령에 의해 정의되는 집계 수입니다.|  
|LastStep|Boolean|행 집합의 데이터가 디자인 프로세스의 마지막 단계를 나타내는지 여부를 나타냅니다. 명령의 `Materialize` 속성이 true로 설정되어 있으면 이 열 값은 true로 설정됩니다.|  
  
 각 `DesignAggregations` 명령 후에 반환된 행 집합에 들어 있는 디자인 통계를 반복 처리와 일괄 처리 모두에서 사용할 수 있습니다. 반복 디자인에서는 디자인 통계를 사용하여 진행률을 확인하고 표시할 수 있습니다. 일괄 처리로 집계를 디자인할 때는 디자인 통계를 사용하여 해당 명령으로 만들어진 집계 수를 확인할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Analysis Services에서 XMLA를 사용하여 개발](developing-with-xmla-in-analysis-services.md)  
  
  