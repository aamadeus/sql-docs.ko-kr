---
title: "DQS의 데이터 프로파일링 및 알림 | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2012"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a778bb5b-8e35-4a7b-b04a-ae2b46dec21b
caps.latest.revision: 25
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 25
---
# DQS의 데이터 프로파일링 및 알림
  DQS([!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)])의 데이터 프로파일링은 기존 데이터 원본의 데이터를 분석하고 DQS 작업의 데이터에 대한 통계를 표시하는 프로세스입니다. 자동화된 데이터 품질 평가를 제공합니다. DQS 프로파일링은 DQS 기술 자료 관리 및 데이터 품질 프로젝트에 통합되어 있습니다. 동적이며 조정 가능합니다. 프로파일링에는 두 가지 주요 목표가 있습니다. 첫째는 데이터 품질 프로세스를 안내하고 의사 결정을 지원하는 것이고, 둘째는 프로세스의 효율성을 평가하는 것입니다. DQS 프로파일링 프로세스에는 다음과 같은 이점이 있습니다.  
  
-   프로파일링은 원본 데이터의 품질에 대한 통찰력을 제공하고 데이터 품질 문제를 식별하도록 도와줍니다.  
  
-   프로파일링은 데이터 품질 프로세스의 효율성을 평가하여 기술 자료 검색, 데이터 정리, 일치 정책 및 일치 작업의 과정을 설명합니다.  
  
-   프로파일링은 가장 적절한 시간에 가장 적절한 정보를 제공합니다.  
  
-   프로파일링 프로세스는 조치가 필요한 중요한 통계 또는 이벤트를 강조하는 알림을 생성합니다. 대부분의 경우 DQS 알림은 특정 상태를 나타내고 해당 상태를 해결하기 위해 수행할 수 있는 작업을 권장합니다.  
  
 프로파일링을 통해 Data Quality Services를 기술 자료 검색, 정리 및 일치 용도뿐만 아니라 분석 도구로도 사용할 수 있습니다. 분석용 기술 자료를 하나 만들고 해당 기술 자료로 기술 자료 검색을 실행하여 프로파일 통계를 통해 기술 자료가 검색, 정리 및 일치 요구 사항을 만족하는지 파악할 수 있습니다.  
  
##  <a name="How"></a> 프로파일 작동 방식  
 프로파일링은 기술 자료의 품질을 평가하지 않습니다. 원본 데이터의 품질을 평가합니다. 프로파일링은 원본 데이터에 대한 기술 자료 관리 또는 데이터 품질 프로젝트에서 수행 중인 특정 작업의 결과를 나타내는 통계를 제공합니다. 프로파일링은 항상 현재 수행 중인 특정 작업의 컨텍스트에서 실행됩니다. 특정 화면에서 프로파일링 탭을 클릭하면 현재 수행 중인 작업의 단계를 나가지 않고도 프로파일링 데이터를 표시할 수 있습니다. 프로파일링 테이블은 프로세스가 수행될 때 실시간으로 채워지므로 데이터 품질 태스크를 수행하면서 해당 태스크를 평가할 수 있습니다. 정리 또는 중복 제거 후 원본 데이터가 개선되었는지, 그렇다면 얼마나 개선되었는지 확인할 수 있습니다.  
  
 모든 프로파일링 숫자는 값의 발생 횟수를 나타내며 고유성 메트릭을 제외하고 대부분 합계에 대한 백분율로 표시됩니다. 고유성 메트릭은 값의 발생 횟수에 관계없이 값의 절대 개수를 나타냅니다.  
  
 프로파일링은 DQS 기술 자료 기반 솔루션의 일부입니다. 데이터 원본 필드와 기술 자료 도메인 간 매핑에 따라 기술 자료, 일치 또는 데이터 정리 프로세스에 대한 정보를 제공합니다. 프로파일링은 매핑이 완료된 후에만 수행됩니다. 작업의 매핑 단계 도중에는 수행되지 않습니다. 프로파일링은 항상 특정 작업에 연결됩니다. 프로파일링 프로세스는 도메인의 데이터가 아니라 도메인에 매핑된 데이터에 대해 수행됩니다. 프로파일링은 다음과 같은 작업 단계에 통합되어 있습니다.  
  
-   기술 자료 검색 작업의 **검색** 및 **도메인 값 관리** 단계  
  
-   정리 작업의 **정리** 및 **결과 관리 및 보기** 단계  
  
-   일치 정책 작업의 **일치 정책** 및 **일치 결과** 단계  
  
-   일치 정책 작업의 **일치** 및 **내보내기** 단계  
  
 DQS에서는 도메인 관리 작업에 대한 프로파일링 통계를 제공하지 않습니다.  
  
##  <a name="Activity"></a> 작업별 데이터 프로파일링  
 DQS 프로파일링에서는 완결성(데이터가 존재하는 정도), 정확도(데이터를 의도된 용도에 맞게 사용할 수 있는 정도) 및 고유성(여러 값이 여러 엔터티를 나타내는 정도)의 표준 데이터 품질 차원을 사용하여 데이터의 품질을 나타냅니다. 기본적으로 NULL과 빈 값은 누락되었거나 완결성 백분율이 낮은 것으로 간주됩니다. 그러나 다른 값을 NULL에 해당하는 값으로 정의할 수 있으며, 이 경우 이러한 값은 누락된 것으로 간주됩니다.  
  
 프로파일링에서 프로세스를 평가하는 데 필요한 통계를 제공하지만 통계 해석은 사용자가 수행해야 합니다. 통계를 열 단위로 보면서 프로파일링의 결과를 이해하세요.  
  
 DQS 작업에는 다음과 같은 여러 프로파일링 통계 집합이 있습니다.  
  
-   정리 작업에만 정확도에 대한 프로파일링 통계가 있습니다(도메인별 백분율). 정확도는 유효성, 일관성, 구문 오류 및 도메인 규칙의 영향을 받습니다.  
  
-   정리 작업에만 원본의 올바름, 수정됨 및 제안과 도메인별 수정됨 및 제안 값에 대한 프로파일링 통계가 있습니다(모두 백분율).  
  
-   정리 및 기술 자료 검색 작업에는 유효성에 대한 프로파일링 통계가 있습니다(레코드별 정리, 레코드 및 도메인별 기술 자료 검색). 일치 정책과 일치 작업에는 유효성에 대한 통계가 없습니다.  
  
-   정리 작업에는 고유성에 대한 프로파일링 통계가 없습니다. 기술 자료 검색, 일치 정책 및 일치 작업에는 원본에 대한 고유성과 도메인별 고유성에 대한 숫자와 백분율 단위의 프로파일링 통계가 있습니다.  
  
 특정 작업과 관련된 특정 프로파일링 통계에 대한 자세한 내용은 다음 항목의 프로파일링 섹션을 참조하세요.  
  
-   [기술 자료 검색 수행](../data-quality-services/perform-knowledge-discovery.md)  
  
-   [DQS & #40;를 사용 하 여 데이터를 정리 내부 & #41; 기술](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)  
  
-   [일치 정책 만들기](../data-quality-services/create-a-matching-policy.md)  
  
-   [일치 프로젝트 실행](../data-quality-services/run-a-matching-project.md)  
  
##  <a name="Monitoring"></a> 작업 모니터링 데이터 프로파일링  
 기술 자료 검색, 일치 정책, 일치 및 정리 작업에 대한 프로파일링 정보는 Data Quality 클라이언트의 작업 페이지뿐만 아니라 작업 모니터링에서도 볼 수 있습니다. 작업 모니터링은 현재 및 이전 작업에 대한 개요를 제공합니다. 작업의 속성 및 관련 계산 프로세스 외에도 각 작업에 대해 생성된 프로파일링 정보를 한 곳에서 볼 수 있습니다. 작업 테이블에서 특정 작업을 선택하여 아래 테이블에 프로파일링 결과를 표시할 수 있습니다. 또한 프로파일링 결과를 내보낼 수도 있습니다. 자세한 내용은 [DQS Administration](../data-quality-services/dqs-administration.md)을 참조하세요.  
  
##  <a name="Notifications"></a> 알림  
 DQS에서는 프로파일링을 통해 중요한 통계와 메트릭을 수집하고 표시하는 것 외에도 표시된 프로파일링 통계에 따라 작업을 수행해야 할 시기를 알려 주는 알림을 생성합니다(설정된 경우). DQS에서는 알림을 사용하여 데이터 원본에 대한 중요한 사실을 강조하고 실행 목적을 기준으로 한 현재 작업의 효율성을 표시합니다. 알림은 팁과 권장 사항을 제공하여 특정 상태를 나타내고 기술 자료 검색, 데이터 정리 또는 데이터 일치 작업을 개선할 수 있는 방법을 권장합니다.  
  
 DQS 알림은 사용자가 관심을 가질만한 문제를 언급하거나 잠재적인 문제를 해결하는 데 사용됩니다. 알림이 목적과 관련이 있는지에 따라 알림에 대해 작업을 수행할지 여부가 달라집니다. 예를 들어 완결성과 정확도가 모두 100%인 상태에서 데이터 정리가 수정된 값이나 제안된 값을 생성하지 않은 경우 DQS에서 알림을 게시했다고 가정하겠습니다. 이 알림에서는 작업을 실행할 필요가 없다는 메시지가 표시될 것입니다. 그러나 작업을 실행하도록 선택할지 여부는 사용자가 결정할 일입니다.  
  
 알림은 **프로파일링** 탭에서 느낌표가 있는 도구 설명으로 표시됩니다. 알림과 관련된 통계가 빨간색으로 표시되어 알림에 대한 통계적 이유를 알려줍니다.  
  
 알림을 사용 하지 않도록 설정 하거나 (기본값)을 설정할 수 있습니다는 **일반 설정** 탭은 **관리** Data Quality 클라이언트 홈 페이지의 섹션입니다. 알림이 해제되면 도구 설명이 표시되지 않고 통계가 빨간색으로 표시되지 않습니다. 알림을 해제할 경우 성능에 큰 이점은 없습니다. 알림을 해제해도 프로파일링은 계속 작동합니다.  
  
 특정 작업에 대한 알림과 관련된 특정 상태는 다음을 참조하세요.  
  
-   [기술 자료 검색 수행](../data-quality-services/perform-knowledge-discovery.md)  
  
-   [DQS & #40;를 사용 하 여 데이터를 정리 내부 & #41; 기술](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)  
  
-   [일치 정책 만들기](../data-quality-services/create-a-matching-policy.md)  
  
-   [일치 프로젝트 실행](../data-quality-services/run-a-matching-project.md)  
  
## 관련 태스크  
  
|태스크 설명|항목|  
|----------------------|-----------|  
|DQS에서 알림을 설정 또는 해제하는 방법에 대해 설명합니다.|[DQS에서 프로파일링 알림 설정 또는 해제](../data-quality-services/enable-or-disable-profiling-notifications-in-dqs.md)|  
  
  