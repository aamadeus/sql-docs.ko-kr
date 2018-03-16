---
title: "Analysis Services tutorial 11 단원: 역할 만들기 | Microsoft Docs"
description: "Analysis Services tutorial 프로젝트에서 역할을 만들 방법을 설명 합니다."
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: 
author: Minewiskan
manager: kfile
editor: 
tags: 
ms.assetid: 
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: na
ms.date: 02/20/2018
ms.author: owend
ms.openlocfilehash: b3ed6028a02b117fb6cdb87a8097d1e1eab48b0f
ms.sourcegitcommit: 7ed8c61fb54e3963e451bfb7f80c6a3899d93322
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2018
---
# <a name="create-roles"></a>역할 만들기

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

이 단원에서는 역할을 만듭니다. 역할은 역할 멤버인 사용자만에 대 한 액세스를 제한 하 여 모델 데이터베이스 개체 및 데이터 보안을 제공 합니다. 각 역할은 없음, 읽기, 읽기 및 처리, 처리 또는 관리자라는 단일 사용 권한으로 정의됩니다. 역할 관리자를 사용 하 여 모델을 제작 하는 동안 역할을 정의할 수 있습니다. 모델을 배포한 후에 SQL Server Management Studio (SSMS)를 사용 하 여 역할을 관리할 수 있습니다. 자세한 내용은 참고 [역할](../tabular-models/roles-ssas-tabular.md)합니다.
  
> [!NOTE]  
> 이 자습서를 완료하기 위해 역할을 만들 필요는 없습니다. 기본적으로 현재 로그인 하는 계정 관리자에 대 한 권한이 모델입니다. 그러나 보고 클라이언트를 사용 하 여 찾아보려면 조직의 다른 사용자에 대 한 사용 권한을 읽기 역할을 하나 이상 만들 하며 해당 사용자가 구성원으로 추가 합니다.  
  
세 가지 역할을 만들 있습니다.  
  
-   **영업 관리자** –이 역할 모든 모델 개체와 데이터에 읽기 권한이 하려는 조직에서 사용자를 포함할 수 있습니다.  
  
-   **Sales Analyst US** –이 역할에 미국 내에서 판매와 관련 된 데이터를 탐색할 수에 할당할 조직의 사용자를 포함할 수 있습니다. 이 역할에 대해 정의 하는 DAX 수식을 사용는 *행 필터*, United States에 대 한 데이터를 검색 하는 멤버 제한 합니다.  
  
-   **관리자** –이 역할에서 관리자 권한을 할당 해 무제한 액세스 및 model 데이터베이스에서 관리 작업을 수행할 수 있는 권한이 있는 사용자를 포함할 수 있습니다.  
  
조직의 Windows 사용자 및 그룹 계정은 고유하므로 특정 조직의 계정을 멤버에 추가할 수 있습니다. 그러나 이 자습서에서는 멤버를 비워둘 수도 있습니다. 나중에 12 단원 각 역할의 효과 테스트할: Excel에서 분석 합니다.  
  
이 단원에 소요되는 예상 시간: **15분**  
  
## <a name="prerequisites"></a>필수 구성 요소  

이 문서는 순서 대로 완료 해야 하는 테이블 형식 모델링 자습서의 일부입니다. 이 단원의 태스크를 수행 하기 전에 완료 해야 이전 단원: [10 단원: 파티션 만들기](../tutorial-tabular-1400/as-lesson-10-create-partitions.md)합니다.  
  
## <a name="create-roles"></a>역할 만들기  
  
#### <a name="to-create-a-sales-manager-user-role"></a>Sales Manager 사용자 역할을 만들려면  
  
1.  테이블 형식 모델 탐색기에서 마우스 오른쪽 단추로 클릭 **역할** > **역할**합니다.  
  
2.  역할 관리자에서 클릭 **새로**합니다.  
  
3.  새 역할을 클릭 한 다음는 **이름** 열을 역할 이름 바꾸기 **판매 관리자**합니다.  
  
4.  **사용 권한** 열에서 드롭다운 목록을 클릭한 다음 **읽기** 권한을 선택합니다. 

    ![as-lesson11-new-role](../tutorial-tabular-1400/media/as-lesson11-new-role.png) 
  
5.  선택 사항: 클릭는 **멤버** 탭을 클릭 한 다음 **추가**합니다. **사용자 또는 그룹 선택** 대화 상자에서 역할에 포함할 조직의 Windows 사용자 또는 그룹을 입력합니다.  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a>Sales Analyst US 사용자 역할을 만들려면  
  
1.  역할 관리자에서 클릭 **새로**합니다.    
  
2.  역할 이름 바꾸기 **Sales Analyst US**합니다.  
  
3.  이 역할을 부여 **읽기** 권한.  
  
4.  행 필터 탭을 클릭 한 후의 **DimGeography** 테이블만 DAX 필터 열에 다음 수식을 입력 합니다.  
  
    ```Administrator
    =DimGeography[CountryRegionCode] = "US" 
    ```
    
    행 필터 수식은 부울(TRUE/FALSE) 값으로 확인되어야 합니다. 이 수식을 사용 하 여 지정 하는 행만 Country Region Code 값 "미국" 사용자에 게 표시 됩니다.  
    ![as-lesson11-role-filter](../tutorial-tabular-1400/media/as-lesson11-role-filter.png) 
  
6.  선택 사항: 클릭는 **멤버** 탭을 클릭 한 다음 **추가**합니다. **사용자 또는 그룹 선택** 대화 상자에서 역할에 포함할 조직의 Windows 사용자 또는 그룹을 입력합니다.  
  
#### <a name="to-create-an-administrator-user-role"></a>관리자 사용자 역할을 만들려면  
  
1.  **새로 만들기**를 클릭합니다.  
  
2.  역할 이름 바꾸기 **관리자**합니다.  
  
3.  이 역할을 부여 **관리자** 권한.  
  
4.  선택 사항: 클릭는 **멤버** 탭을 클릭 한 다음 **추가**합니다. **사용자 또는 그룹 선택** 대화 상자에서 역할에 포함할 조직의 Windows 사용자 또는 그룹을 입력합니다. 
  
  
## <a name="whats-next"></a>다음 단계

[12 단원: Excel에서 분석](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md)합니다.

  
  