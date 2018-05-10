---
title: RightsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RightsEnum
helpviewer_keywords:
- RightsEnum enumeration [ADOX]
ms.assetid: 55ee67c7-a583-42aa-849a-78264b4cb614
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5548cb17169d73cca6a66b08ac487e62557ed22d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="rightsenum"></a>RightsEnum
권한이 나 그룹 또는 사용자에 대 한 사용 권한이 개체에 지정합니다.  
  
|상수|Value|Description|  
|--------------|-----------|-----------------|  
|**adRightCreate**|16384 (&AMP; H4000)|사용자 또는 그룹에는이 형식의 새 개체를 만들 수 있는 권한이 있습니다.|  
|**adRightDelete**|65536 (&AMP; H10000)|사용자 또는 그룹에는 개체에서 데이터를 삭제할 수 있는 권한이 있습니다. 와 같은 개체에 대 한 **테이블**, 사용자가을 레코드의 데이터 값을 삭제할 수 있습니다.|  
|**adRightDrop**|256 (&AMP; H100)|사용자 또는 그룹에는 카탈로그에서 개체를 제거 하려면 권한을 가집니다. 예를 들어 **테이블** DROP TABLE SQL 명령으로 삭제할 수 있습니다.|  
|**adRightExclusive**|512 (&AMP; H200)|사용자 또는 그룹에 개체를 단독으로 액세스할 수 있는 권한이 있습니다.|  
|**adRightExecute**|536870912 (&H20000000)|사용자 또는 그룹에 개체를 실행할 수 있는 권한이 있습니다.|  
|**adRightFull**|268435456 (&AMP; H10000000)|에 모든 권한이 개체에 사용자 또는 그룹입니다.|  
|**adRightInsert**|32768 (&AMP; H8000)|사용자 또는 그룹에 개체를 삽입할 수 있는 권한이 있습니다. 와 같은 개체에 대 한 **테이블**, 사용자에 게 권한이 테이블에 데이터를 삽입 합니다.|  
|**adRightMaximumAllowed**|33554432 (&AMP; H 2000000)|사용자 또는 그룹에는 공급자에서 허용 되는 권한의 최대 수입니다. 특정 사용 권한은 공급자에 따라 다릅니다.|  
|**adRightNone**|0|사용자 또는 그룹에는 개체에 대 한 권한이 없습니다.|  
|**adRightRead**|-2147483648 (&H80000000)|사용자 또는 그룹에 개체를 읽을 수 있는 권한이 있습니다. 와 같은 개체에 대 한 [테이블](../../../ado/reference/adox-api/table-object-adox.md), 사용자는 테이블의 데이터를 읽을 수 있는 권한이 있습니다.|  
|**adRightReadDesign**|1024 (&AMP; H400)|사용자 또는 그룹에는 개체에 대 한 디자인을 읽을 수 있는 권한이 있습니다.|  
|**adRightReadPermissions**|131072 (&AMP; H20000)|사용자 또는 그룹 볼 수 있지만 변경 하지는 카탈로그에 있는 개체에 대 한 특정 권한이 됩니다.|  
|**adRightReference**|8192 (&AMP; H2000)|사용자 또는 그룹에 개체를 참조할 수 있는 권한이 있습니다.|  
|**adRightUpdate**|1073741824 (&AMP; H40000000)|사용자 또는 그룹에 개체를 업데이트할 수 있는 권한이 있습니다. 와 같은 개체에 대 한 **테이블**, 사용자가 테이블의 데이터를 업데이트할 수 있습니다.|  
|**adRightWithGrant**|4096 (&H1000)|사용자 또는 그룹 개체에 사용 권한을 부여할 권한이 있습니다.|  
|**adRightWriteDesign**|2048 (&AMP; H800)|사용자 또는 그룹에는 개체에 대 한 디자인을 수정할 수 있는 권한이 있습니다.|  
|**adRightWriteOwner**|524288 (&AMP; H80000)|사용자 또는 그룹에 개체의 소유자를 수정할 수 있는 권한이 있습니다.|  
|**adRightWritePermissions**|262144 (&AMP; H40000)|사용자 또는 그룹 카탈로그에 있는 개체에 대 한 특정 사용 권한을 수정할 수 있습니다.|  
  
## <a name="applies-to"></a>적용 대상  
  
|||  
|-|-|  
|[GetPermissions 메서드(ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|[SetPermissions 메서드(ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|