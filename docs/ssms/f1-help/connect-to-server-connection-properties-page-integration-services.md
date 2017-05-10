---
title: "SSIS 서버에 연결(연결 속성) | Microsoft 문서"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssiseditserverregistration.connectionproperties.f1
- sql13.swb.connecttodts.connectionproperties.f1
ms.assetid: c2513dab-8415-4e0c-9475-6d4ab97fea7c
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 734f14076b65d0ea7e4c26c95c463a3554828587
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-connection-properties-page-integration-services"></a>서버에 연결(연결 속성 페이지) Integration Services
[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)]에 연결하거나 [!INCLUDE[ssIS](../../includes/ssis_md.md)]를 **등록된 서버**에 등록할 때 이 탭을 사용하여 옵션을 확인하거나 지정할 수 있습니다. **연결** 및 **옵션** 은 연결 시에만 이 대화 상자에 나타납니다. **테스트** 및 **저장** 은 [!INCLUDE[ssIS](../../includes/ssis_md.md)]등록 시에만 이 대화 상자에 나타납니다.  
  
## <a name="options"></a>옵션  
**포트 번호**  
[!INCLUDE[ssIS](../../includes/ssis_md.md)]에서 사용하는 포트 번호를 입력합니다.  
  
**연결 제한 시간**  
제한 시간이 초과하기 전까지 연결을 대기하는 시간(초)을 입력합니다. 기본값은 15초입니다.  
  
**실행 제한 시간**  
서버에서 태스크가 실행 완료되기까지 대기하는 시간(초)을 입력합니다. 기본값은 0초이며 시간 제한 없음을 의미합니다.  
  
**모두 다시 설정**  
수동으로 입력한 모든 연결 속성 값을 기본값으로 되돌립니다.  
  
**연결**  
목록에 있는 값을 사용하여 연결을 시도합니다.  
  
**옵션**  
대화 상자를 변경하고 암호 저장과 같은 추가 서버 연결 옵션을 숨기려면 클릭합니다.  
  
**테스트**  
[!INCLUDE[ssIS](../../includes/ssis_md.md)] 을 **등록된 서버**에 등록하는 경우 연결을 테스트하려면 클릭합니다.  
  
**저장**  
**등록된 서버**에 설정을 저장합니다.  
  
