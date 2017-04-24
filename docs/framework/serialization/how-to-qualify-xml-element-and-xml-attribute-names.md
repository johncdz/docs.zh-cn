---
title: "如何：限定 XML 元素和 XML 特性名 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "限定 XML 元素"
  - "限定 XML 名称"
  - "XML 命名空间, 限定元素和名称"
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 如何：限定 XML 元素和 XML 特性名
[代码示例](#cpconworkingwithxmlnamespacesanchor1)  
  
 [XmlSerializerNamespaces](frlrfSystemXmlSerializationXmlSerializerNamespacesClassTopic) 类的实例所包含的 XML 命名空间必须符合万维网联合会 \(www.w3.org\) 规范“XML 中的命名空间”\(Namespaces in XML\)。  
  
 XML 命名空间提供了一种方法，用来限定 XML 文档中 XML 元素和 XML 特性的名称。限定名由前缀和本地名称组成，两者之间用冒号分隔。前缀仅用作占位符；它将映射到用于指定命名空间的 URI。统一管理的 URI 命名空间和本地名称的组合能够产生保证为全局唯一的名称。  
  
 通过创建 **XmlSerializerNamespaces** 的实例，并向对象中添加命名空间对，可以指定在 XML 文档中使用的前缀。  
  
### 在 XML 文档中创建限定名称  
  
1.  创建 **XmlSerializerNamespaces** 类的实例。  
  
2.  将所有的前缀和命名空间对添加至 **XmlSerializerNamespaces**。  
  
3.  对每个由 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx) 序列化为 XML 文档的成员或类应用相应的 **System.Xml.Serialization** 特性。  
  
     可用的特性包括：[XmlAnyElementAttribute](frlrfSystemXmlSerializationXmlAnyElementAttributeClassTopic)、[XmlArrayAttribute](frlrfSystemXmlSerializationXmlArrayAttributeClassTopic)、[XmlArrayItemAttribute](frlrfSystemXmlSerializationXmlArrayItemAttributeClassTopic)、[XmlAttributeAttribute](frlrfSystemXmlSerializationXmlAttributeAttributeClassTopic)、[XmlElementAttribute](frlrfSystemXmlSerializationXmlElementAttributeClassTopic)、[XmlRootAttribute](frlrfSystemXmlSerializationXmlRootAttributeClassTopic) 和 [XmlTypeAttribute](frlrfSystemXmlSerializationXmlTypeAttributeClassTopic)。  
  
4.  将每个特性的 **Namespace** 属性设置为 **XmlSerializerNamespaces** 的命名空间值之一。  
  
5.  将 **XmlSerializerNamespaces** 传递到 **XmlSerializer** 的 **Serialize** 方法。  
  
## 示例  
 下面的示例创建一个 **XmlSerializerNamespaces**，并向对象添加两个前缀和命名空间对。该代码创建了用来序列化 `Books` 类实例的 **XmlSerializer**，并通过 **XmlSerializerNamespaces** 调用 **Serialize** 方法，使 XML 可以包含带前缀的命名空间。  
  
```vb  
Option Explicit   
public class Price  
{  
    [XmlAttribute(Namespace = "http://www.cpandl.com")]  
    public string currency;  
    [XmlElement(Namespace = "http://www.cohowinery.com")]  
    public decimal price;  
}  
  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Serialization  
  
Public Class Run  
  
    Public Shared Sub Main()  
        Dim test As New Run()  
        test.SerializeObject("XmlNamespaces.xml")  
    End Sub 'Main  
  
    Public Sub SerializeObject(filename As String)  
        Dim mySerializer As New XmlSerializer(GetType(Books))  
        ' Writing a file requires a TextWriter.  
        Dim myWriter As New StreamWriter(filename)  
  
        ' Creates an XmlSerializerNamespaces and adds two  
        ' prefix-namespace pairs.   
        Dim myNamespaces As New XmlSerializerNamespaces()  
        myNamespaces.Add("books", "http://www.cpandl.com")  
        myNamespaces.Add("money", "http://www.cohowinery.com")  
  
        ' Creates a Book.  
        Dim myBook As New Book()  
        myBook.TITLE = "A Book Title"  
        Dim myPrice As New Price()  
        myPrice.price = CDec(9.95)  
        myPrice.currency = "US Dollar"  
        myBook.PRICE = myPrice  
        Dim myBooks As New Books()  
        myBooks.Book = myBook  
        mySerializer.Serialize(myWriter, myBooks, myNamespaces)  
        myWriter.Close()  
    End Sub  
End Class  
  
Public Class Books  
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _  
    Public Book As Book  
End Class 'Books  
  
<XmlType([Namespace] := "http://www.cpandl.com")> _  
Public Class Book  
  
    <XmlElement([Namespace] := "http://www.cpandl.com")> _  
    Public TITLE As String  
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _  
    Public PRICE As Price  
End Class  
  
Public Class Price  
    <XmlAttribute([Namespace] := "http://www.cpandl.com")> _  
    Public currency As String  
    Public <XmlElement([Namespace] := "http://www.cohowinery.com")> _  
        price As Decimal  
End Class  
  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Serialization;  
  
public class Run  
{  
    public static void Main()  
    {  
        Run test = new Run();  
        test.SerializeObject("XmlNamespaces.xml");  
    }  
    public void SerializeObject(string filename)  
    {  
        XmlSerializer mySerializer = new XmlSerializer(typeof(Books));  
        // Writing a file requires a TextWriter.  
        TextWriter myWriter = new StreamWriter(filename);  
  
        // Creates an XmlSerializerNamespaces and adds two  
        // prefix-namespace pairs.  
        XmlSerializerNamespaces myNamespaces =   
        new XmlSerializerNamespaces();  
        myNamespaces.Add("books", "http://www.cpandl.com");  
        myNamespaces.Add("money", "http://www.cohowinery.com");  
  
        // Creates a Book.  
        Book myBook = new Book();  
        myBook.TITLE = "A Book Title";  
        Price myPrice = new Price();  
        myPrice.price = (decimal) 9.95;  
        myPrice.currency = "US Dollar";  
        myBook.PRICE = myPrice;  
        Books myBooks = new Books();  
        myBooks.Book = myBook;  
        mySerializer.Serialize(myWriter,myBooks,myNamespaces);  
        myWriter.Close();  
    }  
}  
  
public class Books  
{  
    [XmlElement(Namespace = "http://www.cohowinery.com")]  
    public Book Book;  
}  
  
[XmlType(Namespace ="http://www.cpandl.com")]  
public class Book  
{  
    [XmlElement(Namespace = "http://www.cpandl.com")]  
    public string TITLE;  
    [XmlElement(Namespace ="http://www.cohowinery.com")]  
    public Price PRICE;  
}  
```  
  
## 请参阅  
 [XML 架构定义工具和 XML 序列化](../../../docs/framework/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)   
 [XML 序列化简介](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [XmlSerializer Class](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)   
 [用来控制 XML 序列化的特性](../../../docs/framework/serialization/attributes-that-control-xml-serialization.md)   
 [XmlSerializerNamespaces Class](frlrfSystemXmlSerializationXmlSerializerNamespacesClassTopic)   
 [如何：指定 XML 流的替代元素名称](../../../docs/framework/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)   
 [如何：序列化对象](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [如何：反序列化对象](../../../docs/framework/serialization/how-to-deserialize-an-object.md)