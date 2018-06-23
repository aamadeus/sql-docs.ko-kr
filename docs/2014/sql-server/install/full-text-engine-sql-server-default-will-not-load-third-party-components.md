---
title: SQL Server 용 Microsoft 전체 텍스트 엔진은 기본적으로 서명 되지 않은 타사 구성 요소를 로드 하지 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c66544657e97ed8efcf2ed0dc46dfe21702787a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36093008"
---
# <a name="the-microsoft-full-text-engine-for-sql-server-will-not-load-unsigned-third-party-components-by-default"></a>SQL Server용 Microsoft 전체 텍스트 엔진은 기본적으로 서명되지 않은 타사 구성 요소를 로드하지 않습니다.
  기본적으로 [!INCLUDE[msCoName](../../includes/msconame-md.md)]용 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 전체 텍스트 엔진은 [!INCLUDE[msCoName](../../includes/msconame-md.md)]가 서명하지 않은 구성 요소를 로드하지 않습니다.  
  
## <a name="component"></a>구성 요소  
 전체 텍스트 검색  
  
## <a name="description"></a>Description  
 업그레이드 후에는 [!INCLUDE[msCoName](../../includes/msconame-md.md)]용 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 전체 텍스트 엔진이 현재 서버에 설치된 PDF 필터 등의 타사 필터를 기본적으로 로드하지 않습니다.  
  
## <a name="corrective-action"></a>수정 동작  
 타사 필터를 로드 하려면 설정 해야 *load_os_resource* 해제 *verify_signature* 해당 인스턴스에서 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [업그레이드 관리자 작업](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  