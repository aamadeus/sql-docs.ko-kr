---
title: 일반 (데이터베이스 디자이너) (Analysis Services-다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.databasedesigner.dbconfigurationpane.f1
helpviewer_keywords:
- Database Designer
ms.assetid: 00c9c42b-db2b-4620-8fb6-1e165ff0cbdd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1a353d633287ad4b535a88b9ba76fa403a20c9e4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48195813"
---
# <a name="general-database-designer-analysis-services---multidimensional-data"></a>일반(데이터베이스 디자이너)(Analysis Services - 다차원 데이터)
  **일반** 탭을 사용하여 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스의 속성을 변경할 수 있습니다.  
  
 **일반 탭을 표시 하려면**  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트를 엽니다.  
  
2.  **솔루션 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트를 마우스 오른쪽 단추로 클릭하고 **데이터베이스 편집**을 클릭한 다음 **일반** 탭을 클릭합니다.  
  
## <a name="basic-options"></a>기본 옵션  
 **기본** 섹션을 확장하여 데이터베이스에 대한 기본 정보를 수정할 수 있습니다. 이 섹션에는 다음 옵션이 있습니다.  
  
 **데이터베이스 이름**  
 데이터베이스 이름을 표시합니다.  
  
> [!NOTE]  
>  데이터베이스 이름을 바꾸려면 **솔루션 탐색기**에서 해당 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다. 데이터베이스 **속성 페이지** 대화 상자의 **배포** 페이지에서 **데이터베이스** 속성 값을 새 데이터베이스 이름으로 변경합니다.  
  
 **설명**  
 데이터베이스에 대한 설명을 입력합니다.  
  
## <a name="translations-options"></a>번역 옵션  
 **번역** 섹션을 확장하여 데이터베이스 캡션 및 설명의 번역을 생성 및 수정할 수 있습니다. 이 섹션에서는 다음 열을 다루는 표를 제공합니다.  
  
 **언어**  
 지정한 트랜잭션의 언어를 선택합니다.  
  
 새 번역을 표에 추가 하려면 클릭  **\<새 번역 추가 >** 합니다.  
  
 **번역 된 캡션**  
 번역에 해당하는 언어로 데이터베이스 캡션을 입력합니다. 공백인 경우 기본 데이터베이스 캡션이 사용됩니다.  
  
 **번역 된 설명**  
 번역에 해당하는 언어로 데이터베이스 설명을 입력합니다. 공백인 경우 기본 데이터베이스 설명이 사용됩니다.  
  
## <a name="account-type-mapping-options"></a>계정 유형 매핑 옵션  
 **계정 유형 매핑** 섹션을 확장하여 선택한 데이터베이스의 각 계정 **유형** 과 연결된 기본 집계 함수를 수정할 수 있습니다.  
  
> [!NOTE]  
>  이 옵션은 *ByAccount* 집계 함수를 사용하는 측정값이 하나 이상인 큐브에서만 실행됩니다.  
  
 이 섹션에서는 다음 열을 다루는 표를 제공합니다.  
  
 **이름**  
 계정 유형의 이름을 입력합니다.  
  
 새 계정 유형을 추가 하려면 클릭  **\<새 계정 유형 추가 >** 합니다.  
  
 **별칭**  
 비즈니스 인텔리전스 마법사에서 사용할 계정 유형의 기본 이름을 설정합니다. 이 열을 비워 두면 **이름** 열의 기본값이 사용됩니다.  
  
 **집계 함수**  
 선택한 계정 유형에 사용할 집계 함수를 선택합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Analysis Services Designers and Dialog Boxes &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [다차원 Model 데이터베이스 &#40;SSAS&#41;](multidimensional-models/multidimensional-model-databases-ssas.md)   
 [경고 &#40;데이터베이스 디자이너&#41; &#40;Analysis Services-다차원 데이터&#41;](warnings-database-designer-analysis-services-multidimensional-data.md)  
  
  
