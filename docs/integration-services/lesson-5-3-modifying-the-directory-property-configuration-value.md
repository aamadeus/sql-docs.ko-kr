---
title: '3단계: Directory 속성 구성 값 수정 | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a144bbde1537e167c82b63389be83c72f55a6346
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47742411"
---
# <a name="lesson-5-3---modifying-the-directory-property-configuration-value"></a>5-3단원 - Directory 속성 구성 값 수정
이 태스크에서는 패키지 수준 변수 `User::varFolderName`의 Value 속성에 대해 SSISTutorial.dtsConfig 파일에 저장된 구성 설정을 수정합니다. 이 변수는 Foreach 루프 컨테이너의 Directory 속성을 업데이트합니다. 수정된 값은 이전 태스크에서 만들어진 **New Sample Data** 폴더를 가리킵니다. 구성 설정을 수정하고 패키지를 실행하면 Directory 속성은 원래 패키지에서 구성된 디렉터리 값 대신 구성 파일에서 채워진 값을 사용하여 변수를 통해 업데이트됩니다.  
  
### <a name="to-modify-the-configuration-setting-of-the-directory-property"></a>Directory 속성의 구성 설정을 수정하려면  
  
1.  메모장이나 다른 텍스트 편집기에서 패키지 구성 마법사를 사용하여 이전 태스크에서 만든 SSISTutorial.dtsConfig 구성 파일을 찾아 엽니다.  
  
2.  **ConfiguredValue** 요소의 값을 변경하여 이전 태스크에서 만든 **New Sample Data** 폴더 경로와 일치시킵니다. 경로를 따옴표로 묶지 마십시오. **New Sample Data** 폴더가 드라이브의 루트 수준(예:C:\\)에 있는 경우 업데이트된 XML은 다음 샘플과 비슷합니다.  
  
    `<?xml version="1.0"?><DTSConfiguration><DTSConfigurationHeading><DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFA61D3FA}" GeneratedDate="6/10/2012 8:16:50 AM"/></DTSConfigurationHeading><Configuration ConfiguredType="Property" Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"><ConfiguredValue></ConfiguredValue></Configuration></DTSConfiguration>`  
  
    물론 사용자 파일의 제목 정보, **GeneratedBy**, **GeneratedFromPackageID**및 **GeneratedDate** 는 다릅니다. 주의해야 할 요소는 **Configuration** 입니다. 이제 **변수의** Value `User::varFolderName`속성에 C:\New Sample Data가 포함됩니다.  
  
3.  변경 내용을 저장하고 텍스트 편집기를 닫습니다.  
  
## <a name="next-task-in-lesson"></a>단원의 다음 태스크  
[4단계: 5단원 자습서 패키지 테스트](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
  
  
