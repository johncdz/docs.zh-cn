---
title: "推断列"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ba06bce55db53de1da1c07d2a6451d5664fa23bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="inferring-columns"></a>推断列
ADO.NET 从 XML 文档中确定了哪些元素要作为 <xref:System.Data.DataSet> 的表进行推断后，即开始推断这些表的列。 ADO.NET 2.0 引入了新的架构推断引擎，为每个推断强类型的数据类型**simpleType**元素。 在以前版本的数据类型推断**simpleType**元素始终是**xsd: string**。  
  
## <a name="migration-and-backward-compatibility"></a>迁移和向后兼容性  
 **ReadXml**方法采用类型的自变量**InferSchema**。 使用此自变量可以指定与以前的版本兼容的推断行为。 可用值**InferSchema**枚举显示下表中。  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 通过始终将简单类型作为 <xref:System.String> 进行推断，提供向后兼容性。  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 推断强类型化的数据类型。 如果与 <xref:System.Data.DataTable> 一起使用，会发生异常。  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 忽略任何内联架构并将数据读入现有的 <xref:System.Data.DataSet> 架构。  
  
## <a name="attributes"></a>特性  
 中定义[推断表](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)，具有属性的元素将被推断为表。 然后，该元素的属性将被推断为该表的列。 **ColumnMapping**的列的属性将设置为**MappingType.Attribute**，以确保列名称将写为属性中，如果架构写回 XML。 这些属性的值存储在表的行中。 例如，考虑以下 XML：  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 推断过程将生成名为的表**Element1**具有两列， **attr1**和**attr2**。 **ColumnMapping**这两个列的属性将设置为**MappingType.Attribute**。  
  
 **数据集：** DocumentElement  
  
 **表：** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>不具有属性或子元素的元素  
 如果元素不具有子元素或属性，它将被推断为列。 **ColumnMapping**列属性将设置为**MappingType.Element**。 子元素的文本存储在表的行中。 例如，考虑以下 XML：  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推断过程将生成名为的表**Element1**具有两列， **ChildElement1**和**ChildElement2**。 **ColumnMapping**这两个列的属性将设置为**MappingType.Element**。  
  
 **数据集：** DocumentElement  
  
 **表：** Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Text1|Text2|  
  
## <a name="see-also"></a>另请参阅  
 [从 XML 推断数据集关系结构](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [从 XML 加载数据集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [从 XML 加载数据集架构信息](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [在数据集中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [数据集、数据表和数据视图](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET 托管提供程序和数据集开发人员中心](http://go.microsoft.com/fwlink/?LinkId=217917)
