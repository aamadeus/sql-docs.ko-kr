---
title: ParentObject 요소 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ParentObject Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#ParentObject
- http://schemas.microsoft.com/analysisservices/2003/engine#ParentObject
- microsoft.xml.analysis.parentobject
helpviewer_keywords:
- ParentObject element
ms.assetid: f821f8f1-554a-4f16-bf09-262a9448e304
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 025c74f675e8718e31971fafcc0a15fdc8cfe7af
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="parentobject-element-xmla"></a>ParentObject 요소(XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  부모에 의해 정의 된 개체를 만들 부모 개체의 식별자가 포함 된 [만들기](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md) 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Create>  
   ...  
   <ParentObject>  
      <!-- Object reference -->  
   </ParentObject>  
   ...  
</Create>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|데이터 형식 및 길이|없음|  
|기본값|없음|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[만들기](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)|  
|자식 요소|필수 ASSL(Analysis Services Scripting Language) 요소. 개체 및 해당 상위 항목의 ID 요소를 나열 하 여 지정 (제외 하 고는 **서버** 개체입니다.) 예를 들어, 다음 **ParentObject** 요소는 파티션을 식별 합니다.<br /><br /> `<ParentObject>`<br /><br /> `<DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>`<br /><br /> `<CubeID>Adventure Works</CubeID>`<br /><br /> `<MeasureGroupID>Internet Sales</MeasureGroupID>`<br /><br /> `<PartitionID>Inernet_Sales_2001</PartitionID>`<br /><br /> `</ParentObject>`|  
  
## <a name="remarks"></a>주의  
 식별자가 나타나는 순서는 중요하지 않습니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 **시장 바구니** 에 포함 되는 마이닝 구조는 [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] 샘플 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 데이터베이스입니다.  
  
```  
<Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>database</DatabaseID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningStructure xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Market Basket</ID>  
            <Name>Market Basket</Name>  
            <Source xsi:type="DataSourceViewBinding">  
                <DataSourceViewID>Adventure Works DW</DataSourceViewID>  
            </Source>  
            <Language>1033</Language>  
            <Collation>Latin1_General_CI_AS</Collation>  
            <Columns>  
                <Column xsi:type="ScalarMiningStructureColumn">  
                    <ID>Order Number</ID>  
                    <Name>Order Number</Name>  
                    <IsKey>true</IsKey>  
                    <Type>Text</Type>  
                    <Content>Key</Content>  
                    <KeyColumns>  
                        <KeyColumn>  
                            <NullProcessing>Error</NullProcessing>  
                            <DataType>WChar</DataType>  
                            <DataSize>20</DataSize>  
                            <Source xsi:type="ColumnBinding">  
                                <TableID>dbo_vAssocSeqOrders</TableID>  
                                <ColumnID>OrderNumber</ColumnID>  
                            </Source>  
                        </KeyColumn>  
                    </KeyColumns>  
                </Column>  
                <Column xsi:type="TableMiningStructureColumn">  
                    <Annotations>  
                        <Annotation>  
                            <Name>MDXFilterComponent</Name>  
                            <Value />  
                        </Annotation>  
                    </Annotations>  
                    <ID>v Assoc Seq Line Items</ID>  
                    <Name>v Assoc Seq Line Items</Name>  
                    <ForeignKeyColumns>  
                        <ForeignKeyColumn>  
                            <NullProcessing>Error</NullProcessing>  
                            <DataType>WChar</DataType>  
                            <DataSize>20</DataSize>  
                            <Source xsi:type="ColumnBinding">  
                                <TableID>dbo_vAssocSeqLineItems</TableID>  
                                <ColumnID>OrderNumber</ColumnID>  
                            </Source>  
                        </ForeignKeyColumn>  
                    </ForeignKeyColumns>  
                    <Columns>  
                        <Column xsi:type="ScalarMiningStructureColumn">  
                            <ID>Model</ID>  
                            <Name>Model</Name>  
                            <IsKey>true</IsKey>  
                            <Type>Text</Type>  
                            <Content>Key</Content>  
                            <KeyColumns>  
                                <KeyColumn>  
                                    <DataType>WChar</DataType>  
                                    <DataSize>50</DataSize>  
                                    <Source xsi:type="ColumnBinding">  
                                        <TableID>dbo_vAssocSeqLineItems</TableID>  
                                        <ColumnID>Model</ColumnID>  
                                    </Source>  
                                </KeyColumn>  
                            </KeyColumns>  
                        </Column>  
                    </Columns>  
                </Column>  
            </Columns>  
            <MiningModels>  
                <MiningModel>  
                    <ID>Market Basket</ID>  
                    <Name>Association</Name>  
                    <Algorithm>Microsoft_Association_Rules</Algorithm>  
                    <AlgorithmParameters>  
                        <AlgorithmParameter>  
                            <Name>MINIMUM_PROBABILITY</Name>  
                            <Value xsi:type="xsd:double">0.1</Value>  
                        </AlgorithmParameter>  
                        <AlgorithmParameter>  
                            <Name>MINIMUM_SUPPORT</Name>  
                            <Value xsi:type="xsd:double">0.01</Value>  
                        </AlgorithmParameter>  
                    </AlgorithmParameters>  
                    <Columns>  
                        <Column>  
                            <ID>Order Number</ID>  
                            <Name>Order Number</Name>  
                            <SourceColumnID>Order Number</SourceColumnID>  
                            <Usage>Key</Usage>  
                        </Column>  
                        <Column>  
                            <ID>v Assoc Seq Line Items</ID>  
                            <Name>v Assoc Seq Line Items</Name>  
                            <SourceColumnID>v Assoc Seq Line Items</SourceColumnID>  
                            <Usage>Predict</Usage>  
                            <Columns>  
                                <Column>  
                                    <ID>Model</ID>  
                                    <Name>Model</Name>  
                                    <SourceColumnID>Model</SourceColumnID>  
                                    <Usage>Key</Usage>  
                                </Column>  
                            </Columns>  
                        </Column>  
                    </Columns>  
                    <Language>1033</Language>  
                    <Collation>Latin1_General_CI_AS</Collation>  
                </MiningModel>  
            </MiningModels>  
        </MiningStructure>  
    </ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>관련 항목:  
 [속성 & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  