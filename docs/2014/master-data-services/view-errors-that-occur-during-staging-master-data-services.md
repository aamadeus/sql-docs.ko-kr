---
title: 준비 프로세스 (Master Data Services) 중에 발생 하는 오류 보기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], viewing errors
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 8f8d6563514aec7c4e75893facb0caa8850798c9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48204093"
---
# <a name="view-errors-that-occur-during-the-staging-process-master-data-services"></a>준비 프로세스 동안 발생하는 오류 보기(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 준비 프로세스 동안 발생하는 오류를 볼 수 있습니다. [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에는 오류를 표시하는 두 개의 뷰가 있습니다.  
  
-   stg.viw_name_MemberErrorDetails 뷰는 리프 또는 통합 멤버 업데이트를 표시합니다.  
  
-   stg.viw_name_RelationshipErrorDetails 뷰는 계층 관계 업데이트를 표시합니다.  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 절차를 수행하려면  
  
-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에서 stg.viw_name_MemberErrorDetails 또는 stg.viw_name_RelationshipErrorDetails 뷰에 대한 SELECT 권한이 있어야 합니다.  
  
-   모델 관리자여야 합니다. 자세한 내용은 [관리자&#40;Master Data Services&#41;](administrators-master-data-services.md)를 참조하세요.  
  
### <a name="to-view-staging-errors"></a>준비 오류를 보려면  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 을 열고 [!INCLUDE[ssDE](../includes/ssde-md.md)] 데이터베이스의 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 인스턴스에 연결합니다.  
  
2.  새 쿼리를 엽니다.  
  
3.  다음 텍스트를 입력하여 준비 테이블의 이름을 예를 들어 viw_Product_MemberErrorDetails 등으로 바꿉니다.  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  쿼리를 실행합니다. 오류 세부 정보가 **ErrorDescription** 필드에 표시됩니다.  
  
## <a name="next-steps"></a>다음 단계  
 오류 메시지에 대한 자세한 내용은 [준비 프로세스 오류&#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [데이터 가져오기 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [준비 프로세스 문제 해결(Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  
