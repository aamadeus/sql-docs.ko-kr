---
title: 스냅숏 파일 압축(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], compressed
- snapshot replication [SQL Server], compressed snapshots
ms.assetid: 174ade3e-74a1-4e67-a6da-b874be3ff50f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5b65faaa8ad09e91b3fe9a2ebef72696cbee3c1e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47852521"
---
# <a name="compress-snapshot-files-sql-server-management-studio"></a>스냅숏 파일 압축(SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  파일이 **게시 속성 - \<Publication>** 대화 상자의 **스냅숏** 페이지에서 압축되도록 지정합니다. 이 대화 상자에 액세스하는 방법은 [게시 속성 보기 및 수정](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)을 참조하세요.  
  
### <a name="to-compress-snapshot-files"></a>스냅숏 파일을 압축하려면  
  
1.  **게시 속성 - \<게시>** 대화 상자의 **스냅숏** 페이지에서 다음을 수행합니다.  
  
    1.  **다음 폴더에 파일 보관**을 선택한 다음 **찾아보기** 를 클릭하여 디렉터리로 이동하거나 스냅숏 파일을 저장할 디렉터리 경로를 입력합니다.  
  
        > [!NOTE]  
        >  스냅숏 에이전트는 지정한 디렉터리에 대해 쓰기 권한이 있어야 하며 배포 에이전트 또는 병합 에이전트는 읽기 권한이 있어야 합니다. 끌어오기 구독을 사용하는 경우 공유 디렉터리를 \\\computername\snapshot과 같이 UNC(범용 명명 규칙) 경로로 지정해야 합니다. 자세한 내용은 [스냅숏 폴더 보안 설정](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)을 참조하세요.  
  
    2.  두 위치 모두에 스냅숏 파일을 쓸 필요가 없으면 **기본 폴더에 파일 보관** 의 선택을 취소합니다.  
  
        > [!NOTE]  
        >  이 확인란을 선택하면 기본 폴더에 저장된 파일은 압축되지 않습니다. 압축 파일은 이전 단계에서 지정한 대체 위치에만 저장할 수 있습니다.  
  
2.  **이 폴더에 있는 스냅숏 파일 압축**을 선택합니다.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>참고 항목  
 [스냅숏 속성 구성&#40;복제 Transact-SQL 프로그래밍&#41;](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [게시 및 아티클 속성 변경](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [압축 스냅숏](../../../relational-databases/replication/compressed-snapshots.md)   
 [스냅숏으로 구독 초기화](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
