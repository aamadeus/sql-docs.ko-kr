---
title: "어셈블리 변경 | Microsoft Docs"
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
helpviewer_keywords:
- assemblies [CLR integration], modifying
- permissions [CLR integration]
- altering assemblies
- ALTER ASSEMBLY statement
ms.assetid: 9e765fbd-f339-473c-8537-22f478e79696
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f279c3f1e1315ea44cdb75918b471c8fdd22ee01
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="altering-an-assembly"></a>어셈블리 변경
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]에 등록 된 어셈블리 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ALTER ASSEMBLY 문을 사용 하 여 최신 버전에서 업데이트할 수 있습니다. 어셈블리를 업데이트하려면 ALTER ASSEMBLY 문을 다음 구문과 함께 사용합니다.  
  
```  
ALTER ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
```  
  
 ALTER ASSEMBLY는 해당 어셈블리를 사용하는 현재 실행 중인 프로세스를 중단하지 않습니다. 이러한 프로세스는 변경되지 않은 어셈블리를 사용하여 계속해서 실행됩니다. 트리거, 저장 프로시저, 집계 함수 및 CLR(공용 언어 런타임) 함수의 서명을 변경하는 데는 ALTER ASSEMBLY를 사용할 수 없습니다. 새 공용 메서드를 어셈블리에 추가하고 전용 메서드를 수정할 수 있으며 서명이나 특성을 변경하지 않는 범위에서 공용 메서드를 수정할 수도 있습니다. 데이터 멤버 또는 기본 클래스를 비롯하여 기본적으로 직렬화된 사용자 정의 형식에 포함된 필드는 ALTER ASSEMBLY를 사용하여 변경할 수 없습니다. 다른 모든 변경은 지원되지 않습니다. 자세한 내용은 참조 [ALTER assembly&#40; Transact SQL &#41; ](../../../t-sql/statements/alter-assembly-transact-sql.md).  
  
## <a name="changing-the-permission-set-of-an-assembly"></a>어셈블리의 권한 집합 변경  
 ALTER ASSEMBLY 문을 사용하여 어셈블리의 권한 집합도 변경할 수 있습니다. 다음 문은 SQLCLRTest 어셈블리의 권한 집합을 변경 **EXTERNAL_ACCESS**합니다.  
  
```  
ALTER ASSEMBLY SQLCLRTest  
WITH PERMISSION_SET = EXTERNAL_ACCESS   
```  
  
 어셈블리의 권한 집합에서 변경 되는 경우 **안전** 를 **EXTERNAL_ACCESS** 또는 **UNSAFE**, 비대칭 키 및 해당 로그인을  **EXTERNAL ACCESS ASSEMBLY** 권한 또는 **UNSAFE ASSEMBLY** 어셈블리에 대 한 권한을 먼저 만들어야 합니다. 자세한 내용은 [Creating an Assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)을 참조하세요.  
  
## <a name="adding-the-source-code-of-an-assembly"></a>어셈블리의 원본 코드 추가  
 ALTER ASSEMBLY 구문의 ADD FILE 절은 CREATE ASSEMBLY에 없습니다. 이 절을 사용하여 원본 코드나 어셈블리와 연결된 다른 파일을 추가할 수 있습니다. 이렇게 하면 파일이 원래 위치에서 복사되어 데이터베이스의 시스템 테이블에 저장됩니다. 따라서 UDT의 현재 버전을 다시 만들거나 문서화해야 할 경우 간편하게 원본 코드나 기타 파일을 사용할 수 있습니다.  
  
 다음 문은 Point UDT의 Point.cs 클래스 원본 코드를 추가합니다. 이 문은 Point.cs 파일에 있는 텍스트를 복사하여 "PointSource"라는 이름으로 데이터베이스에 저장합니다.  
  
 `ALTER ASSEMBLY Point`  
  
 `ADD FILE FROM 'C:\Projects\Point\Point.cs' AS PointSource`  
  
## <a name="see-also"></a>관련 항목:  
 [CLR 통합 어셈블리 관리](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [어셈블리 만들기](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [어셈블리 삭제](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [ALTER ASSEMBLY&#40;Transact-SQL&#41;](../../../t-sql/statements/alter-assembly-transact-sql.md)  
  
  