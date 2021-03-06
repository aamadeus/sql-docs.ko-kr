---
title: SAP BW 대상 편집기(연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 04ae38f8-5287-45a3-826a-8aac5dd15a91
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 46572a9fac9e3d1749c65acf9370718fbc8b3dd0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125513"
---
# <a name="sap-bw-destination-editor-connection-manager-page"></a>SAP BW 대상 편집기(연결 관리자 페이지)
  **SAP BW 대상 편집기** 의 **연결 관리자** 페이지를 사용하여 SAP BW 대상이 사용할 SAP BW 연결 관리자를 선택할 수 있습니다. 이 페이지에서는 SAP Netweaver BW 시스템으로 데이터를 로드하기 위한 매개 변수도 선택합니다.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW의 SAP BW 대상에 대한 자세한 내용은 [SAP BW 대상](sap-bw-destination.md)을 참조하세요.  
  
> [!IMPORTANT]  
>  SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다. SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.  
  
 **연결 관리자 페이지를 열려면**  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 대상이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.  
  
2.  **데이터 흐름** 탭에서 SAP BW 대상을 두 번 클릭합니다.  
  
3.  **SAP BW 대상 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.  
  
## <a name="options"></a>변수  
  
> [!NOTE]  
>  대상을 구성하는 데 필요한 값 중 모르는 것이 있으면 SAP 관리자에게 문의하십시오.  
  
 **SAP BW 연결 관리자**  
 목록에서 기존 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.  
  
 **새로 만들기**  
 **SAP BW 연결 관리자** 대화 상자를 사용하여 새 연결 관리자를 만듭니다.  
  
 **테스트 로드**  
 사용자가 선택한 설정을 사용하고 0 행을 로드하는 로드 프로세스의 테스트를 수행합니다.  
  
### <a name="infopackageinfosource-options"></a>InfoPackage/InfoSource 옵션  
 이러한 값을 미리 알고 입력할 필요는 없습니다. **조회** 단추를 사용하여 적절한 InfoPackage를 찾고 선택합니다. InfoPackage를 선택하면 이러한 옵션의 적절한 값이 입력됩니다.  
  
 **InfoPackage**  
 InfoPackage의 이름을 입력합니다.  
  
 **InfoSource**  
 InfoSource의 이름을 입력합니다.  
  
 **형식**  
 InfoSource의 유형을 식별하는 단일 문자를 입력합니다. 다음 표에서는 허용 가능한 단일 문자 값을 나열합니다.  
  
|Value|Description|  
|-----------|-----------------|  
|**D**|트랜잭션 데이터|  
|**M**|마스터 데이터|  
|**T**|텍스트|  
|**H**|계층 데이터|  
  
 **논리 시스템**  
 InfoPackage와 연결된 논리 시스템의 이름을 입력합니다.  
  
 **조회**  
 **InfoPackage 조회** 대화 상자를 사용하여 InfoPackage를 조회합니다. 이 대화 상자에 대한 자세한 내용은 [Look Up InfoPackage](look-up-infopackage.md)을 참조하십시오.  
  
### <a name="rfc-destination-options"></a>RFC 대상 옵션  
 이러한 값을 미리 알고 입력할 필요는 없습니다. **조회** 단추를 사용하여 적절한 RFC 대상을 찾고 선택합니다. RFC 대상을 선택하면 이러한 옵션의 적절한 값이 입력됩니다.  
  
 **게이트웨이 호스트**  
 게이트웨이 호스트의 서버 이름 또는 IP 주소를 입력합니다. 일반적으로 이름 또는 IP 주소는 SAP 응용 프로그램 서버와 동일합니다.  
  
 **게이트웨이 서비스**  
 게이트웨이 서비스의 이름 형식으로 입력 `sapgwNN`여기서 `NN` 은 시스템 번호입니다.  
  
 **프로그램 ID**  
 RFC 대상과 연결된 프로그램 ID를 입력합니다.  
  
 **조회**  
 **RFC 대상 조회** 대화 상자를 사용하여 RFC 대상을 조회합니다. 이 대화 상자에 대한 자세한 내용은 [Look Up RFC Destination](look-up-rfc-destination.md)을 참조하십시오.  
  
### <a name="create-sap-bw-objects-options"></a>SAP BW 개체 만들기 옵션  
 **개체 유형 선택**  
 만들려는 SAP Netweaver BW 개체의 유형을 선택합니다. 다음 유형 중 하나를 선택할 수 있습니다.  
  
-   InfoObject  
  
-   InfoCube  
  
-   InfoSource  
  
-   InfoPackage  
  
 **만들기**  
 선택된 유형의 SAP Netweaver BW 개체를 만듭니다.  
  
|개체 유형|결과|  
|-----------------|------------|  
|**InfoObject**|**새 InfoObject 만들기** 대화 상자를 사용하여 새 InfoObject를 만듭니다. 이 대화 상자에 대한 자세한 내용은 [Create New InfoObject](create-new-infoobject.md)을 참조하십시오.|  
|**InfoCube**|**트랜잭션 데이터용 InfoCube 만들기** 대화 상자를 사용하여 새 InfoCube를 만듭니다. 이 대화 상자에 대한 자세한 내용은 [Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md)을 참조하십시오.|  
|**InfoSource**|**InfoSource 만들기** 대화 상자를 사용한 다음 **트랜잭션 데이터용 InfoSource 만들기** 또는 **마스터 데이터용 InfoSource 만들기** 대화 상자를 사용하여 새 InfoSource를 만듭니다. 이러한 대화 상자에 대한 자세한 내용은 [Create InfoSource](create-infosource.md), [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) 및 [Create InfoSource for Master Data](create-infosource-for-master-data.md)를 참조하십시오.|  
|**InfoPackage**|**InfoPackage 만들기** 대화 상자를 사용하여 새 InfoPackage를 만듭니다. 이 대화 상자에 대한 자세한 내용은 [Create InfoPackage](create-infopackage.md)을 참조하십시오.|  
  
## <a name="see-also"></a>관련 항목  
 [SAP BW 대상 편집기 &#40;매핑 페이지&#41;](sap-bw-destination-editor-mappings-page.md)   
 [SAP BW 대상 편집기&#40;오류 출력 페이지&#41;](sap-bw-destination-editor-error-output-page.md)   
 [SAP BW 대상 편집기&#40;고급 페이지&#41;](sap-bw-destination-editor-advanced-page.md)   
 [Microsoft Connector 1.1 for SAP BW F1 도움말](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
