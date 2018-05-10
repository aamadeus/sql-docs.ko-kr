---
title: DefaultDetails 요소 (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 05a08baa-23cc-4011-9c2e-f60a20bb87da
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b4b4611ddb68689ff81b9fe5b68b2f88aa850e46
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="defaultdetails-element-csdlbi"></a>DefaultDetails 요소(CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  DefaultDetails 요소는 테이블에서 열의 '기본 필드 집합'을 함께 정의하는 속성 참조 목록을 나타냅니다. 각 속성은 측정값 또는 열만 참조할 수 있습니다.  
  
## <a name="elements-and-attributes"></a>요소 및 특성  
 다음 표에서는 DefaultDetails 요소를 정의하는 요소와 특성을 보여 줍니다.  
  
|이름|필수 여부|설명|  
|----------|-----------------|-----------------|  
|DefaultDetailsPosition|아니요|컬렉션에서의 존재 여부와 위치를 나타내는 양의 정수입니다.|  
  
## <a name="example"></a>예제  
 **테이블 형식**  
  
 다음 예에서는 CSDLBI 버전 1.1의 AdventureWorks 예제 데이터 모델에서 발췌한 구문을 보여 줍니다. Employees 테이블에 대한 기본 열 집합이 한 개뿐입니다(제목). 그러나 테이블의 기본 필드 집합으로 열 세 개가 정의되었습니다.  
  
```  
  
<EntityType   
    Name="DimEmployee">  
....  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Title" />  
   </bi:DefaultDetails>  
.....  
<EntityType   
    Name="Products">  
.....  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Color" />  
      <bi:MemberRef Name="DealerPrice" />  
      <bi:MemberRef Name="Status" />  
   </bi:DefaultDetails>  
  
```  
  
## <a name="example"></a>예제  
 **다차원**  
  
 다음 예에서는 CSDLBI 버전 1.1의 Contoso Operations 큐브에 있는 Bike 테이블 정의에서 발췌한 구문을 보여 줍니다. 이 주석은 다른 표시 열을 지정하지 않은 경우 기본적으로 Color 열을 표시해야 함을 나타냅니다.  
  
```  
  
<EntityType Name="Bike">  
   <Key>  
   <PropertyRef Name="RowNumber" />  
   </Key>  
....  
<bi:EntityType>  
   <bi:DisplayKey>  
      <bi:MemberRef Name="Color" />  
   </bi:DisplayKey>  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Color" />  
   </bi:DefaultDetails>  
   <bi:SortMembers>  
      <bi:MemberRef Name="Color" />  
   </bi:SortMembers>  
....  
</bi:EntityType>  
</EntityType>  
```  
  
## <a name="see-also"></a>관련 항목:  
 [1050-1103을 수준 테이블 형식 개체 모델 호환성을 이해 합니다.](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [CSDLBI 개념](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md)  
  
  