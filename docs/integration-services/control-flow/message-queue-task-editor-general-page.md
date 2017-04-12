---
title: "메시지 큐 태스크 편집기(일반 페이지) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.msgqueuetask.general.f1"
helpviewer_keywords: 
  - "메시지 큐 태스크 편집기"
ms.assetid: 09368b18-37a5-4321-a173-7cfe5d42d2a2
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# 메시지 큐 태스크 편집기(일반 페이지)
  **메시지 큐 태스크 편집기** 대화 상자의 **일반 페이지** 를 사용하여 메시지 큐 태스크의 이름을 지정하고 설명하며 메시지 형식을 지정하고 태스크에서 메시지를 보내거나 받을지를 나타낼 수 있습니다.  
  
 이 태스크에 대한 자세한 내용은 [Message Queue Task](../../integration-services/control-flow/message-queue-task.md)를 참조하십시오.  
  
## 옵션  
 **이름**  
 메시지 큐 태스크에 사용할 고유 이름을 제공합니다. 이 이름은 태스크 아이콘에서 레이블로 사용됩니다.  
  
> [!NOTE]  
>  태스크 이름은 패키지 내에서 고유해야 합니다.  
  
 **Description**  
 메시지 큐 태스크에 대한 설명을 입력합니다.  
  
 **Use2000Format**  
 2000 형식의 MSMQ(메시지 큐)를 사용할지 여부를 나타냅니다. 기본값은 **False**입니다.  
  
 **MSMQConnection**  
 기존 MSMQ 연결 관리자를 선택하거나 \<**새 연결...**>을 클릭하여 새 연결 관리자를 만듭니다.  
  
 **관련 항목**: [MSMQ 연결 관리자](../../integration-services/connection-manager/msmq-connection-manager.md), [MSMQ 연결 관리자 편집기](../../integration-services/connection-manager/msmq-connection-manager-editor.md)  
  
 ** 메시지 **  
 메시지 큐 태스크에서 메시지를 보내거나 받을지를 지정합니다. **메시지 보내기**를 선택하면 대화 상자의 왼쪽 창에 보내기 페이지가 표시되고 **메시지 받기**를 선택하면 받기 페이지가 표시됩니다. 기본적으로 이 값은 **메시지 보내기**로 설정됩니다.  
  
## 관련 항목:  
 [Integration Services 오류 및 메시지 참조](../../integration-services/integration-services-error-and-message-reference.md)   
 [메시지 큐 태스크 편집기&#40;받기 페이지&#41;](../../integration-services/control-flow/message-queue-task-editor-receive-page.md)   
 [메시지 큐 태스크 편집기&#40;보내기 페이지&#41;](../../integration-services/control-flow/message-queue-task-editor-send-page.md)   
 [식 페이지](../../integration-services/expressions/expressions-page.md)  
  
  