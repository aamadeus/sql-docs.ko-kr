---
title: 네임 스페이스 | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- namespaces in ADO
ms.assetid: efff5569-db52-451d-a039-2e74870534da
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5553072dcea3ed64ef8454019892ac5790c7a142
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600113"
---
# <a name="namespaces"></a>네임스페이스
ADO의 XML 지 속성 형식으로 다음 네 가지 네임 스페이스를 사용합니다.  
  
## <a name="remarks"></a>Remarks  
 ADO의 XML 지 속성 형식으로 다음 네 가지 네임 스페이스를 사용합니다.  
  
|접두사|설명|  
|------------|-----------------|  
|s|현재 레코드 집합의 스키마를 정의 하는 특성 및 요소를 포함 하는 "XML 데이터" 네임 스페이스를 가리킵니다.|  
|dt|데이터 형식 정의 사양을 나타냅니다.|  
|rs|요소를 포함 하는 네임 스페이스 및 ADO 레코드 집합 속성에 특정 특성 및 특성을 가리킵니다.|  
|z|현재 행 집합의 스키마를 가리킵니다.|  
  
 클라이언트 사양에 정의 된 대로 이러한 네임 스페이스에는 고유한 태그 추가 하지 해야 합니다. 예를 들어, 클라이언트 정의 안 네임 스페이스 "urn: 스키마-microsoft-com:rowset" 및 "rs: MyOwnTag."와 같은 무엇 인가 작성할 네임 스페이스에 대 한 자세한 내용은 참조는 [XML 권장 사항의 W3C 네임 스페이스](https://www.w3.org/TR/REC-xml-names/)합니다.  
  
> [!IMPORTANT]
>  스키마 태그에 대 한 ID에는 "RowsetSchema," 이어야 하며 현재 행 집합의 스키마를 참조 하는 데 네임 스페이스 "#RowsetSchema."를 가리켜야 합니다.  
  
 네임 스페이스의 접두사, 콜론 및 등호 기호 사이의 부분-는 임의로 지정 됩니다.  
  
```  
xmlns:rs="urn:schemas-microsoft-com:rowset"  
```  
  
 사용자는이 XML 문서 전체에서 일관 되 게는이 이름으로 모든 이름을 정의할 수 있습니다. 항상 "s", "rs", "dt" ADO에 작성 되며 "z" 하지만 이러한 접두사 이름은 없습니다 로드 구성 요소에 하드 코딩 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [XML 형식으로 레코드 유지](../../../ado/guide/data/persisting-records-in-xml-format.md)
