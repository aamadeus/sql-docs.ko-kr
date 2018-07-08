---
title: 요소 (CSDLBI) 측정 | Microsoft Docs
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
ms.assetid: bfbc9274-053a-421a-bb81-2095bba710be
caps.latest.revision: 10
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 36dda5645c53a88fa497682e6946331c85ca67db
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36080950"
---
# <a name="measure-element-csdlbi"></a>Measure 요소(CSDLBI)
  Measure 요소는 CSDL Property 요소를 기반으로 하는 복합 유형입니다. CSDLBI 주석은 비즈니스 인텔리전스 데이터 모델에서 사용할 복합 수식의 정의를 지원하는 특성을 추가합니다.  
  
## <a name="elements-and-attributes"></a>요소 및 특성  
 다음 표에서는 Measure 요소를 정의하는 특성과 해당 요소 및 Property 요소에 적용 가능한 모든 특성을 설명합니다.  
  
|속성|필수 여부|Description|  
|----------|-----------------|-----------------|  
|Kpi|아니요|KPI로 사용되는 측정값 전용의 필수 요소입니다. 모든 측정값이 KPI인 것은 아니지만 모든 KPI는 측정값 정의를 기반으로 해야 합니다.<br /><br /> [KPI 요소 &#40;CSDLBI&#41;](kpi-element-csdlbi.md)|  
|IsSimpleMeasure|아니요|측정값에 사용된 수식이 단순 집계(SUM, COUNT, MIN, MAX, AVG, DistinctCount) 중 하나인지 여부를 나타내는 True/False 값입니다.<br /><br /> 기본값은 true입니다.|  
  
## <a name="example"></a>예제  
 **테이블 형식**  
  
 다음 예제는 CSDLBI 버전 1.1에서 AdventureWorks 테이블 형식 모델 예제의 측정값 두 개를 보여 줍니다. 두 번째 측정값은 KPI 요소가 추가되어 KPI로 변환되었습니다.  
  
```  
  
<Property   
    Name="Order_Lines_Count"   
    Type="Int64">  
<bi:Measure   
    Caption="Order Lines Count"   
    ReferenceName="Order Lines Count"   
    Width="0"   
    IsSimpleMeasure="false" />  
</Property>  
  
<Property   
    Name="Total_Current_Quarter_Sales_Performance"   
    Type="Double">  
<bi:Measure   
    Caption="Total Current Quarter Sales Performance"   
    ReferenceName="Total Current Quarter Sales Performance"   
    Width="0"   
    IsSimpleMeasure="false">  
    <bi:Kpi   
    StatusGraphic="Three Signs Colored">  
      <bi:KpiGoal>  
        <bi:PropertyRef Name="Measures___Total_Current_Quarter_Sales_Performance_Goal_" />  
      </bi:KpiGoal>  
      <bi:KpiStatus>  
        <bi:PropertyRef Name="Measures___Total_Current_Quarter_Sales_Performance_Status_" />  
      </bi:KpiStatus>  
    </bi:Kpi>  
  </bi:Measure>  
</Property>  
```  
  
## <a name="example"></a>예제  
 **Multidimensiona;**  
  
 다음 예제는 CSDLBI 버전 1.1에서 KPI로 사용되는 Contoso Operations 큐브의 측정값을 보여 줍니다.  
  
```  
  
<Property   
    Name="Sum_of_SalesAmount"   
    Type="Decimal" Precision="19" Scale="4">  
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
  
  