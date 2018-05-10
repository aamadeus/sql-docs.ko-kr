---
title: 차원 관계 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 02395302dec93b270bb49291f858ab33755f6bbf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="dimension-relationships"></a>차원 관계
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  차원 용도는 큐브 차원과 큐브에 있는 측정값 그룹 간의 관계를 정의합니다. 큐브 차원은 특정 큐브에 사용되는 데이터베이스 차원의 인스턴스입니다. 큐브에는 측정값 그룹에 직접 관련되어 있지 않지만 다른 차원 또는 측정값 그룹을 통해 측정값 그룹에 간접적으로 관련될 수 있는 큐브 차원이 있을 수 있습니다. 큐브에 데이터베이스 차원이 나 측정값 그룹을 추가 하면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 검사 하 여 큐브의 데이터 원본 뷰에서 팩트 테이블과 차원 테이블 간의 관계를 검토 하 여 차원 용도 결정 하려고 합니다. 차원의 특성 간 관계입니다. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서는 감지할 수 있는 관계에 대해 차원 용도 설정을 자동으로 지정합니다.  
  
 차원과 측정값 그룹 간 관계는 관계에 참여하는 차원 및 팩트 테이블과 특정 측정값 그룹에서 차원 세분성을 지정하는 세분성 특성으로 구성됩니다.  
  
## <a name="regular-dimension-relationships"></a>일반 차원 관계  
 큐브 차원과 측정값 그룹 간 일반 차원 관계는 차원의 키 열이 팩트 테이블에 직접 조인되어 있을 때 존재하게 됩니다. 이러한 직접적인 관계는 기본 관계형 데이터베이스의 기본 키 - 외래 키 관계를 기반으로 하지만 데이터 원본 뷰에 정의된 논리적 관계를 기반으로 할 수도 있습니다. 일반 차원 관계는 전형적인 별모양 스키마 디자인에서 차원 테이블과 팩트 테이블 간 관계를 나타냅니다. 일반 관계에 대 한 자세한 내용은 참조 [일반 관계 및 일반 관계 속성 정의](../../analysis-services/multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md)합니다.  
  
## <a name="reference-dimension-relationships"></a>참조 차원 관계  
 큐브 차원과 측정값 그룹 간 참조 차원 관계는 다음 그림에 표시된 것처럼 차원의 키 열이 다른 차원 테이블의 키를 통해 팩트 테이블에 간접적으로 조인될 때 존재하게 됩니다.  
  
 ![논리 다이어그램, 참조 차원 관계](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-refdimension1.gif "논리 다이어그램, 참조 차원 관계")  
  
 참조 차원 관계는 눈송이 스키마 디자인에서 차원 테이블과 팩트 테이블 간 관계를 나타냅니다. 차원 테이블이 눈송이 스키마에 연결되어 있으면 여러 테이블의 열을 사용하여 단일 차원을 정의하거나 별도의 차원 테이블을 기반으로 별도의 차원을 정의한 후 참조 차원 관계 설정을 사용하여 차원 간에 연결을 정의할 수 있습니다. 다음 그림은 라는 하나의 팩트 테이블 **InternetSales**, 라는 두 차원 이라고 하는 테이블 및 **고객** 및 **Geography**, 눈송이 스키마입니다.  
  
 ![논리 스키마, 참조 차원 관계](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-refdim-schema1.gif "논리 스키마, 참조 차원 관계")  
  
 사용 하 여 차원을 만들 수는 **고객** 차원의 주 테이블로 테이블 및 **Geography** 은 관련 테이블로 포함 된 테이블입니다. 그런 다음 차원과 InternetSales 측정값 그룹 간에 일반 관계가 정의됩니다.  
  
 또는 InternetSales 측정값 그룹과 관련 된 두 개의 차원을 만들 수 있습니다: 차원을 기반으로 **고객** 테이블과 기반으로 차원을 **Geography** 테이블입니다. 그런 후 Customer 차원을 사용하는 참조 차원 관계를 통해 Geography 차원을 InternetSales 측정값 그룹에 연관지을 수 있습니다. 이 경우 InternetSales 측정값 그룹의 팩트를 Geography 차원에 따라 구분하면 팩트는 고객 및 지리별로 차원이 구분됩니다. 해당 큐브에 Reseller Sales라는 두 번째 측정값 그룹이 포함되면 Reseller Sales와 Geography 간에 관계가 없으므로 Reseller Sales 측정값 그룹의 팩트를 Geography 차원에 따라 구분할 수 없습니다.  
  
 다음 그림과 같이 함께 연결할 수 있는 참조 차원 수에는 제한이 없습니다.  
  
 ![논리 다이어그램, 참조 차원 관계](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-refdimension2.gif "논리 다이어그램, 참조 차원 관계")  
  
 참조 된 관계에 대 한 자세한 내용은 참조 [참조 관계 및 참조 관계 속성 정의](../../analysis-services/multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)합니다.  
  
## <a name="fact-dimension-relationships"></a>팩트 차원 관계  
 중복 제거 차원이라고 통칭되는 팩트 차원은 차원 테이블의 특성 열이 아닌 팩트 테이블의 특성 열에서 생성되는 표준 차원입니다. 중복을 줄이기 위해 유용한 차원 데이터가 팩트 테이블에 저장되는 경우가 있습니다. 예를 들어 다음 다이어그램은 **FactResellerSales** 팩트 테이블에서의 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] 예제 데이터베이스.  
  
 ![열 테이블은 차원을 지원함 실제로](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-factdim.gif "열 실제로 테이블 크기를 지원할 수 있습니다")  
  
 테이블에는 대리점에서 발주하는 주문 행뿐만 아니라 주문 자체에 대한 특성 정보도 포함됩니다. 정보를 식별 하는 위의 다이어그램에서 원이 표시 된 특성의 **FactResellerSales** 차원에서 특성으로 사용할 수 있는 테이블입니다. 이 경우 대리점에서 발주하는 구매 주문 번호와 운송업체 추적 번호의 두 가지 정보가 CustomerPONumber 및 CarrierTrackingNumber 특성 열로 표시됩니다. 이 정보는 사용자가 한 추적 번호로 발송되는 모든 주문에 대한 집계된 정보(예: 총 제품 원가)를 보려는 경우와 같은 때에 유용합니다. 그러나 차원 없이는 이러한 두 가지 특성에 대한 차원 데이터를 구성하고 집계할 수 없습니다.  
  
 이론상으로는 FactResellerSales 테이블과 동일한 키 정보를 사용하는 차원 테이블을 만들어 CarrierTrackingNumber와 CustomerPONumber라는 두 가지 다른 특성 열을 이 차원 테이블로 이동할 수 있습니다. 그러나 이렇게 하면 단 두 가지 특성을 별개의 차원으로 표시하기 위해 데이터의 중요 부분이 중복되고 데이터 웨어하우스가 불필요하게 더 복잡해집니다.  
  
> [!NOTE]  
>  팩트 차원은 종종 드릴스루 동작을 지원하는 데 사용됩니다. 동작에 대한 자세한 내용은 [동작&#40;Analysis Services - 다차원 데이터&#41;](../../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)을 참조하세요.  
  
> [!NOTE]  
>  팩트 관계에서 참조하는 측정값 그룹을 업데이트할 때마다 팩트 차원을 증분 업데이트해야 합니다. 팩트 차원이 ROLAP 차원이면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 처리 엔진에서 모든 캐시를 삭제하고 측정값 그룹을 증분 처리합니다.  
  
 팩트 관계에 대 한 자세한 내용은 참조 [팩트 관계 및 팩트 관계 속성 정의](../../analysis-services/multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)합니다.  
  
## <a name="many-to-many-dimension-relationships"></a>다 대 다 차원 관계  
 대부분의 차원에서 각 팩트는 하나의 차원 멤버에만 조인되고 단일 차원 멤버는 여러 팩트와 연결될 수 있습니다. 관계형 데이터베이스 용어에서 이 관계를 일 대 다 관계라고 합니다. 그러나 단일 팩트를 여러 차원 멤버에 조인하는 것이 유용한 경우가 종종 있습니다. 예를 들어 은행 고객이 당좌 예금 계정, 저축 예금 계정, 신용 카드 계정 및 투자 계정 등의 여러 계정을 가질 수 있으며 한 계정에 공동 예금주나 여러 예금주가 있을 수도 있습니다. 따라서 이러한 관계로 구성된 Customer 차원에는 단일 계정 트랜잭션과 관련된 여러 멤버가 포함됩니다.  
  
 ![논리 스키마/다 대 다 차원 관계](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-many-dimension1.gif "논리 스키마/다 대 다 차원 관계")  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 차원 및 팩트 테이블 간에 다 대 다 관계를 정의할 수 있습니다.  
  
> [!NOTE]  
>  다 대 다 차원 관계를 지원하려면 위의 다이어그램과 같이 데이터 원본 뷰에서 관련된 모든 테이블 간에 외래 키 관계를 설정해야 합니다. 그렇지 않으면 수 없게 됩니다에 관계를 설정할 때 올바른 중간 측정값 그룹을 선택 하 고 **차원 용도** 차원 디자이너의 탭 합니다.  
  
 다 대 다 관계에 대 한 자세한 내용은 참조 [정의 다 대 다 관계 및 다 대 다 관계 속성](../../analysis-services/multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md)합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [차원 & #40; Analysis Services-다차원 데이터 & #41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  