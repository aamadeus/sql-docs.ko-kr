---
title: MSMQ 연결 관리자 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msmqconnectionmanager.f1
helpviewer_keywords:
- MSMQ Connection Manager Editor
ms.assetid: ef842cb4-82da-4550-85fe-9bedbc1e77c7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 42fe0f316914a83ab87deed68ff7095b66b80402
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48226553"
---
# <a name="msmq-connection-manager-editor"></a>MSMQ 연결 관리자 편집기
  **MSMQ 연결 관리자** 대화 상자를 사용하여 MSMQ(메시지 큐)의 경로를 지정할 수 있습니다.  
  
 MSMQ 연결 관리자에 대한 자세한 내용은 [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md)를 참조하십시오.  
  
> [!NOTE]  
>  MSMQ 연결 관리자는 로컬 공개 큐, 로컬 개인 큐 및 원격 공개 큐를 지원합니다. 원격 개인 큐는 지원하지 않습니다. 스크립트 태스크를 사용하는 해결 방법은 [스크립트 태스크를 사용하여 원격 개인 메시지 큐에 메시지 보내기](control-flow/script-task.md)를 참조하십시오.  
  
## <a name="options"></a>변수  
 **이름**  
 워크플로의 MSMQ 연결 관리자에 고유한 이름을 지정합니다. 제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.  
  
 **설명**  
 연결 관리자에 대한 설명을 입력합니다. 설명에 해당 연결 관리자의 용도를 정의하면 패키지를 이해하기 쉬우며 유지 관리가 간편합니다.  
  
 **경로**  
 메시지 큐의 전체 경로를 입력합니다. 경로 형식은 큐 유형에 따라 달라집니다.  
  
|큐 유형|샘플 경로|  
|----------------|-----------------|  
|공개|\<컴퓨터 이름>\\<큐 이름\>|  
|Private|\<컴퓨터 이름>\Private$\\<큐 이름\>|  
  
 "."를 사용하여 로컬 컴퓨터를 나타낼 수 있습니다.  
  
 **테스트**  
 MSMQ 연결 관리자를 구성했으면 **테스트**를 클릭하여 연결이 실행 가능한지 확인합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
