---
title: ADO.NET 사용자 지정 속성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: e062a9ab-1e6b-4061-845a-4f8a0552b09d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c04ffa97900e7fd392b5c8b53a2ba7cdb0c5d8dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221533"
---
# <a name="ado-net-custom-properties"></a>ADO.NET 사용자 지정 속성
  **원본 사용자 지정 속성**  
  
 ADO.NET 원본에는 사용자 지정 속성과 모든 데이터 흐름 구성 요소에 공통된 속성이 모두 있습니다.  
  
 다음 표에서는 ADO.NET 원본의 사용자 지정 속성에 대해 설명합니다. 모든 속성은 읽기/쓰기가 가능합니다.  
  
|속성 이름|데이터 형식|Description|  
|-------------------|---------------|-----------------|  
|CommandTimeout|String|SQL 명령이 종료되기 전의 제한 시간(초)을 지정하는 값입니다. 값 0은 명령의 제한 시간이 없음을 나타냅니다.|  
|SqlCommand|String|ADO.NET 원본이 데이터 추출에 사용하는 SQL 문입니다.<br /><br /> 패키지가 로드되면 ADO.NET 원본이 사용할 SQL 문으로 이 속성을 동적으로 업데이트할 수 있습니다. 자세한 내용은 [Integration Services&#40;SSIS&#41; 식](../expressions/integration-services-ssis-expressions.md) 및 [패키지에서 속성 식 사용](../expressions/use-property-expressions-in-packages.md)을 참조하세요.|  
|AllowImplicitStringConversion|Boolean|다음이 발생하는지 여부를 나타내는 값입니다.<br /><br /> 문자열(DT_WSTR 또는 DT_NTEXT)인 출력 열 유형과 외부 메타데이터 유형이 일치하지 않을 경우 유효성 검사 오류를 생성하지 않음<br /><br /> 출력 열이 사용하는 문자열 데이터 형식으로 외부 메타데이터 유형을 암시적으로 변환<br /><br /> <br /><br /> 기본값은 TRUE입니다.<br /><br /> 자세한 내용은 [ADO NET Source](ado-net-source.md)을 참조하세요.|  
  
 ADO.NET 원본의 출력 및 출력 열에는 사용자 지정 속성이 없습니다.  
  
 자세한 내용은 [ADO NET Source](ado-net-source.md)을 참조하세요.  
  
 **대상 사용자 지정 속성**  
  
 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 대상에는 사용자 지정 속성과 모든 데이터 흐름 구성 요소에 공통된 속성이 모두 있습니다.  
  
 다음 표에서는 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 대상의 사용자 지정 속성을 설명합니다. 모든 속성은 읽기/쓰기가 가능합니다. 이러한 속성은 **ADO NET 대상 편집기**에서 사용할 수 없지만 **고급 편집기**를 사용하여 설정할 수 있습니다.  
  
|속성|데이터 형식|Description|  
|--------------|---------------|-----------------|  
|BatchSize|정수|일괄 처리를 통해 서버로 전송되는 행 수입니다. 값 **0** 은 일괄 처리 크기가 내부 버퍼 크기와 일치함을 나타냅니다. 이 속성의 기본값은 **0**입니다.|  
|CommandTimeOut|정수|제한 시간이 초과될 때까지 SQL 명령을 실행할 수 있는 최대 시간(초)입니다. 값 **0** 은 제한 시간이 없음을 의미합니다. 이 속성의 기본값은 **0**입니다.|  
|TableOrViewName|String|대상 테이블 또는 뷰의 이름입니다.|  
  
 자세한 내용은 [ADO NET Destination](ado-net-destination.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [Common Properties](../common-properties.md)  
  
  
