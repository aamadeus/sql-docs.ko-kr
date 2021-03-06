---
title: 데이터 원본 개체 (Analysis Services)에 대 한 권한을 부여 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9d550b376a644592a228708decb59ca436756ddc
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34024190"
---
# <a name="grant-permissions-on-a-data-source-object-analysis-services"></a>데이터 원본 개체에 대한 권한 부여(Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  일반적으로 대부분의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 사용자는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트의 기반이 되는 데이터 원본에 액세스할 필요가 없습니다. 사용자는 일반적으로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 내의 데이터를 쿼리하기만 합니다. 그러나 마이닝 모델 기반의 예측을 수행하는 등의 데이터 마이닝 컨텍스트에서는 사용자가 마이닝 모델에서 얻은 데이터와 사용자 제공 데이터를 조인해야 합니다. 사용자 제공 데이터가 포함된 데이터 원본에 연결하기 위해 사용자는 [OPENQUERY &#40;DMX&#41;](../../dmx/source-data-query-openquery.md) 또는 [OPENROWSET &#40;DMX&#41;](../../dmx/source-data-query-openrowset.md) 절이 포함된 DMX(Data Mining Extensions) 쿼리를 사용합니다.  
  
 데이터 원본에 연결하는 DMX 쿼리를 실행하려면 사용자가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 내의 데이터 원본 개체에 액세스할 수 있어야 합니다. 기본적으로 서버 관리자 또는 데이터베이스 관리자가 데이터 원본 개체에 액세스할 수 있습니다. 즉, 관리자가 권한을 부여하지 않으면 사용자는 데이터 원본 개체에 액세스할 수 없습니다.  
  
> [!IMPORTANT]  
>  보안상의 이유로 OPENROWSET 절에서 열린 연결 문자열을 사용하여 DMX 쿼리를 제출하는 기능은 해제되어 있습니다.  
  
## <a name="set-read-permissions-to-a-data-source"></a>데이터 원본에 대한 읽기 권한 설정  
 데이터베이스 역할에는 데이터 원본 개체에 대한 액세스 권한 또는 읽기 권한이 부여되지 않을 수 있습니다.  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에 연결하고 개체 탐색기에서 해당 데이터베이스에 대한 **역할** 을 확장한 다음 데이터베이스 역할을 클릭하거나 새 데이터베이스 역할을 만듭니다.  
  
2.  **데이터 원본 액세스** 창의 **데이터 원본** 목록에서 데이터 원본 개체를 찾은 다음 데이터 원본에 대한 **액세스 권한** 목록에서 **읽기** 를 선택합니다. 이 옵션을 사용할 수 없는 경우 **일반** 창을 확인하여 모든 권한을 선택했는지 확인합니다. 모든 권한은 이미 권한을 제공하므로, 데이터 원본에 대한 권한을 재정의할 수 없습니다.  
  
## <a name="working-with-the-connection-string-used-by-a-data-source-object"></a>데이터 원본 개체에서 사용하는 연결 문자열 작업  
 데이터 원본 개체에는 기본 데이터 원본에 연결하는 데 사용되는 연결 문자열이 포함되어 있습니다. 이 연결 문자열을 사용하여 다음 중 하나를 지정할 수 있습니다.  
  
-   **사용자 이름 및 암호 지정**  
  
     데이터 원본 개체에서 사용하는 연결 문자열이 사용자 이름과 암호를 지정하면 각각 다른 사용자 계정으로 여러 데이터 원본 개체를 만들 수 있습니다. 여러 데이터 원본 개체를 만들면 사용자가 특정 데이터 원본 개체에만 액세스할 수 있고 다른 데이터 원본 개체에는 액세스할 수 없게 됩니다. 이러한 다른 데이터 원본 개체는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 자체에서 큐브 및 마이닝 모델과 같은 개체를 처리하는 데 사용될 수 있습니다.  
  
-   **Windows 인증 지정**  
  
     데이터 원본 개체가 사용하는 연결 문자열이 Windows 인증을 지정하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 클라이언트를 가장할 수 있어야 합니다. 데이터 원본이 원격 컴퓨터에 있으면 가장을 위해 두 컴퓨터가 Kerberos 인증을 통해 트러스트되어야 합니다. 그렇지 않은 경우 쿼리는 대개 실패합니다. 자세한 내용은 [Configure Analysis Services for Kerberos constrained delegation](../../analysis-services/instances/configure-analysis-services-for-kerberos-constrained-delegation.md) 을 참조하세요.  
  
     클라이언트가 OLE DB 및 다른 클라이언트 구성 요소의 가장 수준 속성을 사용한 가장을 허용하지 않으면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 기본 데이터 원본에 대한 익명 연결을 시도합니다. 대부분의 데이터 원본이 익명 연결을 허용하지 않으므로 원격 데이터 원본에 대한 익명 연결은 대개 이뤄지지 않습니다.  
  
## <a name="see-also"></a>관련 항목:  
 [다차원 모델의 데이터 원본](../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)   
 [연결 문자열 속성 & #40; Analysis Services & #41;](../../analysis-services/instances/connection-string-properties-analysis-services.md)   
 [Analysis Services에서 지 원하는 인증 방법](../../analysis-services/instances/authentication-methodologies-supported-by-analysis-services.md)   
 [데이터 & #40; 차원에 대 한 사용자 지정 액세스 부여 Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)   
 [큐브 또는 모델 사용 권한 & #40; 부여 Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)   
 [셀 데이터 & #40;에 대 한 사용자 지정 액세스 부여 Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)  
  
  
