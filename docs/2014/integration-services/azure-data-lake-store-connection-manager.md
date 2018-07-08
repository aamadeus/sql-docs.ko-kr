---
title: Azure Data Lake Store 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSCM.F1
- SQL11.DTS.DESIGNER.AFPADLSCM.F1
ms.assetid: 7f1323f9-9dc3-4378-9c70-bbc65bfeabfd
caps.latest.revision: 5
author: yualan
ms.author: yual
manager: jhubbard
ms.openlocfilehash: 00854154db97d5ee2cbc8d6f301f4d043bc26167
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36093814"
---
# <a name="azure-data-lake-store-connection-manager"></a>Azure Data Lake Store 연결 관리자
  **Azure Data Lake Store 연결 관리자** 를 사용하면 두 가지 인증 유형 즉, Azure AD 사용자 ID와 Azure AD 서비스 ID를 통해 SSIS 패키지를 Azure Data Lake Store 서비스에 연결할 수 있습니다.  

## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Azure Data Lake Store 연결 관리자 구성 
  
1.  **SSIS 연결 관리자 추가** 대화 상자에서 **AzureDataLake**를 선택하고 **추가**를 클릭합니다.   
  
2.  Azure Data Lake Store 연결 관리자 편집기 대화 상자에서 **ADLS 호스트** 필드에 Azure Data Lake Store 호스트 URL을 입력합니다. 예를 들어: https://test.azuredatalakestore.net 또는 test.azuredatalakestore.net 합니다.
  
3.  해당 인증 유형을 선택하여 Azure Data Lake Store 데이터에 액세스합니다.

    1.  **Azure AD 사용자 ID** 인증 옵션을 선택한 경우 다음을 수행합니다.

        1. **사용자 이름** 및 **암호** 필드에 값을 지정합니다. 
    
        2. **연결 테스트** 단추를 클릭하여 연결을 테스트합니다. 이전에 사용자 본인과 테넌트 관리자가 Azure Data Lake Store 데이터에 SSIS가 액세스하는 것에 동의하지 않은 경우 팝아웃 대화 상자에서 **동의** 단추를 클릭하여 SSIS가 Azure Data Lake Store 데이터에 액세스하는 것에 동의해야 합니다. 이 동의 환경에 대한 자세한 내용은 [Azure Active Directory와 응용 프로그램 통합](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-integrating-applications#updating-an-application)을 참조하세요.
    
        >   [!NOTE] 
        >   Azure AD 사용자 ID 인증 옵션에서는 다단계 인증과 Microsoft 계정이 지원되지 않습니다.
    
    2.  **Azure AD 서비스 ID** 인증 옵션을 선택한 경우 다음을 수행합니다.
        1. Azure Data Lake 리소스에 액세스할 수 있는 AAD 응용 프로그램 및 서비스 사용자를 만듭니다.
    
        2. 이 AAD 응용 프로그램에 Azure Data Lake 리소스에 액세스할 수 있는 해당 권한을 할당합니다. 이 인증 옵션에 대한 자세한 내용은 [Use portal to create Active Directory application and service principal that can access resources](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal)(리소스에 액세스할 수 있는 Active Directory 응용 프로그램 및 서비스 사용자를 포털에서 만들기)를 참조하세요.
    
        3. **클라이언트 ID**, **보안 키** 및 **테넌트 이름** 필드에 값을 지정합니다.
    
        4. **연결 테스트** 단추를 클릭하여 연결을 테스트합니다.  
  
4.  **확인** 을 클릭하여 대화 상자를 닫습니다.  
  
    작성한 연결 관리자의 속성은 **속성** 창에서 확인할 수 있습니다.  
  
  