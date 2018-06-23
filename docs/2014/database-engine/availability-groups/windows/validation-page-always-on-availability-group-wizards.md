---
title: 유효성 검사 페이지 (AlwaysOn 가용성 그룹 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.newagwizard.validation.f1
- sql12.swb.addreplicawizard.validation.f1
- sql12.swb.adddatabasewizard.validation.f1
helpviewer_keywords:
- ', listeners'
ms.assetid: c8971556-240c-491a-bc86-9cc72f71a3dd
caps.latest.revision: 13
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: 6a786543983739efe940631ab05be4d41ab5798e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36183699"
---
# <a name="validation-page-alwayson-availability-group-wizards"></a>유효성 검사 페이지(AlwaysOn 가용성 그룹 마법사)
  이 도움말 항목에서는 **유효성 검사** 페이지의 옵션에 대해 설명합니다. 이 항목은 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]의 [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)], [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 및 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에 적용됩니다. 이 페이지를 사용하여 사용자 환경에서 마법사의 이전 페이지에서 선택한 모든 구성 항목을 지원하는지 확인할 수 있습니다.  
  
##  <a name="PageOptions"></a> 유효성 검사 페이지 옵션  
 **가용성 그룹의 유효성 검사 결과입니다.**  
 이 표는 각 완료된 유효성 검사 단계의 결과를 표시합니다. 표 열은 다음과 같습니다.  
  
 **이름**  
 특정 단계를 설명하는 문구를 표시합니다.  
  
 **결과**  
 다음 하이퍼링크 텍스트 중 하나를 표시합니다. 지정된 유효성 검사 단계의 결과에 대한 자세한 내용을 보려면 하이퍼링크를 클릭하십시오.  
  
|결과|Description|  
|------------|-----------------|  
|**오류**|유효성 검사 단계가 실패했음을 나타냅니다. 오류 메시지를 보려면 링크를 클릭합니다.|  
|**건너뜀**|선택 항목에 필요하지 않아 유효성 검사 단계를 건너뛰었음을 나타냅니다. 단계를 건너뛴 이유를 보려면 링크를 클릭합니다.|  
|**성공**|유효성 검사 단계가 완료되었음을 나타냅니다.|  
|**경고**|가용성 그룹 구성에 대한 잠재적 문제를 나타냅니다.  경고 메시지를 보려면 링크를 클릭합니다.|  
  
 **유효성 검사 다시 실행**  
 유효성 검사 오류에 응답하여 마법사 외부에서 변경할 경우 유효성 검사 단계를 반복하려면 클릭합니다.  
  

  
##  <a name="RelatedTasks"></a> 관련 태스크  
  
-   [새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [가용성 그룹에 복제본 추가 마법사 사용&#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [가용성 그룹에 데이터베이스 추가 마법사 사용&#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md)  
  
 
  
## <a name="see-also"></a>관련 항목  
 [AlwaysOn 가용성 그룹 개요 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  