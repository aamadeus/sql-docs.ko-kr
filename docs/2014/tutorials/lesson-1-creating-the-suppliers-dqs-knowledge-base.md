---
title: '1 단원: 공급자 DQS 기술 자료 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 78825ccb-30fc-463c-8140-435532e2ecd2
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 58f787d1204cde60dee3a10fdaf587b52cf6dfa4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36186867"
---
# <a name="lesson-1-creating-the-suppliers-dqs-knowledge-base"></a>1단원: 공급자 DQS 기술 자료 만들기
  이 단원에서는 공급자 데이터에 대한 지식(메타데이터)이 포함된 **Suppliers** 라는 DQS 기술 자료를 만듭니다. 이 기술 자료는 입력 공급자 데이터에 대해 정리 및 일치 작업을 수행하는 데 사용됩니다. 정리 작업은 잘못된/올바르지 않은 데이터를 식별하고, 잘못된 데이터를 수정하고, 수정/제안을 제공하고, 데이터를 표준화하고, 자세한 정보를 사용해서 데이터를 강화합니다. 일치 작업은 데이터를 비교하고 데이터에서 중복 항목을 제거하는 데 도움이 될 수 있도록 데이터에서 비슷하지만 약간 다른 레코드를 식별합니다.  
  
 대화형 및 컴퓨터 기반 프로세스를 모두 사용해서 기술 자료를 만들고, 빌드 및 관리할 수 있습니다. 기술 자료에서 지식은 도메인에서 유지 관리되며 이러한 각 기술 자료는 정리 및/또는 일치 작업을 수행하려는 데이터의 특정 데이터 필드와 관련이 있습니다.  
  
 이 단원에서는 다음 작업을 수행하여 **Suppliers** 기술 자료를 만듭니다.  
  
-   **Suppliers**라는 DQS 기술 자료를 만듭니다. 기술 자료는 여러 가지 방법으로 만들 수 있습니다. 기술 자료는 처음부터 새로 만들거나, 기존 기술 자료를 기반으로 해서 만들거나, 미리 작성되어 내보낸 기술 자료가 포함된 DQS 파일(.dqs)을 가져와서 만들거나, 예제 데이터에 대해 기술 자료 검색 작업을 수행하여 만들 수 있습니다. 이 자습서에서는 기술 자료를 처음부터 새로 만듭니다.  
  
-   중복 항목을 식별할 수 있도록 데이터 정리 및 데이터 일치 작업에 사용하는 도메인을 **Suppliers** 기술 자료에 만듭니다. 데이터의 모든 데이터 필드가 아니라 정리 및 일치 작업에 사용하려는 데이터 필드에 대해 도메인을 만듭니다.  
  
-   값을 수동으로 추가하거나, Excel 파일에서 값을 가져오거나, 예제 데이터에 대해 기술 자료 검색 작업을 수행하거나, 정리 프로젝트에서 프로젝트 값을 가져와서 도메인에 값을 추가합니다. 또한 이 자습서에서 수행하지 않는 도메인 속성 및 값이 포함된 DQS 파일을 가져와서 도메인 값을 가져올 수도 있습니다.  
  
-   도메인에 대한 규칙을 설정합니다. 도메인 규칙은 DQS에서 도메인 값의 유효성 검사, 수정 및 표준화를 수행하는 데 사용되는 조건입니다.  
  
-   도메인에 대한 용어 기반 관계를 설정합니다. 용어 기반 관계를 사용하면 도메인에서 값의 일부인 용어를 수정할 수 있습니다. 예를 들어 **Contoso Inc.라는 값에서 Inc.** 는 Incorporated로 정의될 수 있는 용어입니다. 이렇게 하면 중복 항목을 식별하는 것뿐만 아니라 데이터를 표준화하는 데에도 도움이 됩니다. 예를 들어 **Contoso Inc.** 와 **Contoso Incorporated** 는 중복 항목으로 고려될 수 있습니다.  
  
-   도메인 값에 동의어를 지정합니다. 두 개 이상의 값을 동의어로 설정하고 이중 하나를 데이터 표준화를 위한 정리 작업 중 해당 동의어 값 대신 사용되는 선행 값으로 설정할 수 있습니다.  
  
-   Address line, City, State 및 Zip 도메인으로 구성되는 Address Validation이라는 복합 도메인을 만듭니다. 복합 도메인은 하나 이상의 단일 도메인으로 구성된 도메인입니다. 복합 도메인을 사용하면 여러 도메인에 관련된 규칙을 만들 수 있습니다. 예를 들어 City 및 State가 두 개의 개별 도메인이라고 가정할 때 City가 Los Angeles이면 State가 CA여야 하는 규칙을 정의할 수 있습니다.  
  
-   참조 데이터 서비스를 구성하고 사용합니다. DQS(Data Quality Services)의 참조 데이터 서비스 기능을 사용하면 타사 참조 데이터 공급자를 구독하고 고품질 데이터를 기준으로 비즈니스 데이터의 유효성을 검사하여 비즈니스 데이터를 정리하고 강화할 수 있습니다. 정리 프로세스가 진행되는 동안 DQS 내에서 유명 DQS 공급자의 서비스를 사용하여 데이터를 표준화, 수정 또는 강화할 수 있습니다. 이 자습서에서는 Windows Azure 마켓플레이스에서 참조 데이터 서비스를 사용하도록 DQS 환경을 구성하고 Address Validation 복합 도메인과 연관된 서비스를 사용해서 주소 데이터를 정리하는 방법에 대해 알아봅니다.  
  
-   정리 및 일치 작업에서 기술 자료를 사용할 수 있도록 기술 자료를 게시합니다.  
  
## <a name="next-step"></a>다음 단계  
 [태스크 1: 기술 자료 및 도메인 만들기](../../2014/tutorials/task-1-creating-a-knowledge-base-and-domains.md)  
  
  