---
title: DimensionAttribute 데이터 형식 (ASSL) | Microsoft Docs
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
api_name:
- DimensionAttribute Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DimensionAttribute
helpviewer_keywords:
- DimensionAttribute data type
ms.assetid: 94349a87-b284-49d1-ac72-888f0375ceb8
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2d022a0bfb5c11efe38694b614bd65676fb3ee28
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36079372"
---
# <a name="dimensionattribute-data-type-assl"></a>DimensionAttribute 데이터 형식(ASSL)
  차원의 특성을 나타내는 기본 데이터 형식을 정의합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<DimensionAttribute>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Description>...</Description>  
   <Type>...</Type>  
   <Usage>...</Usage>  
   <Source>...</Source>  
   <EstimatedCount>...</EstimatedCount>  
   <KeyColumns>...</KeyColumns>  
   <NameColumn>...</NameColumn>  
   <ValueColumn>...</ValueColumn>  
   <Translations>...</Translations>  
   <AttributeRelationships>...</AttributeRelationships>  
   <DiscretizationMethod>...</DiscretizationMethod>  
   <DiscretizationBucketCount>...</DiscretizationBucketCount>  
   <RootMemberIf>...</RootMemberIf>  
   <OrderBy>...</OrderBy>  
   <DefaultMember>...</DefaultMember>  
   <OrderByAttributeID>...</OrderByAttributeID>  
   <SkippedLevelsColumn>...</SkippedLevelsColumn>  
   <NamingTemplate>...</NamingTemplate>  
   <MembersWithData>...</MembersWithData>  
   <MembersWithDataCaption>...</MembersWithDataCaption>  
   <NamingTemplateTranslations>...</NamingTemplateTranslations>  
   <CustomRollupColumn>...</CustomRollupColumn>  
   <CustomRollupPropertiesColumn>...</CustomRollupPropertiesColumn>  
   <UnaryOperatorColumn>...</UnaryOperatorColumn>  
   <AttributeHierarchyOrdered>...</AttributeHierarchyOrdered>  
   <MemberNamesUnique>...</MemberNamesUnique>  
   <IsAggregatable>...</IsAggregatable>  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
   <AttributeHierarchyOptimizedState>...</AttributeHierarchyOptimizedState>  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
   <AttributeHierarchyDisplayFolder>...</AttributeHierarchyDisplayFolder>  
   <KeyUniquenessGuarantee>...<KeyUniquenessGuarantee>  
   <InstanceSelection>...</InstanceSelection>  
   <Annotations>...</Annotations>  
</DimensionAttribute>  
```  
  
## <a name="data-type-characteristics"></a>데이터 형식 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|기본 데이터 형식|InclusionThresholdSetting|  
|파생 데이터 형식|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>데이터 형식 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|InclusionThresholdSetting|  
|자식 요소|[Annotations](../collections/annotations-element-assl.md), [AttributeHierarchyDisplayFolder](../properties/displayfolder-element-assl.md), [AttributeHierarchyEnabled](../properties/enabled-element-assl.md), [AttributeHierarchyOptimizedState](../properties/state-element-assl.md), [AttributeHierarchyOrdered](../properties/attributehierarchyordered-element-assl.md), [AttributeHierarchyVisible](../properties/visible-element-assl.md), [AttributeRelationships](../collections/relationships-element-assl.md), [CustomRollupColumn](../objects/column-element-assl.md), [CustomRollupPropertiesColumn](../objects/customrolluppropertiescolumn-element-assl.md), [DefaultMember](../objects/member-element-assl.md), [Description](../properties/description-element-assl.md), [DiscretizationBucketCount](../properties/discretizationbucketcount-element-assl.md), [DiscretizationMethod](../properties/discretizationmethod-element-assl.md), [EstimatedCount](../properties/estimatedcount-element-assl.md), [ID](../properties/id-element-assl.md), [InstanceSelection](../properties/instanceselection-element-assl.md), [IsAggregatable](../properties/isaggregatable-element-assl.md), [KeyColumns](../collections/columns-element-assl.md), [KeyUniquenessGuarantee](../properties/keyuniquenessguarantee-element-assl.md), [MemberNamesUnique](../properties/membernamesunique-element-assl.md), [MembersWithData](../objects/data-element-assl.md), [MembersWithDataCaption](../properties/caption-element-assl.md), [Name](../properties/name-element-assl.md), [NameColumn](../objects/namecolumn-element-assl.md), [NamingTemplate](../properties/namingtemplate-element-assl.md), [NamingTemplateTranslations](../collections/translations-element-assl.md), [OrderBy](../properties/orderby-element-assl.md), [OrderByAttributeID](../properties/attributeid-element-assl.md), [RootMemberIf](../properties/rootmemberif-element-assl.md), [SkippedLevelsColumn](../objects/skippedlevelscolumn-element-assl.md), [Source](../properties/source-element-binding-assl.md), [Translations](../collections/translations-element-assl.md), [Type](../properties/type-element-dimensionattribute-assl.md), [UnaryOperatorColumn](../objects/unaryoperatorcolumn-element-assl.md), [Usage](../properties/usage-element-dimensionattribute-assl.md), [ValueColumn](../objects/valuecolumn-element-assl.md)|  
|파생 요소|[특성](../objects/attribute-element-assl.md) ([특성](../collections/attributes-element-assl.md) 컬렉션 [차원](../objects/dimension-element-assl.md))|  
  
## <a name="remarks"></a>Remarks  
 DeploymentMode 구성 속성 값이 1 및 2(PowerPivot 및 테이블 형식 모델 데이터베이스를 실행하는 데 사용되는 SharePoint 및 테이블 형식 모드)로 설정된 상태에서 서비스를 실행하는 경우 다음 제한 사항이 적용됩니다.  
  
-   Usage 요소는 KEY 또는 REGULAR 값만 수락합니다.  
  
-   IsAggregatable 요소는 false일 수 없습니다.  
  
-   OrderBy 요소는 KEY 또는 PROPERTYKEY 값만 수락합니다.  
  
-   계산된 열은 테이블의 기본 키일 수 없습니다.  
  
-   계산된 열의 바인딩에는 DataSize가 포함될 수 없습니다.  
  
-   계산된 열 각각에 대해 특성 정의를 저장하기 전에 구문 유효성 검사가 수행됩니다.  
  
-   AttributeRelationships의 경우 RelationshipType의 값을 Flexible로 설정해야 합니다.  
  
-   'RowNumber'에 의해 식별되는 'RowNumber' 특성은 정수 형식이어야 합니다.  
  
-   'RowNumber' 특성만 RowNumberBinding 유형의 KeyBinding을 가질 수 있습니다.  
  
-   'RowNumber' 이외의 모든 특성은 특성 자체가 키가 아니면 키와의 관계에서 카디널리티가 1이어야 합니다.  
  
-   OrderBy에 의해 지정된 열이 PropertyKey이기도 한 경우 OrderByAttributeId가 행 번호 열을 가리킬 수 없습니다.  
  
-   키로 사용되는 특성은 다른 모든 특성과 관련되어야 합니다. 다른 유형의 관계는 지원되지 않습니다.  
  
-   NullProcessing 요소를 'UnknownMember'로 설정할 수 없습니다.  
  
-   바인딩을 'Value'로 설정할 수 없습니다.  
  
 DeploymentMode 구성 속성 값이 1 및 2(PowerPivot 및 테이블 형식 모델 데이터베이스를 실행하는 데 사용되는 SharePoint 및 테이블 형식 모드)로 설정된 상태에서 서비스를 실행하는 경우 다음 요소가 지원되지 않습니다.  
  
-   AttributeHierarchyOptimizedState  
  
-   CustomRollupColumn  
  
-   CustomRollupPropertiesColumn  
  
-   DefaultMember  
  
-   DiscretizationBucketCount  
  
-   DiscretizationMethod  
  
-   SkippedLevelsColumn  
  
-   Source  
  
-   UnaryOperatorColumn  
  
 Analysis Management Objects (AMO) 개체 모델의 해당 요소는 <xref:Microsoft.AnalysisServices.DimensionAttribute>합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Analysis Services 스크립팅 언어 XML 데이터 형식 &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  