---
title: 추가, 데이터 업데이트 및 삭제 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: b6295ead-bd2f-49dd-8756-35c6afb59648
author: leolimsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6751dcfca820fcd7bdcdf73ff6979e572c7159fa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48066593"
---
# <a name="add-update-and-delete-data-master-data-services"></a>데이터 추가, 업데이트 및 삭제(MDS(Master Data Services))
  데이터를 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]의 모델에 대량으로 추가하고 변경할 수 있습니다.  
  
 **필수 구성 요소**  
  
-   데이터를 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스의 stg.\<name>_Leaf, stg.\<name>_Consolidated, stg.\<name>_Relationship 테이블에 삽입할 수 있는 권한이 있어야 합니다.  
  
-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에서 stg.udp_\<name>_Leaf, stg.udp\_\<name>_Consolidated 또는 stg.udp\_\<name>_Relationship 저장 프로시저를 실행할 수 있는 권한이 있어야 합니다.  
  
-   모델이 **커밋됨**상태가 아니어야 합니다.  
  
 **[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에서 데이터를 추가, 업데이트 및 삭제하려면**  
  
1.  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스의 적절한 준비 테이블로 가져올 구성원을 준비합니다. 예를 들어 필수 필드의 값을 입력합니다. 준비 테이블의 개요를 보려면 [데이터 가져오기 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
    -   리프 멤버의 경우 테이블은 stg.\<name>_Leaf입니다. 여기서 \<name>은 해당 엔터티를 나타냅니다. 필수 필드에 대한 자세한 내용은 [리프 멤버 준비 테이블&#40;Master Data Services&#41;](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md)을 참조하세요.  
  
    -   통합 멤버의 경우 테이블은 stg.\<name>_Consolidated입니다. 필수 필드에 대한 자세한 내용은 [통합 멤버 준비 테이블&#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md)을 참조하세요.  
  
    -   명시적 계층에서 멤버의 위치를 이동하는 경우 테이블은 stg.\<name>_Relationship입니다. 필수 필드에 대한 자세한 내용은 [관계 준비 테이블&#40;Master Data Services&#41;](../../2014/master-data-services/relationship-staging-table-master-data-services.md)을 참조하세요.  
  
         명시적 계층에서 멤버 이동에 대 한 개요를 참조 하세요 [데이터 가져오기 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)합니다.  
  
    -   **ImportType** 필드 값을 사용하여 새 구성원을 만드는지, 구성원을 비활성화하는지 또는 구성원을 삭제하는지를 명시합니다. 값에 대한 자세한 내용은 [리프 멤버 준비 테이블&#40;Master Data Services&#41;](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md) 및 [통합 멤버 준비 테이블&#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md)을 참조하세요.  
  
         멤버 비활성화 및 삭제의 개요를 보려면 [데이터 가져오기 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)합니다.  
  
2.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 열고 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스의 데이터베이스 엔진 인스턴스에 연결합니다.  
  
     자세한 내용은 [SQL Server Management Studio](../ssms/sql-server-management-studio-ssms.md)를 참조하세요.  
  
3.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사를 사용하여 준비 테이블로 데이터 가져옵니다.  
  
     자세한 내용은 [SQL Server Import and Export Wizard](../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조하세요.  
  
4.  다음 중 하나를 수행하여 준비 테이블에서 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 테이블로 데이터를 로드합니다.  
  
    -   데이터를 이동하려는 준비 테이블에 해당하는 준비 저장 프로시저를 실행합니다.  
  
         준비 저장된 프로시저 및 준비 테이블의 개요를 보려면 [데이터 가져오기 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)합니다. 준비 저장 프로시저의 매개 변수에 대한 자세한 내용과 코드 예제는 [준비 저장 프로시저&#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md)를 참조하세요.  
  
    -   마스터 데이터 관리의 **통합 관리** 기능 영역을 사용합니다.  
  
         **준비 일괄 처리** 페이지의 드롭다운 목록에서 데이터를 추가할 모델을 선택한 다음 **일괄 처리 시작**을 클릭합니다. 일괄 처리의 상태가 **상태** 필드에 표시됩니다. 상태에 대한 자세한 내용은 [가져오기 상태&#40;Master Data Services&#41;](../../2014/master-data-services/import-statuses-master-data-services.md)를 참조하세요.  
  
         ![마스터 데이터 관리자의 준비 일괄 처리 페이지](../../2014/master-data-services/media/mds-staging-batches.png "마스터 데이터 관리자의 준비 일괄 처리 페이지")  
  
         **의** 준비 일괄 처리 간격 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]설정에 지정된 간격마다 준비 프로세스가 시작됩니다. 자세한 내용은 [시스템 설정&#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md)을 참조하세요.  
  
5.  준비 과정에서 발생한 오류를 봅니다. 자세한 내용은 [준비 프로세스 중에 발생 하는 오류 보기 &#40;Master Data Services&#41; ](view-errors-that-occur-during-staging-master-data-services.md) 하 고 [준비 프로세스 오류 &#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md).  
  
6.  비즈니스 규칙에 대해 데이터의 유효성을 검사합니다.  
  
     마스터 데이터 관리자에서 모델의 **탐색기** 기능 영역으로 이동한 다음 비즈니스 규칙을 적용하여 데이터의 유효성을 검사합니다. 자세한 내용은 [비즈니스 규칙에 대해 특정 멤버 유효성 검사&#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)를 참조하세요. 저장 프로시저를 사용하여 데이터의 유효성을 검사할 수도 있습니다. 자세한 내용은 [유효성 검사 저장 프로시저&#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md)를 참조하세요.  
  
     준비 테이블에서 데이터를 로드하는 경우 비즈니스 규칙에 대해 데이터의 유효성이 자동으로 검사되지 않습니다. 유효성 검사 및 유효성 검사가 발생하는 경우에 대한 자세한 내용은 [유효성 검사&#40;Master Data Services&#41;](../../2014/master-data-services/validation-master-data-services.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [데이터 가져오기 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
  
