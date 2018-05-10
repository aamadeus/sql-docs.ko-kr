---
title: XML 데이터 형식 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- XML data types [XMLA]
- data types [XML for Analysis]
- XMLA, data types
- XML for Analysis, data types
ms.assetid: 979b5384-90d9-4e09-9286-1d1eafdc4864
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f510e78d39ee1a61c17a9f79524a64befc0e127d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="xml-data-types-xmla"></a>XML 데이터 형식(XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  XML 1.0 권장 사항에 정의된 표준 기본 형식 및 파생 형식 외에 XMLA(XML for Analysis) 1.1 사양은 추가 데이터 형식을 정의하여 다차원 및 테이블 형식 데이터의 표현을 지원합니다.  
  
 XMLA는 다음 표에 나열된 데이터 형식을 사용합니다.  
  
|데이터 형식|Description|  
|----------------|-----------------|  
|Boolean|표준 XML **boolean** 데이터 형식입니다.|  
|Decimal|표준 XML **decimal** 데이터 형식입니다.|  
|[EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|**root** 요소의 네임스페이스입니다. XMLA 명령이 결과 반환 하지 않으면 XMLA 명령이 결과 정상적으로 반환 하지 않으므로 또는에서 오류가 발생 하기 때문에이 네임 스페이스가 반환 됩니다는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] XMLA 명령을 실행 하는 동안 인스턴스.|  
|[EnumString](../../../analysis-services/xmla/xml-data-types/enumstring-data-type-xmla.md)|지정된 열거자에 대한 명명된 문자열 상수 집합입니다.|  
|정수|표준 XML **int** 데이터 형식입니다.|  
|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)|반환 된 다차원 데이터는 *결과* 의 매개 변수는 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) 메서드.|  
|[결과 집합](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|**Execute** 메서드에 의해 반환되는 자기 설명적 XML 결과 집합입니다.|  
|[행 집합](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)|포함된 된 XML 스키마에 의해 구조화 하는 데이터 원본의 행을 반환한는 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) 메서드.|  
|문자열|XML **string** 데이터 형식입니다.|  
|UnsignedInt|XML **unsignedInt** 스키마 유형입니다.|  
  
 표준 XML 데이터 형식에 대한 자세한 내용은 WC3(World Wide Web Consortium) 후보 권장 사항을 참조하십시오.  
  
## <a name="see-also"></a>관련 항목:  
 [XML 요소 & #40; XMLA & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [XML for Analysis & #40; XMLA & #41; 참조](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  