---
title: 열 속성 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.columnprop.f1
ms.assetid: 4046c1a3-46c7-47db-b355-52e9c2f23671
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e091df45f6531dfd0922c795105fe8aadd69b4bc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173189"
---
# <a name="column-properties-ssas-tabular"></a>열 속성(SSAS 테이블 형식)
  이 항목에서는 테이블 형식 모델 열 속성에 대해 설명합니다.  
  
 이 항목의 섹션:  
  
-   [열 속성](#bkmk_properties)  
  
-   [열 속성 설정을 구성 하려면](#bkmk_config_prop)  
  
##  <a name="bkmk_properties"></a> 열 속성  
 **기본**  
  
|속성|기본 설정|Description|  
|--------------|---------------------|-----------------|  
|**열 이름**||모델에 저장되고 보고 클라이언트 필드 목록에 표시되는 열의 이름입니다.|  
|**데이터 형식**|가져오는 동안 자동으로 결정됩니다.|이 열의 데이터에 사용할 표시 형식을 지정합니다. 데이터 형식을 설정한 후 각 형식과 관련된 속성을 설정할 수 있습니다. 예를 들어 **통화** 형식을 선택하는 경우 표시되는 소수 자릿수를 설정하고 천 단위 구분 기호를 선택한 다음 통화 기호를 선택할 수 있습니다. 이 속성에는 다음과 같은 옵션이 있습니다.<br /><br /> **일반**<br /><br /> **10진수**<br /><br /> **정수**<br /><br /> **Currency**<br /><br /> **백분율**<br /><br /> **공학**<br /><br /> 열 값에 이미지가 포함된 경우 **대표 이미지**를 참조하세요.|  
|**데이터 형식**|가져오는 동안 자동으로 결정됩니다.|열에 포함된 모든 값의 데이터 형식을 지정합니다.|  
|**설명**||열에 대한 텍스트 설명입니다.<br /><br /> 일부 보고 클라이언트에서는 최종 사용자가 필드 목록의 이 열 위에 커서를 두면 설명이 도구 설명으로 나타납니다.|  
|**숨김**|False|보고 클라이언트 필드 목록에서 열이 숨겨지는지 여부를 지정합니다.<br /><br /> 이 열을 숨기려면 이 속성을 **True** 로 설정합니다. 예를 들어 식별자나 키가 포함된 열은 일반적으로 최종 사용자에게 유용하지 않습니다.<br /><br /> 보고 클라이언트에서 열을 숨기는 경우 모델 데이터에서는 해당 필드가 표시됩니다. 모델에 대한 쿼리를 만드는 경우 해당 필드가 여전히 표시됩니다. 숨겨진 열을 그룹화나 정렬에 계속 사용할 수 있습니다.<br /><br /> **숨김** 속성은 어떠한 형태의 데이터 보안도 제공하지 않습니다. 데이터를 보호하려면 역할에서 행 필터를 사용합니다. 자세한 내용은 [역할&#40;SSAS 테이블 형식&#41;](roles-ssas-tabular.md)을 참조하세요.|  
|**열 기준 정렬**||이 열의 값을 정렬할 다른 열을 지정합니다. 두 열 간의 관계가 존재해야 합니다.<br /><br /> 이 값은 기존 열의 이름이어야 합니다. 수식 또는 측정값을 지정할 수 없습니다.|  
  
 **보고 속성**  
  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 테이블 동작 속성을 설정하는 방법에 대한 자세한 내용은 [파워 뷰 보고서의 테이블 동작 속성 구성&#40;SSAS 테이블 형식&#41;](power-view-configure-table-behavior-properties-for-reports.md)을 참조하세요.  
  
|속성|기본 설정|Description|  
|--------------|---------------------|-----------------|  
|기본 이미지|False|행 데이터를 표시하는 이미지를 제공하는 열을 지정합니다(예: 직원 레코드의 사진 ID).|  
|기본 레이블|False|행 데이터를 표시하도록 표시 이름을 제공하는 열을 지정합니다(예: 직원 레코드의 직원 이름).|  
|이미지 URL/데이터 범주(SP1)|False|이 열의 값을 서버의 이미지에 대한 하이퍼링크로 지정합니다. 예를 들어 http://localhost/images/image1.jpg을 참조하십시오.|  
|고유한 행 유지|False|중복된 경우에도 고유한 값으로 처리되어야 하는 값을 제공하는 열을 지정합니다(예: 이름이 같은 직원이 여러 명 있는 경우의 직원 이름과 성).|  
|행 식별자|False|열을 내부 그룹화 키로 사용할 수 있도록 고유한 값만 포함하는 열을 지정합니다.|  
|요약 기준|Default|이 열이 필드 목록에 추가될 때 보고 클라이언트 도구에서 열 계산에 대한 집계 함수 SUM을 적용하도록 지정합니다. 기본 계산을 변경하려면 드롭다운 목록에서 기본 계산을 선택합니다. 이 속성은 집계할 수 있는 형식의 열에만 적용됩니다.|  
|테이블 세부 정보 위치|기본 필드 집합 없음|보고 클라이언트에서 테이블 시각화 환경을 개선할 수 있도록 이 열 또는 측정값을 단일 테이블의 필드 집합에 추가할 수 있도록 지정합니다.|  
  
###  <a name="bkmk_config_prop"></a> 열 속성 설정을 구성 하려면  
  
1.  모델 디자이너의 테이블에서 열을 선택합니다.  
  
2.  **속성** 창에서 속성을 클릭한 다음 값을 입력하거나 아래쪽 화살표를 클릭하여 설정 옵션을 선택합니다.  
  
## <a name="see-also"></a>관련 항목  
 [전원 보고 속성을 볼 &#40;SSAS 테이블 형식&#41;](properties-ssas-tabular.md)   
 [열 숨기기 또는 고정 &#40;SSAS 테이블 형식&#41;](hide-or-freeze-columns-ssas-tabular.md)   
 [테이블에 열 추가 &#40;SSAS 테이블 형식&#41;](add-columns-to-a-table-ssas-tabular.md)  
  
  