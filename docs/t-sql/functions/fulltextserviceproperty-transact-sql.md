---
title: FULLTEXTSERVICEPROPERTY (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FULLTEXTSERVICEPROPERTY_TSQL
- FULLTEXTSERVICEPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], properties
- FULLTEXTSERVICEPROPERTY function
- services [SQL Server], full-text search properties
- test
ms.assetid: b7dcacb0-af83-4807-9d1e-49148b56b59c
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b40c8cc7070c3cd459cf6fff99854942544f7459
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="fulltextserviceproperty-transact-sql"></a>FULLTEXTSERVICEPROPERT(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  전체 텍스트 엔진의 속성과 관련된 정보를 반환합니다. 이러한 속성을 설정 하거나 사용 하 여 검색할 수 있습니다 **sp_fulltext_service**합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
FULLTEXTSERVICEPROPERTY ('property')  
```  
  
## <a name="arguments"></a>인수  
 *속성*  
 전체 텍스트 서비스 수준 속성의 이름이 포함된 식입니다. 다음은 속성과 반환되는 정보에 대한 설명입니다.  
  
> [!NOTE]  
>  다음 속성의 후속 릴리스에서 제거 됩니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **ConnectTimeout**, **DataTimeout**, 및 **ResourceUsage**합니다. 향후 개발 작업에서는 이 속성을 사용하지 않도록 하고 현재 이 속성을 사용하는 응용 프로그램은 수정하십시오.  
  
|속성|값|  
|--------------|-----------|  
|**ResourceUsage**|0을 반환합니다. 이전 버전과의 호환성을 위해서만 지원됩니다.|  
|**ConnectTimeout**|0을 반환합니다. 이전 버전과의 호환성을 위해서만 지원됩니다.|  
|**IsFulltextInstalled**|전체 텍스트 구성 요소가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 현재 인스턴스와 함께 설치되었습니다.<br /><br /> 0 = 전체 텍스트가 설치되지 않음<br /><br /> 1 = 전체 텍스트가 설치됨<br /><br /> NULL = 잘못된 입력 또는 오류|  
|**DataTimeout**|0을 반환합니다. 이전 버전과의 호환성을 위해서만 지원됩니다.|  
|**LoadOSResources**|운영 체제 단어 분리기 및 필터가 이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 함께 등록되고 사용되는지 여부를 나타냅니다. 기본적으로 이 속성은 OS(운영 체제) 업데이트 시 실수로 동작이 변경되는 것을 방지하기 위해 비활성화되어 있습니다. OS 리소스를 사용하도록 설정하면 설치된 인스턴스별 리소스가 없는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 인덱싱 서비스에 등록된 언어 및 문서 유형에 대한 리소스에 액세스할 수 있습니다. OS 리소스 로드를 사용 하도록 설정 하면 운영 체제 리소스가 트러스트 된 서명 된 이진 파일; 인지 확인 그렇지 않으면 로드 된 경우 수 없습니다 **VerifySignature** 1로 설정 됩니다.<br /><br /> 0 = 이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 연관된 필터와 단어 분리기만 사용합니다.<br /><br /> 1 = OS 필터와 단어 분리기를 로드합니다.|  
|**VerifySignature**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Search 서비스가 서명된 이진 파일만 로드할지 여부를 지정합니다. 기본적으로 트러스트된 서명된 이진 파일만 로드됩니다.<br /><br /> 0 = 이진 파일의 서명 여부를 확인하지 않습니다.<br /><br /> 1 = 트러스트된 서명된 바이너리만 로드하는지 확인합니다.|  
  
## <a name="return-types"></a>반환 형식  
 **int**  
  
## <a name="examples"></a>예  
 다음 예에서는 서명된 이진 파일만 로드할지 여부를 확인하고 반환 값은 이 확인이 발생하지 않음을 나타냅니다.  
  
```  
SELECT fulltextserviceproperty('VerifySignature');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------   
0  
```  
  
 서명 확인을 다시 기본값인 1로 설정하려면 다음 `sp_fulltext_service` 문을 사용할 수 있습니다.  
  
```  
EXEC sp_fulltext_service @action='verify_signature', @value=1;  
GO  
```  
  
## <a name="see-also"></a>관련 항목:  
 [FULLTEXTCATALOGPROPERTY &#40; Transact SQL &#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [메타 데이터 함수 &#40; Transact SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_fulltext_service&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)  
  
  