---
title: KPI 요소 (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 203ee6e8-eef2-4476-b09f-bd95e492ddaa
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 2f6c4ee26beb74acd6817615d34847883c3b3565
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36185484"
---
# <a name="kpi-element-csdlbi"></a>KPI 요소(CSDLBI)
  KPI 요소는 KPI(핵심 성과 지표)로 사용할 수 있는 계산을 정의합니다. 비즈니스 인텔리전스 데이터 모델에서 KPI는 측정값을 기반으로 하며, KPI 정의처럼 측정값과 관련된 모든 메타데이터뿐 아니라 KPI 값을 표시하는 데 필요한 기본 그래픽 등의 정보를 포함합니다.  
  
 Kpi 요소는 측정값 정의에 포함되는 수식을 지정하는 것이 아니라 KPI로 사용되는 측정값과 관련된 추가 메타데이터를 지정합니다. 측정값을 KPI로 지정한 후에는 이를 다른 컨텍스트에서 측정값으로 사용할 수 없습니다.  
  
## <a name="elements-and-attributes"></a>요소 및 특성  
 다음 표는 KPI 요소를 정의하는 특성과 해당 요소를 보여 줍니다.  
  
|속성|필수 여부|Description|  
|----------|-----------------|-----------------|  
|설명서|아니요|KPI에 대한 설명입니다.|  
|KpiGoal|예|목표로 사용할 수 있는 값이 포함된 열에 대한 참조입니다.<br /><br /> [PropertyRef 요소&#40;CSDLBI&#41;](propertyref-element-csdlbi.md)a를 참조하세요.|  
|KpiStatus|예|KPI의 현재 상태를 나타내는 값이 포함된 열에 대한 참조입니다.|  
|StatusGraphic|예|KPI에 정의된 대상에 대한 음수, 보통 또는 양수 진행률을 나타내는 이미지에 대한 참조입니다.|  
  
## <a name="remarks"></a>Remarks  
 모델을 디자인할 때 측정값을 만든 다음 이 측정값을 KPI로 사용하도록 할당하여 KPI를 만들 수 있습니다. 그런 다음 추세를 나타내는 데 사용할 그래픽과 같은 KPI 관련 정보를 추가합니다.  
  
## <a name="example"></a>예제  
 **테이블 형식**  
  
 다음 예제는 CSDLBI 버전 1.0에서 AdventureWorks 테이블 형식 모델 예제의 판매를 측정하는 KPI를 보여 줍니다.  
  
```  
  
<Property Name="InternetCurrSalesPerf" Type="Double">  
  <bi:Measure>  
    <bi:Kpi StatusGraphic="Three Stars Colored">  
      <bi:KpiGoal>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Goal" />  
      </bi:KpiGoal>  
      <bi:KpiStatus>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Status" />  
      </bi:KpiStatus>  
    </bi:Kpi>  
  </bi:Measure>  
</Property>  
  
```  
  
## <a name="example"></a>예제  
 **다차원**  
  
 다음 예제는 CSDLBI 버전 1.1에서 Contoso Operations 큐브의 KPI를 보여 줍니다.  
  
```  
<Property Name="Sum_of_SalesAmount" Type="Decimal" Precision="19" Scale="4">  
   <Documentation>  
     <Summary>KPI Description</Summary>  
   </Documentation>  
     <bi:Measure   
         Caption="Sum of SalesAmount"   
         ReferenceName="Sum of SalesAmount"   
         FormatString="\$#,0.00;(\$#,0.00);\$#,0.00">  
     <bi:Kpi   
           StatusGraphic="Three Circles Colored">  
         <bi:KpiGoal>  
            <bi:PropertyRef Name="v_Sum_of_SalesAmount_Goal" />  
          </bi:KpiGoal>  
          <bi:KpiStatus>  
              <bi:PropertyRef Name="v_Sum_of_SalesAmount_Status" />  
          </bi:KpiStatus>  
     </bi:Kpi>  
     </bi:Measure>  
</Property>  
```  
  
## <a name="see-also"></a>관련 항목  
 [CSDL용 BI 주석에 대한 기술 참조](technical-reference-for-bi-annotations-to-csdl.md)  
  
  