---
title: "序列 (F#)"
description: "了解如何使用 F # 序列，当你具有大型，排序的数据集合，但是不一定是希望使用的所有元素。"
keywords: "visual f#, f#, 函数编程"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 23dc7d75-cd26-4df2-9be3-9d1aba5c4443
ms.openlocfilehash: b0562a6efbd2398cd8730bb835a1833955fee1c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="sequences"></a><span data-ttu-id="aa399-104">序列</span><span class="sxs-lookup"><span data-stu-id="aa399-104">Sequences</span></span>

> [!NOTE]
<span data-ttu-id="aa399-105">本文中的 API 参考链接将转至 MSDN。</span><span class="sxs-lookup"><span data-stu-id="aa399-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="aa399-106">Docs.microsoft.com API 参考尚未完成。</span><span class="sxs-lookup"><span data-stu-id="aa399-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="aa399-107">A*序列*是逻辑的一系列元素类型相同的所有。</span><span class="sxs-lookup"><span data-stu-id="aa399-107">A *sequence* is a logical series of elements all of one type.</span></span> <span data-ttu-id="aa399-108">当你具有大型，排序的数据集合，但一定不希望使用的所有元素时，序列会特别有用。</span><span class="sxs-lookup"><span data-stu-id="aa399-108">Sequences are particularly useful when you have a large, ordered collection of data but do not necessarily expect to use all of the elements.</span></span> <span data-ttu-id="aa399-109">各个序列元素计算仅为必需的因此序列都可以提供更好的性能比在情况下在不使用的所有元素的列表。</span><span class="sxs-lookup"><span data-stu-id="aa399-109">Individual sequence elements are computed only as required, so a sequence can provide better performance than a list in situations in which not all the elements are used.</span></span> <span data-ttu-id="aa399-110">序列由`seq<'T>`类型，这是一个别名为`System.Collections.Generic.IEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="aa399-110">Sequences are represented by the `seq<'T>` type, which is an alias for `System.Collections.Generic.IEnumerable`.</span></span> <span data-ttu-id="aa399-111">因此，任何.NET Framework 类型实现`System.IEnumerable`可用作一个序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-111">Therefore, any .NET Framework type that implements `System.IEnumerable` can be used as a sequence.</span></span> <span data-ttu-id="aa399-112">[Seq 模块](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)对涉及多个序列的操作提供支持。</span><span class="sxs-lookup"><span data-stu-id="aa399-112">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) provides support for manipulations involving sequences.</span></span>

## <a name="sequence-expressions"></a><span data-ttu-id="aa399-113">序列表达式</span><span class="sxs-lookup"><span data-stu-id="aa399-113">Sequence Expressions</span></span>
<span data-ttu-id="aa399-114">A*序列表达式*是计算结果为一个序列的表达式。</span><span class="sxs-lookup"><span data-stu-id="aa399-114">A *sequence expression* is an expression that evaluates to a sequence.</span></span> <span data-ttu-id="aa399-115">序列表达式可以采用多种形式。</span><span class="sxs-lookup"><span data-stu-id="aa399-115">Sequence expressions can take a number of forms.</span></span> <span data-ttu-id="aa399-116">最简单的形式指定范围。</span><span class="sxs-lookup"><span data-stu-id="aa399-116">The simplest form specifies a range.</span></span> <span data-ttu-id="aa399-117">例如，`seq { 1 .. 5 }`创建包含五个元素，包括 1 和 5 的终结点的序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-117">For example, `seq { 1 .. 5 }` creates a sequence that contains five elements, including the endpoints 1 and 5.</span></span> <span data-ttu-id="aa399-118">也可以指定一个增量 （或递减） 之间两个双句点。</span><span class="sxs-lookup"><span data-stu-id="aa399-118">You can also specify an increment (or decrement) between two double periods.</span></span> <span data-ttu-id="aa399-119">例如，以下代码创建为 10 的倍数的序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-119">For example, the following code creates the sequence of multiples of 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

<span data-ttu-id="aa399-120">序列表达式组成的序列的值为生成的 F # 表达式。</span><span class="sxs-lookup"><span data-stu-id="aa399-120">Sequence expressions are made up of F# expressions that produce values of the sequence.</span></span> <span data-ttu-id="aa399-121">他们可以使用`yield`关键字来生成将成为序列的一部分的值。</span><span class="sxs-lookup"><span data-stu-id="aa399-121">They can use the `yield` keyword to produce values that become part of the sequence.</span></span>

<span data-ttu-id="aa399-122">下面是一个示例。</span><span class="sxs-lookup"><span data-stu-id="aa399-122">Following is an example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

<span data-ttu-id="aa399-123">你可以使用`->`运算符而不是`yield`，在这种情况下则可以省略`do`关键字，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="aa399-123">You can use the `->` operator instead of `yield`, in which case you can omit the `do` keyword, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

<span data-ttu-id="aa399-124">下面的代码生成到一个数组，表示网格坐标对以及索引的列表。</span><span class="sxs-lookup"><span data-stu-id="aa399-124">The following code generates a list of coordinate pairs along with an index into an array that represents the grid.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

<span data-ttu-id="aa399-125">`if`序列中，使用的表达式是一个筛选器。</span><span class="sxs-lookup"><span data-stu-id="aa399-125">An `if` expression used in a sequence is a filter.</span></span> <span data-ttu-id="aa399-126">例如，若要生成只包含质数，假设您有一个函数的序列`isprime`类型的`int -> bool`，按以下方式构造序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-126">For example, to generate a sequence of only prime numbers, assuming that you have a function `isprime` of type `int -> bool`, construct the sequence as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

<span data-ttu-id="aa399-127">当你使用`yield`或`->`迭代后，在每次迭代都应生成序列的单个元素。</span><span class="sxs-lookup"><span data-stu-id="aa399-127">When you use `yield` or `->` in an iteration, each iteration is expected to generate a single element of the sequence.</span></span> <span data-ttu-id="aa399-128">如果每次迭代将生成一个序列的元素，使用`yield!`。</span><span class="sxs-lookup"><span data-stu-id="aa399-128">If each iteration produces a sequence of elements, use `yield!`.</span></span> <span data-ttu-id="aa399-129">在这种情况下，每个迭代上生成的元素串联在一起以生成最终的序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-129">In that case, the elements generated on each iteration are concatenated to produce the final sequence.</span></span>

<span data-ttu-id="aa399-130">你可以组合在一起在序列表达式中的多个表达式。</span><span class="sxs-lookup"><span data-stu-id="aa399-130">You can combine multiple expressions together in a sequence expression.</span></span> <span data-ttu-id="aa399-131">由每个表达式生成的元素连接在一起。</span><span class="sxs-lookup"><span data-stu-id="aa399-131">The elements generated by each expression are concatenated together.</span></span> <span data-ttu-id="aa399-132">有关示例，请参阅本主题的"示例"一节。</span><span class="sxs-lookup"><span data-stu-id="aa399-132">For an example, see the "Examples" section of this topic.</span></span>

## <a name="examples"></a><span data-ttu-id="aa399-133">示例</span><span class="sxs-lookup"><span data-stu-id="aa399-133">Examples</span></span>
<span data-ttu-id="aa399-134">第一个示例使用包含迭代、 筛选器，yield 来生成一个数组为序列表达式。</span><span class="sxs-lookup"><span data-stu-id="aa399-134">The first example uses a sequence expression that contains an iteration, a filter, and a yield to generate an array.</span></span> <span data-ttu-id="aa399-135">此代码将打印介于 1 和 100 到控制台之间的质数的序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-135">This code prints a sequence of prime numbers between 1 and 100 to the console.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

<span data-ttu-id="aa399-136">下面的代码使用`yield`若要创建的三个元素，其中每个包括的两个因素和产品的元组组成一个乘法表。</span><span class="sxs-lookup"><span data-stu-id="aa399-136">The following code uses `yield` to create a multiplication table that consists of tuples of three elements, each consisting of two factors and the product.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

<span data-ttu-id="aa399-137">下面的示例演示了利用`yield!`组合到一个最终序列的单个序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-137">The following example demonstrates the use of `yield!` to combine individual sequences into a single final sequence.</span></span> <span data-ttu-id="aa399-138">在这种情况下，二进制树中每个子树的序列串联在一起的递归函数，以生成最终的序列中。</span><span class="sxs-lookup"><span data-stu-id="aa399-138">In this case, the sequences for each subtree in a binary tree are concatenated in a recursive function to produce the final sequence.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]
    
## <a name="using-sequences"></a><span data-ttu-id="aa399-139">使用序列</span><span class="sxs-lookup"><span data-stu-id="aa399-139">Using Sequences</span></span>
<span data-ttu-id="aa399-140">序列支持许多功能与成员相同[列出](lists.md)。</span><span class="sxs-lookup"><span data-stu-id="aa399-140">Sequences support many of the same functions as [lists](lists.md).</span></span> <span data-ttu-id="aa399-141">序列还支持分组，然后通过使用键生成函数计算等操作。</span><span class="sxs-lookup"><span data-stu-id="aa399-141">Sequences also support operations such as grouping and counting by using key-generating functions.</span></span> <span data-ttu-id="aa399-142">序列还支持多不同的功能，用于提取子序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-142">Sequences also support more diverse functions for extracting subsequences.</span></span>

<span data-ttu-id="aa399-143">许多数据类型，如列表、 数组、 组和地图隐式是序列，因为它们是可枚举集合。</span><span class="sxs-lookup"><span data-stu-id="aa399-143">Many data types, such as lists, arrays, sets, and maps are implicitly sequences because they are enumerable collections.</span></span> <span data-ttu-id="aa399-144">将一个序列，作为参数的工作方式与任何常见的 F # 数据类型，此外为实现任何.NET Framework 数据类型的函数`System.Collections.Generic.IEnumerable<'T>`。</span><span class="sxs-lookup"><span data-stu-id="aa399-144">A function that takes a sequence as an argument works with any of the common F# data types, in addition to any .NET Framework data type that implements `System.Collections.Generic.IEnumerable<'T>`.</span></span> <span data-ttu-id="aa399-145">正好相反，将列表作为参数，它只能使用列表的函数。</span><span class="sxs-lookup"><span data-stu-id="aa399-145">Contrast this to a function that takes a list as an argument, which can only take lists.</span></span> <span data-ttu-id="aa399-146">类型`seq<'T>`是类型缩写`IEnumerable<'T>`。</span><span class="sxs-lookup"><span data-stu-id="aa399-146">The type `seq<'T>` is a type abbreviation for `IEnumerable<'T>`.</span></span> <span data-ttu-id="aa399-147">这意味着，可以实现泛型的任何类型`System.Collections.Generic.IEnumerable<'T>`，其中包括数组、 列表、 设置，并在 F # 中，并还大多数.NET Framework 集合类型，映射是与兼容`seq`键入和可以在一个序列的任何地方使用。</span><span class="sxs-lookup"><span data-stu-id="aa399-147">This means that any type that implements the generic `System.Collections.Generic.IEnumerable<'T>`, which includes arrays, lists, sets, and maps in F#, and also most .NET Framework collection types, is compatible with the `seq` type and can be used wherever a sequence is expected.</span></span>


## <a name="module-functions"></a><span data-ttu-id="aa399-148">模块函数</span><span class="sxs-lookup"><span data-stu-id="aa399-148">Module Functions</span></span>
<span data-ttu-id="aa399-149">[Seq 模块](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)中[Microsoft.FSharp.Collections 命名空间](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f)包含用于使用序列函数。</span><span class="sxs-lookup"><span data-stu-id="aa399-149">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) in the [Microsoft.FSharp.Collections namespace](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) contains functions for working with sequences.</span></span> <span data-ttu-id="aa399-150">这些函数处理列表、 数组、 映射和集，因为所有这些类型是可枚举的并因此会被视为序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-150">These functions work with lists, arrays, maps, and sets as well, because all of those types are enumerable, and therefore can be treated as sequences.</span></span>


## <a name="creating-sequences"></a><span data-ttu-id="aa399-151">创建序列</span><span class="sxs-lookup"><span data-stu-id="aa399-151">Creating Sequences</span></span>
<span data-ttu-id="aa399-152">通过使用序列表达式，如前面所述，或通过使用某些函数，您可以创建序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-152">You can create sequences by using sequence expressions, as described previously, or by using certain functions.</span></span>

<span data-ttu-id="aa399-153">你可以通过创建空序列[Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)，也可以通过使用来创建只在一个指定元素的序列[Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7)。</span><span class="sxs-lookup"><span data-stu-id="aa399-153">You can create an empty sequence by using [Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), or you can create a sequence of just one specified element by using [Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet9.fs)]

<span data-ttu-id="aa399-154">你可以使用[Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576)创建为其元素通过使用你提供的函数创建的序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-154">You can use [Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) to create a sequence for which the elements are created by using a function that you provide.</span></span> <span data-ttu-id="aa399-155">您还可以为序列提供大小。</span><span class="sxs-lookup"><span data-stu-id="aa399-155">You also provide a size for the sequence.</span></span> <span data-ttu-id="aa399-156">此函数就像是[List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)，只不过循环访问序列时才会创建元素。</span><span class="sxs-lookup"><span data-stu-id="aa399-156">This function is just like [List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), except that the elements are not created until you iterate through the sequence.</span></span> <span data-ttu-id="aa399-157">下面的代码演示如何使用`Seq.init`。</span><span class="sxs-lookup"><span data-stu-id="aa399-157">The following code illustrates the use of `Seq.init`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet10.fs)]

<span data-ttu-id="aa399-158">输出为</span><span class="sxs-lookup"><span data-stu-id="aa399-158">The output is</span></span>

```
0 10 20 30 40
```

<span data-ttu-id="aa399-159">通过使用[Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99)和[Seq.ofList &#60;&#62;函数](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d)，你可以从数组和列表创建序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-159">By using [Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) and [Seq.ofList&#60;'T&#62; Function](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), you can create sequences from arrays and lists.</span></span> <span data-ttu-id="aa399-160">但是，你还可以将转换数组和列表到序列使用转换运算符。</span><span class="sxs-lookup"><span data-stu-id="aa399-160">However, you can also convert arrays and lists to sequences by using a cast operator.</span></span> <span data-ttu-id="aa399-161">在下面的代码演示了这两种技术。</span><span class="sxs-lookup"><span data-stu-id="aa399-161">Both techniques are shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet11.fs)]

<span data-ttu-id="aa399-162">通过使用[Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334)，您可以创建一个序列，从弱类型的集合，如中定义的那些`System.Collections`。</span><span class="sxs-lookup"><span data-stu-id="aa399-162">By using [Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), you can create a sequence from a weakly typed collection, such as those defined in `System.Collections`.</span></span> <span data-ttu-id="aa399-163">此类弱类型的集合具有元素类型`System.Object`并通过使用非泛型枚举`System.Collections.Generic.IEnumerable&#96;1`类型。</span><span class="sxs-lookup"><span data-stu-id="aa399-163">Such weakly typed collections have the element type `System.Object` and are enumerated by using the non-generic `System.Collections.Generic.IEnumerable&#96;1` type.</span></span> <span data-ttu-id="aa399-164">下面的代码演示如何使用`Seq.cast`要转换`System.Collections.ArrayList`为一个序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-164">The following code illustrates the use of `Seq.cast` to convert an `System.Collections.ArrayList` into a sequence.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet12.fs)]

<span data-ttu-id="aa399-165">您可以通过使用定义无限的序列[Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef)函数。</span><span class="sxs-lookup"><span data-stu-id="aa399-165">You can define infinite sequences by using the [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) function.</span></span> <span data-ttu-id="aa399-166">此类的序列，你可以提供生成每个元素从元素的索引的函数。</span><span class="sxs-lookup"><span data-stu-id="aa399-166">For such a sequence, you provide a function that generates each element from the index of the element.</span></span> <span data-ttu-id="aa399-167">之所以可行无限的序列是由于迟缓计算;根据需要通过调用你指定的函数，则会创建元素。</span><span class="sxs-lookup"><span data-stu-id="aa399-167">Infinite sequences are possible because of lazy evaluation; elements are created as needed by calling the function that you specify.</span></span> <span data-ttu-id="aa399-168">下面的代码示例将生成一系列交替出现的连续整数的平方的倒数浮点数，在此情况下无限序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-168">The following code example produces an infinite sequence of floating point numbers, in this case the alternating series of reciprocals of squares of successive integers.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet13.fs)]

<span data-ttu-id="aa399-169">[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21)从计算函数，它接受状态，并将其以生成序列中的每个后续元素转换生成的序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-169">[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) generates a sequence from a computation function that takes a state and transforms it to produce each subsequent element in the sequence.</span></span> <span data-ttu-id="aa399-170">状态为只是一个值，用于计算每个元素，并且可以将更改为计算每个元素。</span><span class="sxs-lookup"><span data-stu-id="aa399-170">The state is just a value that is used to compute each element, and can change as each element is computed.</span></span> <span data-ttu-id="aa399-171">第二个参数`Seq.unfold`是用于启动序列的初始值。</span><span class="sxs-lookup"><span data-stu-id="aa399-171">The second argument to `Seq.unfold` is the initial value that is used to start the sequence.</span></span> <span data-ttu-id="aa399-172">`Seq.unfold`使用状态时，它使你可以通过返回终止序列选项类型`None`值。</span><span class="sxs-lookup"><span data-stu-id="aa399-172">`Seq.unfold` uses an option type for the state, which enables you to terminate the sequence by returning the `None` value.</span></span> <span data-ttu-id="aa399-173">下面的代码演示的序列，两个示例`seq1`和`fib`，由生成`unfold`操作。</span><span class="sxs-lookup"><span data-stu-id="aa399-173">The following code shows two examples of sequences, `seq1` and `fib`, that are generated by an `unfold` operation.</span></span> <span data-ttu-id="aa399-174">首先， `seq1`，是只具有最多 100 个数字的简单序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-174">The first, `seq1`, is just a simple sequence with numbers up to 100.</span></span> <span data-ttu-id="aa399-175">第二个， `fib`，使用`unfold`来计算斐波那契序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-175">The second, `fib`, uses `unfold` to compute the Fibonacci sequence.</span></span> <span data-ttu-id="aa399-176">因为斐波那契序列中的每个元素之和的前两个斐波那契数字，状态的值将是一个元组组成的序列中前两个数字。</span><span class="sxs-lookup"><span data-stu-id="aa399-176">Because each element in the Fibonacci sequence is the sum of the previous two Fibonacci numbers, the state value is a tuple that consists of the previous two numbers in the sequence.</span></span> <span data-ttu-id="aa399-177">初始值是`(1,1)`，该序列中的前两个数字。</span><span class="sxs-lookup"><span data-stu-id="aa399-177">The initial value is `(1,1)`, the first two numbers in the sequence.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet14.fs)]

<span data-ttu-id="aa399-178">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="aa399-178">The output is as follows:</span></span>

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

<span data-ttu-id="aa399-179">下面的代码演示了使用许多序列模块函数此处所述来生成和计算无限的序列的值。</span><span class="sxs-lookup"><span data-stu-id="aa399-179">The following code is an example that uses many of the sequence module functions described here to generate and compute the values of infinite sequences.</span></span> <span data-ttu-id="aa399-180">该代码可能需要几分钟才能运行。</span><span class="sxs-lookup"><span data-stu-id="aa399-180">The code might take a few minutes to run.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet15.fs)]
    
## <a name="searching-and-finding-elements"></a><span data-ttu-id="aa399-181">搜索和查找元素</span><span class="sxs-lookup"><span data-stu-id="aa399-181">Searching and Finding Elements</span></span>
<span data-ttu-id="aa399-182">序列支持适用于列表的功能： [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1)， [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565)， [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8)， [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3)， [Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d)， [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)，和[Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)。</span><span class="sxs-lookup"><span data-stu-id="aa399-182">Sequences support functionality available with lists: [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), and [Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a).</span></span> <span data-ttu-id="aa399-183">可用于序列这些函数的版本的计算结果仅到进行搜索的元素序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-183">The versions of these functions that are available for sequences evaluate the sequence only up to the element that is being searched for.</span></span> <span data-ttu-id="aa399-184">有关示例，请参阅[列出](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)。</span><span class="sxs-lookup"><span data-stu-id="aa399-184">For examples, see [Lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span>


## <a name="obtaining-subsequences"></a><span data-ttu-id="aa399-185">获取子序列</span><span class="sxs-lookup"><span data-stu-id="aa399-185">Obtaining Subsequences</span></span>
<span data-ttu-id="aa399-186">[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770)和[Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395)是否与相应的函数，只不过的筛选和选择不会发生之前计算序列元素所提供的列表，类似。</span><span class="sxs-lookup"><span data-stu-id="aa399-186">[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) and [Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) are like the corresponding functions that are available for lists, except that the filtering and choosing does not occur until the sequence elements are evaluated.</span></span>

<span data-ttu-id="aa399-187">[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244)从另一个序列，创建一个序列，但会指定数量的元素的序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-187">[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) creates a sequence from another sequence, but limits the sequence to a specified number of elements.</span></span> <span data-ttu-id="aa399-188">[Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596)创建新的序列，其中包含仅的指定的数量的序列的开始的元素。</span><span class="sxs-lookup"><span data-stu-id="aa399-188">[Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) creates a new sequence that contains only a specified number of elements from the start of a sequence.</span></span> <span data-ttu-id="aa399-189">如果有较少元素序列中的超过您指定要执行，`Seq.take`引发`System.InvalidOperationException`。</span><span class="sxs-lookup"><span data-stu-id="aa399-189">If there are fewer elements in the sequence than you specify to take, `Seq.take` throws a `System.InvalidOperationException`.</span></span> <span data-ttu-id="aa399-190">之间的差异`Seq.take`和`Seq.truncate`在于`Seq.truncate`数少于指定的元素数是否不会生成错误。</span><span class="sxs-lookup"><span data-stu-id="aa399-190">The difference between `Seq.take` and `Seq.truncate` is that `Seq.truncate` does not produce an error if the number of elements is fewer than the number you specify.</span></span>

<span data-ttu-id="aa399-191">下面的代码显示的行为和之间的差异`Seq.truncate`和`Seq.take`。</span><span class="sxs-lookup"><span data-stu-id="aa399-191">The following code shows the behavior of and differences between `Seq.truncate` and `Seq.take`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet16.fs)]

<span data-ttu-id="aa399-192">输出中，发生此错误之前，是，如下所示。</span><span class="sxs-lookup"><span data-stu-id="aa399-192">The output, before the error occurs, is as follows.</span></span>

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

<span data-ttu-id="aa399-193">通过使用[Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92)，可以指定的谓词函数 （布尔函数），并从为其谓词是对原始序列的这些元素组成的另一个序列中创建序列`true`，但停止谓词为其返回的第一个元素之前`false`。</span><span class="sxs-lookup"><span data-stu-id="aa399-193">By using [Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), you can specify a predicate function (a Boolean function) and create a sequence from another sequence made up of those elements of the original sequence for which the predicate is `true`, but stop before the first element for which the predicate returns `false`.</span></span> <span data-ttu-id="aa399-194">[Seq.skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1)返回序列，可跳过指定的数目的另一个序列的第一个元素并返回剩余元素。</span><span class="sxs-lookup"><span data-stu-id="aa399-194">[Seq.skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) returns a sequence that skips a specified number of the first elements of another sequence and returns the remaining elements.</span></span> <span data-ttu-id="aa399-195">[Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16)返回跳过另一个序列的第一个元素，只要该谓词返回的序列`true`，然后返回剩余元素，谓词为其返回的第一个元素开始`false`.</span><span class="sxs-lookup"><span data-stu-id="aa399-195">[Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) returns a sequence that skips the first elements of another sequence as long as the predicate returns `true`, and then returns the remaining elements, starting with the first element for which the predicate returns `false`.</span></span>

<span data-ttu-id="aa399-196">下面的代码示例阐释了的行为和之间的差异`Seq.takeWhile`， `Seq.skip`，和`Seq.skipWhile`。</span><span class="sxs-lookup"><span data-stu-id="aa399-196">The following code example illustrates the behavior of and differences between `Seq.takeWhile`, `Seq.skip`, and `Seq.skipWhile`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet17.fs)]

<span data-ttu-id="aa399-197">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="aa399-197">The output is as follows.</span></span>

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a><span data-ttu-id="aa399-198">转换序列</span><span class="sxs-lookup"><span data-stu-id="aa399-198">Transforming Sequences</span></span>
<span data-ttu-id="aa399-199">[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1)创建新的序列中对输入序列的连续元素组合到元组。</span><span class="sxs-lookup"><span data-stu-id="aa399-199">[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) creates a new sequence in which successive elements of the input sequence are grouped into tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet18.fs)]

<span data-ttu-id="aa399-200">[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744)类似`Seq.pairwise`，只不过而不是生成的元组序列，它会生成一个序列包含的相邻元素副本的数组 (*窗口*) 从序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-200">[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) is like `Seq.pairwise`, except that instead of producing a sequence of tuples, it produces a sequence of arrays that contain copies of adjacent elements (a *window*) from the sequence.</span></span> <span data-ttu-id="aa399-201">每个数组中指定所需的相邻元素的数目。</span><span class="sxs-lookup"><span data-stu-id="aa399-201">You specify the number of adjacent elements you want in each array.</span></span>

<span data-ttu-id="aa399-202">以下代码示例演示了 `Seq.windowed` 的用法。</span><span class="sxs-lookup"><span data-stu-id="aa399-202">The following code example demonstrates the use of `Seq.windowed`.</span></span> <span data-ttu-id="aa399-203">在这种情况下的窗口中的元素数为 3。</span><span class="sxs-lookup"><span data-stu-id="aa399-203">In this case the number of elements in the window is 3.</span></span> <span data-ttu-id="aa399-204">该示例使用`printSeq`，前面的代码示例中定义。</span><span class="sxs-lookup"><span data-stu-id="aa399-204">The example uses `printSeq`, which is defined in the previous code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet180.fs)]

<span data-ttu-id="aa399-205">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="aa399-205">The output is as follows.</span></span>

<span data-ttu-id="aa399-206">初始序列：</span><span class="sxs-lookup"><span data-stu-id="aa399-206">Initial sequence:</span></span>

```
1.0 1.5 2.0 1.5 1.0 1.5 

Windows of length 3: 
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|] 

Moving average: 
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a><span data-ttu-id="aa399-207">具有多个序列的操作</span><span class="sxs-lookup"><span data-stu-id="aa399-207">Operations with Multiple Sequences</span></span>
<span data-ttu-id="aa399-208">[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4)和[Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16)采用两个或三个序列并生成一个元组序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-208">[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) and [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) take two or three sequences and produce a sequence of tuples.</span></span> <span data-ttu-id="aa399-209">这些函数是与相应的函数可用于类似[列出](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)。</span><span class="sxs-lookup"><span data-stu-id="aa399-209">These functions are like the corresponding functions available for [lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span> <span data-ttu-id="aa399-210">没有相应的功能将一个序列分成两个或多个序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-210">There is no corresponding functionality to separate one sequence into two or more sequences.</span></span> <span data-ttu-id="aa399-211">如果你需要此功能的序列，将序列转换为列表，并使用[List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)。</span><span class="sxs-lookup"><span data-stu-id="aa399-211">If you need this functionality for a sequence, convert the sequence to a list and use [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>


## <a name="sorting-comparing-and-grouping"></a><span data-ttu-id="aa399-212">排序、 比较和分组</span><span class="sxs-lookup"><span data-stu-id="aa399-212">Sorting, Comparing, and Grouping</span></span>
<span data-ttu-id="aa399-213">对于列表中支持的排序函数也适用于序列中。</span><span class="sxs-lookup"><span data-stu-id="aa399-213">The sorting functions supported for lists also work with sequences.</span></span> <span data-ttu-id="aa399-214">这包括[Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e)和[Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f)。</span><span class="sxs-lookup"><span data-stu-id="aa399-214">This includes [Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) and [Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f).</span></span> <span data-ttu-id="aa399-215">这些函数循环访问整个序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-215">These functions iterate through the whole sequence.</span></span>

<span data-ttu-id="aa399-216">通过比较两个序列[Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f)函数。</span><span class="sxs-lookup"><span data-stu-id="aa399-216">You compare two sequences by using the [Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) function.</span></span> <span data-ttu-id="aa399-217">该函数反过来，比较连续元素，并在遇到第一个不相等对时停止。</span><span class="sxs-lookup"><span data-stu-id="aa399-217">The function compares successive elements in turn, and stops when it encounters the first unequal pair.</span></span> <span data-ttu-id="aa399-218">比较不有利于实现任何其他元素。</span><span class="sxs-lookup"><span data-stu-id="aa399-218">Any additional elements do not contribute to the comparison.</span></span>

<span data-ttu-id="aa399-219">以下代码显示了 `Seq.compareWith` 的用法。</span><span class="sxs-lookup"><span data-stu-id="aa399-219">The following code shows the use of `Seq.compareWith`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet19.fs)]

<span data-ttu-id="aa399-220">在前面的代码中，仅第一个元素是计算和检查，并且结果为-1。</span><span class="sxs-lookup"><span data-stu-id="aa399-220">In the previous code, only the first element is computed and examined, and the result is -1.</span></span>

<span data-ttu-id="aa399-221">[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f)采用生成名为的值的函数*密钥*每个元素。</span><span class="sxs-lookup"><span data-stu-id="aa399-221">[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) takes a function that generates a value called a *key* for each element.</span></span> <span data-ttu-id="aa399-222">通过对每个元素调用此函数的每个元素生成一个密钥。</span><span class="sxs-lookup"><span data-stu-id="aa399-222">A key is generated for each element by calling this function on each element.</span></span> <span data-ttu-id="aa399-223">`Seq.countBy`然后返回一个序列，其中包含的项的值，并生成密钥的每个值的元素数的计数。</span><span class="sxs-lookup"><span data-stu-id="aa399-223">`Seq.countBy` then returns a sequence that contains the key values, and a count of the number of elements that generated each value of the key.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet201.fs)]

<span data-ttu-id="aa399-224">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="aa399-224">The output is as follows.</span></span>

```
(1, 34) (2, 33) (0, 33)
```

<span data-ttu-id="aa399-225">前面的输出显示有 34 元素生成的项 1，对原始序列的 33 个值生成的密钥 2 和 33 生成了键 0 的值。</span><span class="sxs-lookup"><span data-stu-id="aa399-225">The previous output shows that there were 34 elements of the original sequence that produced the key 1, 33 values that produced the key 2, and 33 values that produced the key 0.</span></span>

<span data-ttu-id="aa399-226">你可以通过调用分组的序列的元素[Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd)。</span><span class="sxs-lookup"><span data-stu-id="aa399-226">You can group elements of a sequence by calling [Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd).</span></span> <span data-ttu-id="aa399-227">`Seq.groupBy`采用一个序列和从元素中生成一个键的函数。</span><span class="sxs-lookup"><span data-stu-id="aa399-227">`Seq.groupBy` takes a sequence and a function that generates a key from an element.</span></span> <span data-ttu-id="aa399-228">序列的每个元素执行函数。</span><span class="sxs-lookup"><span data-stu-id="aa399-228">The function is executed on each element of the sequence.</span></span> <span data-ttu-id="aa399-229">`Seq.groupBy`返回的元组，其中每个元组的第一个元素是键，而第二个是生成该密钥的元素的序列的序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-229">`Seq.groupBy` returns a sequence of tuples, where the first element of each tuple is the key and the second is a sequence of elements that produce that key.</span></span>

<span data-ttu-id="aa399-230">下面的代码示例演示了利用`Seq.groupBy`进行分区的从 1 到 100 的数字序列分成三个具有不同的密钥值 0、 1 和 2 的组。</span><span class="sxs-lookup"><span data-stu-id="aa399-230">The following code example shows the use of `Seq.groupBy` to partition the sequence of numbers from 1 to 100 into three groups that have the distinct key values 0, 1, and 2.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet202.fs)]

<span data-ttu-id="aa399-231">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="aa399-231">The output is as follows.</span></span>

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

<span data-ttu-id="aa399-232">你可以创建通过调用中消除重复的元素的序列[Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401)。</span><span class="sxs-lookup"><span data-stu-id="aa399-232">You can create a sequence that eliminates duplicate elements by calling [Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401).</span></span> <span data-ttu-id="aa399-233">也可以使用[Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75)，这需要对每个元素调用的键生成函数。</span><span class="sxs-lookup"><span data-stu-id="aa399-233">Or you can use [Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), which takes a key-generating function to be called on each element.</span></span> <span data-ttu-id="aa399-234">所产生的序列包含具有唯一键; 对原始序列的元素更高版本生成的更早版本的元素的重复键的元素将被丢弃。</span><span class="sxs-lookup"><span data-stu-id="aa399-234">The resulting sequence contains elements of the original sequence that have unique keys; later elements that produce a duplicate key to an earlier element are discarded.</span></span>

<span data-ttu-id="aa399-235">下面的代码示例演示如何使用`Seq.distinct`。</span><span class="sxs-lookup"><span data-stu-id="aa399-235">The following code example illustrates the use of `Seq.distinct`.</span></span> <span data-ttu-id="aa399-236">`Seq.distinct`通过生成表示二进制数字的序列，然后显示仅非重复元素为 0 和 1 演示了。</span><span class="sxs-lookup"><span data-stu-id="aa399-236">`Seq.distinct` is demonstrated by generating sequences that represent binary numbers, and then showing that the only distinct elements are 0 and 1.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet22.fs)]

<span data-ttu-id="aa399-237">下面的代码演示`Seq.distinctBy`通过启动包含正负数字的序列使用绝对值的数值函数作为键生成函数。</span><span class="sxs-lookup"><span data-stu-id="aa399-237">The following code demonstrates `Seq.distinctBy` by starting with a sequence that contains negative and positive numbers and using the absolute value function as the key-generating function.</span></span> <span data-ttu-id="aa399-238">所产生的序列缺少对应于序列中的负数字，因为负数出现在序列中提前但因此选择而不是具有相同的绝对正数的所有正数值值或密钥。</span><span class="sxs-lookup"><span data-stu-id="aa399-238">The resulting sequence is missing all the positive numbers that correspond to the negative numbers in the sequence, because the negative numbers appear earlier in the sequence and therefore are selected instead of the positive numbers that have the same absolute value, or key.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet23.fs)]
    
## <a name="readonly-and-cached-sequences"></a><span data-ttu-id="aa399-239">Readonly 和缓存的序列</span><span class="sxs-lookup"><span data-stu-id="aa399-239">Readonly and Cached Sequences</span></span>
<span data-ttu-id="aa399-240">[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7)创建的序列的只读副本。</span><span class="sxs-lookup"><span data-stu-id="aa399-240">[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) creates a read-only copy of a sequence.</span></span> <span data-ttu-id="aa399-241">`Seq.readonly`有一个读写的集合，如数组，并且你不想要修改原始集合时非常有用。</span><span class="sxs-lookup"><span data-stu-id="aa399-241">`Seq.readonly` is useful when you have a read-write collection, such as an array, and you do not want to modify the original collection.</span></span> <span data-ttu-id="aa399-242">此函数可用来保留数据封装。</span><span class="sxs-lookup"><span data-stu-id="aa399-242">This function can be used to preserve data encapsulation.</span></span> <span data-ttu-id="aa399-243">在下面的代码示例中，创建包含数组的类型。</span><span class="sxs-lookup"><span data-stu-id="aa399-243">In the following code example, a type that contains an array is created.</span></span> <span data-ttu-id="aa399-244">属性可公开数组，但而不是返回一个数组，它将返回一个序列，其中通过使用从该数组创建`Seq.readonly`。</span><span class="sxs-lookup"><span data-stu-id="aa399-244">A property exposes the array, but instead of returning an array, it returns a sequence that is created from the array by using `Seq.readonly`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet24.fs)]

<span data-ttu-id="aa399-245">[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0)创建一个序列的存储的版本。</span><span class="sxs-lookup"><span data-stu-id="aa399-245">[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) creates a stored version of a sequence.</span></span> <span data-ttu-id="aa399-246">使用`Seq.cache`以避免重新评估的序列，或如果你具有多个线程，使用一个序列，但你必须确保每个元素执行操作时只进行一次。</span><span class="sxs-lookup"><span data-stu-id="aa399-246">Use `Seq.cache` to avoid reevaluation of a sequence, or when you have multiple threads that use a sequence, but you must make sure that each element is acted upon only one time.</span></span> <span data-ttu-id="aa399-247">如果你正在使用多个线程的序列，你可以枚举并计算的原始序列的值的一个线程，并且剩余线程可以使用缓存的序列。</span><span class="sxs-lookup"><span data-stu-id="aa399-247">When you have a sequence that is being used by multiple threads, you can have one thread that enumerates and computes the values for the original sequence, and remaining threads can use the cached sequence.</span></span>


## <a name="performing-computations-on-sequences"></a><span data-ttu-id="aa399-248">对序列执行计算</span><span class="sxs-lookup"><span data-stu-id="aa399-248">Performing Computations on Sequences</span></span>
<span data-ttu-id="aa399-249">简单的算术运算是类似的列表，如[Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8)， [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a)， [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8)， [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)，依次类推。</span><span class="sxs-lookup"><span data-stu-id="aa399-249">Simple arithmetic operations are like those of lists, such as [Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1), and so on.</span></span>

<span data-ttu-id="aa399-250">[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3)， [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)，和[Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e)是否与可用于列出的相应函数类似。</span><span class="sxs-lookup"><span data-stu-id="aa399-250">[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), and [Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) are like the corresponding functions that are available for lists.</span></span> <span data-ttu-id="aa399-251">序列支持列出了支持的这些函数的完全变体的子集。</span><span class="sxs-lookup"><span data-stu-id="aa399-251">Sequences support a subset of the full variations of these functions that lists support.</span></span> <span data-ttu-id="aa399-252">有关详细信息和示例，请参阅[列出](lists.md)。</span><span class="sxs-lookup"><span data-stu-id="aa399-252">For more information and examples, see [Lists](lists.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa399-253">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa399-253">See Also</span></span>
[<span data-ttu-id="aa399-254">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="aa399-254">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="aa399-255">F# 类型</span><span class="sxs-lookup"><span data-stu-id="aa399-255">F# Types</span></span>](fsharp-types.md)