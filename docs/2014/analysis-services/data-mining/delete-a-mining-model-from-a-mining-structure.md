---
title: 마이닝 구조에서 마이닝 모델 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2b09560d26d201ced8160bf171a92dbb618a1c94
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48180373"
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a>마이닝 구조에서 마이닝 모델 삭제
  데이터 마이닝 디자이너, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 DMX 문을 사용하여 마이닝 모델을 삭제할 수 있습니다.  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a>SQL Server Data Tools를 사용하여 마이닝 모델 삭제  
  
1.  **에서** 마이닝 모델 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]탭을 선택합니다.  
  
2.  삭제할 모델을 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.  
  
     **개체 삭제** 대화 상자가 열립니다.  
  
3.  **확인**을 클릭합니다.  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a>SQL Server Management Studio를 사용하여 마이닝 모델 삭제  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 모델이 포함된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 엽니다.  
  
2.  **마이닝 구조**를 확장하고 **마이닝 모델**을 확장합니다.  
  
3.  삭제할 모델을 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.  
  
     모델을 삭제해도 학습 데이터는 삭제되지 않고 모델을 학습할 때 메타데이터 및 패턴만 삭제됩니다.  
  
### <a name="delete-a-mining-model-using-dmx"></a>DMX를 사용하여 마이닝 모델 삭제  
  
-   [DROP 마이닝 모델 &AMP;#40;DMX&AMP;#41;](/sql/dmx/drop-mining-model-dmx)  
  
## <a name="see-also"></a>관련 항목  
 [마이닝 모델 태스크 및 방법](mining-model-tasks-and-how-tos.md)  
  
  
