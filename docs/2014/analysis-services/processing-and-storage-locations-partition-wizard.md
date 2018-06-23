---
title: 처리 및 저장소 위치 (파티션 마법사) | Microsoft Docs
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
- sql12.asvs.partitionwizard.specifyprocessingandstorage.f1
ms.assetid: dda2dc57-923d-4db9-93a7-38e95770f3df
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e86bb343a13cd17cca7fa561445c2105725c4369
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36185280"
---
# <a name="processing-and-storage-locations-partition-wizard"></a>처리 및 저장소 위치(파티션 마법사)
  **처리 및 저장소 위치** 페이지를 사용하여 파티션에 대한 데이터를 저장하는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스뿐만 아니라 해당 파티션을 소유하는 큐브의 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스도 지정할 수 있습니다. 원격 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스 또는 기본 저장소 위치 이외의 저장소 위치를 지정하여 파티션을 원격 파티션으로 정의할 수 있습니다. 원격 파티션에 대한 자세한 내용은 [원격 파티션](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md)을 참조하세요.  
  
## <a name="processing-location-options"></a>처리 위치 옵션  
 **현재 서버 인스턴스**  
 현재 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에서 파티션을 처리하도록 지정합니다.  
  
 **원격 Analysis Services 데이터 원본**  
 원격 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에서 파티션을 처리하도록 지정합니다.  
  
 드롭다운 목록에서 파티션을 처리할 원격 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스를 나타내는 데이터 원본을 선택합니다.  
  
> [!NOTE]  
>  `Initial Catalog` 연결 문자열 속성이 유효한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스로 설정되어 있지 않은 데이터 원본을 선택하거나 `Initial Catalog` 연결 문자열 속성에서 지정한 데이터베이스가 원격 파티션을 지원하지 않는 경우, 즉 지정한 데이터베이스의 `MasterDatasourceID` 속성이 유효한 값으로 설정되어 있지 않은 경우 오류가 발생합니다.  
  
 **새로 만들기**  
 파티션을 처리할 원격 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스를 나타내는 새 데이터 원본을 만듭니다.  
  
## <a name="storage-location-options"></a>저장소 위치 옵션  
 **기본 서버 위치**  
 현재 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스의 데이터 폴더를 파티션에 대한 집계 및 인덱싱 데이터의 저장소 위치로 지정합니다.  
  
 **지정 된 폴더**  
 파티션에 대한 집계 및 인덱싱 데이터의 저장소 위치를 지정합니다.  
  
 **...**  
 **지정한 폴더** 에 대한 폴더를 선택할 수 있는 **원격 폴더 찾아보기**대화 상자를 표시합니다.  
  
## <a name="see-also"></a>관련 항목  
 [파티션 마법사 F1 도움말 &#40;Analysis Services-다차원 데이터&#41;](partition-wizard-f1-help-analysis-services-multidimensional-data.md)   
 [파티션 &#40;Analysis Services-다차원 데이터&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [원격 폴더 찾아보기 대화 상자 &#40;Analysis Services-다차원 데이터&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)  
  
  