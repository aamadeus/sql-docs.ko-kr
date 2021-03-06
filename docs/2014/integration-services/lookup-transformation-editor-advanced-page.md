---
title: 조회 변환 편집기 (고급 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.advanced.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: f3395c65-0320-47f9-8d83-daaa082d8713
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: aa56e9366fdc60a5b411e19b200706f0404e7312
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209733"
---
# <a name="lookup-transformation-editor-advanced-page"></a>조회 변환 편집기(고급 페이지)
  **조회 변환 편집기** 대화 상자의 **고급** 페이지를 사용하여 조회 변환의 부분 캐싱을 구성하고 SQL 문을 수정할 수 있습니다.  
  
 조회 변환에 대한 자세한 내용은 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)을 참조하십시오.  
  
## <a name="options"></a>변수  
 **캐시 크기(32비트)**  
 32비트 컴퓨터의 캐시 크기(MB)를 조정합니다. 기본값은 5MB입니다.  
  
 **캐시 크기(64비트)**  
 64비트 컴퓨터의 캐시 크기(MB)를 조정합니다. 기본값은 5MB입니다.  
  
 **일치하는 항목이 없는 행에 캐시 사용**  
 참조 데이터 집합에서 일치하는 항목이 없는 행을 캐시합니다.  
  
 **캐시에서 할당**  
 참조 데이터 집합에서 일치하는 항목이 없는 행에 할당할 캐시 비율을 지정합니다.  
  
 **SQL 문 수정**  
 참조 데이터 집합을 생성하는 데 사용되는 SQL 문을 수정합니다.  
  
> [!NOTE]  
>  이 페이지에서 지정하는 선택적 SQL 문이 **조회 변환 편집기** 의 **연결**페이지에서 지정한 테이블 이름을 재정의하고 대체합니다. 자세한 내용은 [조회 변환 편집기 &#40;연결 페이지&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)합니다.  
  
 **매개 변수**  
 **쿼리 매개 변수 설정** 대화 상자를 사용하여 입력 열을 매개 변수에 매핑합니다.  
  
## <a name="external-resources"></a>외부 리소스  
 blogs.msdn.com의 블로그 항목 - [조회 캐시 모드](http://go.microsoft.com/fwlink/?LinkId=219518)  
  
## <a name="see-also"></a>관련 항목  
 [조회 변환 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md)   
 [조회 변환 편집기 &#40;연결 페이지&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)   
 [조회 변환 편집기&#40;열 페이지&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md)   
 [조회 변환 편집기 &#40;오류 출력 페이지&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)   
 [Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [유사 항목 조회 변환](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
