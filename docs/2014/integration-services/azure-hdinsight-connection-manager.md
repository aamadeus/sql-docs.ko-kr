---
title: Azure HDInsight 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.DTS.DESIGNER.AFPHDICM.F1
- SQL11.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 850a978d-5dba-45b6-a10e-306aafbc353d
caps.latest.revision: 2
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.openlocfilehash: 3d9486108e7f16870d2bf4e22f05b8a0a288b664
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36092033"
---
# <a name="azure-hdinsight-connection-manager"></a>Azure HDInsight 연결 관리자
**Azure HDInsight 연결 관리자**를 통해 SSIS 패키지는 Azure HDInsight 클러스터에 연결할 수 있습니다.

**Azure HDInsight 연결 관리자**를 만들고 구성하려면 다음 단계를 수행합니다.

1. **SSIS 연결 관리자 추가** 대화 상자에서 **AzureHDInsight**를 선택하고 **추가**를 클릭합니다.
2. **Azure HDInsight 연결 관리자 편집기** 대화 상자에서 연결할 HDInsight 클러스터에 대한 **클러스터 DNS 이름**(프로토콜 접두사 없이), **사용자 이름** 및 **암호**를 지정합니다.
3. **확인** 을 클릭하여 대화 상자를 닫습니다.
4. 작성한 연결 관리자의 속성은 **속성** 창에서 확인할 수 있습니다.