---
title: "如何：压缩和解压缩文件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22a95ce18b602d4e329499c5d36557213e08a8b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compress-and-extract-files"></a>如何：压缩和解压缩文件
<xref:System.IO.Compression> 命名空间包含以下类型来对文件和流进行压缩或解压缩。 还可以使用这些类型来读取和修改压缩文件的内容：  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 下面的示例演示当使用压缩文件时可以执行的某些功能。  
  
## <a name="example"></a>示例  
 此示例演示如何使用 <xref:System.IO.Compression.ZipFile> 类创建和提取文件扩展名为 .zip 的压缩文件。 它将文件夹的内容压缩为一个新 .zip 文件，然后将该内容提取到一个新文件夹。 若要使用<xref:System.IO.Compression.ZipFile>类，则必须引用`System.IO.Compression.FileSystem`项目中的程序集。  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a>示例  
 下一示例演示如何循环访问现有 .zip 文件的内容并提取扩展名为 .txt 的文件。 它使用 <xref:System.IO.Compression.ZipArchive> 类访问现有 .zip 文件，使用 <xref:System.IO.Compression.ZipArchiveEntry> 类来检查压缩文件中的各个项。 它为 <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> 对象使用扩展方法 (<xref:System.IO.Compression.ZipArchiveEntry>)。 扩展方法可以在 <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> 类中使用。 若要使用<xref:System.IO.Compression.ZipFileExtensions>类，则必须引用`System.IO.Compression.FileSystem`项目中的程序集。  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a>示例  
 下一个示例使用 <xref:System.IO.Compression.ZipArchive> 类访问现有的 .zip 文件，然后向压缩文件添加新文件。 当将其添加到现有的 .zip 文件时，会对新文件进行压缩。  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a>示例  
 您也可以使用 <xref:System.IO.Compression.GZipStream> 和 <xref:System.IO.Compression.DeflateStream> 类压缩和解压缩数据。 它们使用相同的压缩算法。 除了 <xref:System.IO.Compression.GZipStream> 提供的方法之外，写入扩展名为 .gz 的文件的压缩 <xref:System.IO.Compression.GZipStream> 对象可以通过使用许多常用工具进行解压缩。 此示例演示如何压缩和解压缩文件的目录使用<xref:System.IO.Compression.GZipStream>类。  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [文件和流 I-O](../../../docs/standard/io/index.md)
