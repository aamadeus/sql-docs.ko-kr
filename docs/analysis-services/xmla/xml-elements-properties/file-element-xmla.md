---
title: "파일 요소 (XMLA) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- File Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.file
- http://schemas.microsoft.com/analysisservices/2003/engine#File
- urn:schemas-microsoft-com:xml-analysis#File
helpviewer_keywords:
- File element
ms.assetid: 3dfd0e9b-746b-4ce5-8a95-610d2e573739
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e5bd3025744fa7796bc1f10111c8a12d87d5374d
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="file-element-xmla"></a>File 요소(XMLA)
  부모에서 사용할 파일을 식별 [백업](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) 또는 [복원](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) 명령이 나 부모 [위치](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <File>...</File>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|데이터 형식 및 길이|문자열|  
|기본값|없음|  
|카디널리티|1-1: 한 번만 나타나는 필수 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[백업](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [위치](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [복원](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|자식 요소|없음|  
  
## <a name="remarks"></a>주의  
 **파일** 요소는 UNC 파일 이름을 포함 하 고 부모 요소에 사용 하는 결정은 **파일** 요소입니다.  
  
 에 대 한 **백업** 명령에는 **파일** 에서 만든 백업 파일의 이름을 확인 하는 요소는 **백업** 명령입니다. 경로에 지정 된 파일 이름의 일부로 한 경로 지정 하지 않으면는 **BackupDir** 의 인스턴스에 대 한 구성 속성 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 사용 됩니다. 오류가 발생 하지 않는 한 지정 된 파일이 이미 있는 경우는 **AllowOverwrite** 부모 **백업** 명령으로 설정 되어 **True**합니다.  
  
 에 대 한 **복원** 명령에는 **파일** 하 여 복원할 백업 파일의 이름을 확인 하는 요소는 **복원** 명령입니다.  
  
 에 대 한 **위치** 요소는 **파일** 요소에 대 한 원격 백업 파일을 설명는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 원격 파티션을 포함 하는 인스턴스. 백업 및 원격 파티션을 복원 하는 방법에 대 한 자세한 내용은 참조 [Backing Up, Restoring, 및 데이터베이스 동기화 &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>관련 항목:  
 [AllowOverwrite 요소 &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)   
 [속성 &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  