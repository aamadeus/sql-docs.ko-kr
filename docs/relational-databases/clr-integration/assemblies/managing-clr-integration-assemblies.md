---
title: "CLR 통합 어셈블리 관리 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
caps.latest.revision: "56"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0e95209ed47c5e49177ae43bc9bf5ae1026ca511
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="managing-clr-integration-assemblies"></a>CLR 통합 어셈블리 관리
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]관리 되는 코드를 컴파일하여 다음 어셈블리 라는 단위로 배포 합니다. 어셈블리는 DLL이나 실행 파일(.exe)로 패키지됩니다. 실행 파일은 독립적으로 실행할 수 있는 반면 DLL은 기존 응용 프로그램 내에서 호스팅해야 합니다. 관리 되는 DLL 어셈블리를 로드 하 고 호스팅하 수 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]합니다. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 어셈블리를 프로세스에 로드하여 사용하려면 먼저 CREATE ASSEMBLY 문을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스에 어셈블리를 등록해야 합니다. ALTER ASSEMBLY 문을 사용하여 어셈블리를 최신 버전에서 업데이트하거나 DROP ASSEMBLY 문을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 제거할 수도 있습니다.  
  
 어셈블리 정보에 저장 됩니다는 **sys.assembly_files** 어셈블리가 설치 되어 있는 데이터베이스의 테이블입니다. **sys.assembly_files** 테이블에는 다음 열입니다.  
  
|열|Description|  
|------------|-----------------|  
|assembly_id|어셈블리에 대해 정의되는 식별자입니다. 해당 어셈블리와 관련한 모든 개체에 이 번호가 할당됩니다.|  
|name|개체 이름입니다.|  
|file_id|와 연결 된 첫 번째 개체와 각 개체를 식별 하는 번호는 주어진 **assembly_id** 1의 값이 지정 되 고 있습니다. 여러 개체 연결 되어 있는 경우 동일한 **assembly_id**차례로 **file_id** 값은 1 씩 증가 합니다.|  
|content|어셈블리 또는 파일의 16진수 표현입니다.|  
  
## <a name="in-this-section"></a>섹션 내용  
 [어셈블리 만들기](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 SAFE, EXTERNAL_ACCESS 및 UNSAFE CLR 어셈블리를 만드는 방법에 대해 설명합니다.  
  
 [어셈블리 변경](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 CLR 어셈블리를 업데이트하는 방법에 대해 설명합니다.  
  
 [어셈블리 삭제](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 CLR 어셈블리를 삭제하는 방법에 대해 설명합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [CLR 통합 보안](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [CLR 통합 코드 액세스 보안](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)  
  
  