---
title: Analysis Services 스키마 행 집합 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- SSAS, data access interfaces
- Analysis Services data access interfaces, schema rowsets
- data access interfaces [Analysis Services]
- XML for Analysis, schema rowsets
- rowsets [Analysis Services], retrieving schema rowsets
- retrieving schema rowsets
- XMLA, schema rowsets
- rowsets [Analysis Services]
- schema rowsets [Analysis Services], retrieving
ms.assetid: 820d4b59-d428-4616-b792-c848e5da407e
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6be6dd4c95d2c44400a202e12179cd1eb5757b2f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="analysis-services-schema-rowsets"></a>Analysis Services 스키마 행 집합
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  스키마 행 집합은 데이터베이스 스키마, 활성 세션, 연결, 명령 및 서버에서 실행 중인 작업을 비롯한 Analysis Services 개체 및 서버 상태에 대한 정보를 포함하는 미리 정의된 테이블입니다. SQL Server Management Studio의 XML/A 스크립트 창에서 스키마 행 집합 테이블을 쿼리하거나, 스키마 행 집합에 대해 DMV 쿼리를 실행하거나, 스키마 행 집합 정보를 포함하는 사용자 지정 응용 프로그램(예: 보고서를 만드는 데 사용할 수 있는 사용 가능한 차원의 목록을 검색하는 보고 응용 프로그램)을 만들 수 있습니다.  
  
> [!NOTE]  
>  XML/A에서 스키마 행 집합을 사용 하는 경우 스크립트에서 반환 되는 정보는 *결과* 의 매개 변수는 [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) 메서드는이 섹션에서 설명 하는 행 집합 열 레이아웃에 따라 구성 됩니다. [!INCLUDE[msCoName](../../includes/msconame-md.md)] XMLA(XML for Analysis) 공급자는 XML for Analysis 사양에 필요한 행 집합을 지원합니다. 또한 XMLA 공급자는 OLE DB, OLAP용 OLE DB, 데이터 마이닝용 OLE DB 데이터 원본 공급자에 대한 표준 스키마 행 집합도 일부 지원합니다. 다음 항목에서는 지원되는 행 집합에 대해 설명합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
|항목|Description|  
|-----------|-----------------|  
|[XML for Analysis 스키마 행 집합](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)|XMLA 공급자에서 지원되는 XMLA 행 집합을 설명합니다.|  
|[OLE DB 스키마 행 집합](../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)|XMLA 공급자에서 지원되는 OLE DB 스키마 행 집합을 설명합니다.|  
|[OLAP 스키마 행 집합 용 OLE DB](../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)|XMLA 공급자에서 지원되는 OLAP용 OLE DB 스키마 행 집합을 설명합니다.|  
|[데이터 마이닝 스키마 행 집합](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)|XMLA 공급자에서 지원되는 데이터 마이닝 스키마 행 집합을 설명합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [다차원 모델 데이터 액세스 & #40; Analysis Services-다차원 데이터 & #41;](../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)   
 [사용 하 여 동적 관리 뷰 & #40; Dmv & #41; Analysis Services를 모니터링 하려면](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  