---
title: EntityContainer 요소 (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
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
ms.assetid: e328558e-16b0-4d4a-a79a-fdd3c9493595
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 89d12841c0ef56f7818b9b53b292fb672ba6d51b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="entitycontainer-element-csdlbi"></a>EntityContainer 요소(CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  EntityContainer 요소는 단일 데이터 모델 내의 엔터티 컬렉션을 정의하는 EntityContainer라는 CSDL 유형을 기반으로 하는 복합 유형입니다. 비즈니스 인텔리전스 응용 프로그램에서 EntityContainer가 나타내는 데이터 모델은 관계로 연결된 열은 물론 계산, 측정값, KPI로 연결된 열이 있는 여러 테이블을 포함할 수 있습니다. 이 요소는 개념상 데이터베이스 또는 데이터 원본과 비슷합니다.  
  
 EntityContainer는 테이블 및 관계를 포함하여 데이터 모델에 포함된 각 엔터티 유형을 지정해야 합니다. 이러한 모델 엔터티에 대한 정보는 해당 형식, 즉 Entity 요소의 자식 엔터티를 나열하여 지정됩니다. 자세한 내용은 [EntityType 요소&#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entitytype-element-csdlbi.md)를 참조하세요.  
  
 데이터 정렬 및 언어와 같은 속성은 개별 개체가 아니라 EntityContainer의 수준에서 정의됩니다. 그러나 모델 내의 열 및 텍스트 특성에는 다른 언어의 캡션이나 번역이 있을 수 있습니다.  
  
## <a name="elements-and-attributes"></a>요소 및 특성  
 다음 표에서는 EntityContainer를 정의하는 요소와 특성을 설명합니다.  
  
|이름|필수 여부|설명|  
|----------|-----------------|-----------------|  
|이름|예|데이터 모델의 이름입니다.|  
|캡션|아니오|데이터베이스 또는 데이터 모델에 대한 설명입니다.|  
|Culture|예|요청의 LCID를 포함하는 문자열입니다.|  
|CompareOptions|예|모델에 대한 언어별 정렬 및 문자열 비교 옵션입니다.|  
|DirectQueryMode|아니오|모델이 DirectQuery 모드를 사용할 때 쿼리를 나타내는 열거형입니다.|  
|EntitySet 요소|예|[EntitySet 요소 & #40; CSDLBI & #41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entityset-element-csdlbi.md)|  
|AssociationSet 요소|아니요|[AssociationSet 요소 & #40; CSDLBI & #41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/associationset-element-csdlbi.md)|  
  
## <a name="compareoptions-element"></a>CompareOptions 요소  
 CompareOptions 특성은 데이터 모델에 적용되는 데이터 정렬 속성을 정의합니다. CompareOptions로 정의되는 속성은 모델 디자인 타임에 Analysis Services 데이터베이스에 설정된 정렬 순서, 가나 구분 및 대/소문자 구분에 대한 설정에서 파생됩니다. 다음 표에서는 CompareOptions 특성의 일부로 포함되는 값을 설명합니다.  
  
|Value|Description|  
|-----------|-----------------|  
|IgnoreCase|문자열 비교에서 대소문자를 무시해야 하는지 여부를 나타내는 부울 값입니다.|  
|IgnoreNonSpace|문자열 비교에서 분음 부호와 같은 공백 없는 결합 문자를 무시해야 하는지 여부를 나타내는 부울 값입니다.|  
|IgnoreKanaType|문자열 비교에서 가나(kana) 형식을 무시해야 하는지 여부를 나타내는 부울 값입니다.|  
|IgnoreWidth|문자열 비교에서 문자 너비를 무시해야 하는지 여부를 나타내는 부울 값입니다.|  
  
## <a name="directquerymode"></a>DirectQueryMode  
 **DirectQueryMode**  
  
 DirectQueryMode라는 단순 유형은 모델에서 관계형 데이터 원본에서 데이터를 직접 검색하는 기능을 사용할 때 기본적으로 사용되는 쿼리 유형을 정의합니다. 이 속성은 DirectQuery 모드로 실행되는 테이블 형식 모델에만 적용할 수 있습니다. 다음 표에서는 DirectQuery 모드 열거형에 사용할 수 있는 값을 나열합니다.  
  
|Value|Description|  
|-----------|-----------------|  
|InMemory|모델에 대한 쿼리가 캐시에 있는 데이터를 사용함을 나타냅니다.|  
|InMemoryWithDirectQuery|기본적으로 모델에 대한 쿼리가 관계형 데이터 원본의 데이터를 사용함을 나타냅니다.|  
|DirectQueryWithInMemory|기본적으로 모델에 대한 쿼리가 캐시에 있는 데이터를 사용함을 나타냅니다.|  
|DirectQuery|모델에 대한 쿼리가 관계형 데이터 원본에 있는 데이터만 사용함을 나타냅니다.|  
  
## <a name="example"></a>예제  
 **테이블 형식**  
  
 CSDLBI 버전 1.1의 다음 예제는 AdventureWorks 테이블 형식 데이터 모델의 일부를 나타냅니다.  
  
```  
  
<EntityContainer   
     Name="Sandbox">  
   <EntitySet   
       Name="DimEmployee"   
       EntityType="Sandbox.DimEmployee">  
   <bi:EntitySet />  
   </EntitySet>  
  
   <EntitySet   
     Name="DimProduct"   
       EntityType="Sandbox.DimProduct">  
    <bi:EntitySet />  
    </EntitySet>  
  
<bi:EntityContainer Caption="AWSimple" Culture="en-US">  
  
```  
  
## <a name="example"></a>예제  
 **다차원**  
  
 CSDLBI 버전 1.1의 다음 예제는 Contoso Operations 큐브의 발췌 구문입니다.  
  
```  
  
<EntityContainer   
     Name="Sandbox">  
   <EntitySet   
      Name="Bike"   
      EntityType="Sandbox.Bike">  
    <bi:EntitySet Hidden="true" />  
   </EntitySet>  
…  
<bi:EntityContainer   
   Caption="CSDLTest"   
   Culture="en-US">  
<bi:CompareOptions   
   IgnoreCase="true" />  
</bi:EntityContainer>  
</EntityContainer>  
  
```  
  
## <a name="see-also"></a>관련 항목:  
 [EntitySet 요소 & #40; CSDLBI & #41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entityset-element-csdlbi.md)  
  
  