---
title: XML ドキュメント コメント - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.xml
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
ms.openlocfilehash: 85d75d6420404f278c4a8b16eb9bf30aff958f7c
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645780"
---
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="abe48-102">XML ドキュメント コメント (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="abe48-102">XML Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="abe48-103">Visual C# では、ソース コード内で、コード ブロックの直前の特別なコメント フィールド (3 個のスラッシュで示す) に XML 要素を配置することで、コードのドキュメントを作成できます。例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="abe48-103">In Visual C# you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example:</span></span>  
  
```csharp  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass {}  
```  
  
 <span data-ttu-id="abe48-104">[/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) オプションを使用してコンパイルすると、コンパイラは、ソース コード内のすべての XML タグを検索して、XML ドキュメント ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="abe48-104">When you compile with the [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="abe48-105">コンパイラによって生成されたファイルに基づいて最終的なドキュメントを作成するには、カスタム ツールを作成するか、[DocFX](https://dotnet.github.io/docfx/) や [Sandcastle](https://github.com/EWSoftware/SHFB) などのツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="abe48-105">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="abe48-106">XML 要素を参照するには (たとえば、XML ドキュメント コメントに記述する特定の XML 要素を関数で処理する場合)、標準の引用のしくみを使用できます (`<` と `>`)。</span><span class="sxs-lookup"><span data-stu-id="abe48-106">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="abe48-107">コード参照 (`cref`) 要素でジェネリック識別子を参照するには、エスケープ文字 (たとえば、`cref="List&lt;T&gt;"`) または中かっこ (`cref="List{T}"`) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="abe48-107">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="abe48-108">特殊なケースとして、コンパイラは中かっこを山かっことして解析し、ジェネリック識別子を参照するときにドキュメント コメントの編集があまり面倒にならないようにしています。</span><span class="sxs-lookup"><span data-stu-id="abe48-108">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abe48-109">XML ドキュメント コメントはメタデータではなく、コンパイルされたアセンブリに含まれないため、リフレクションでアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="abe48-109">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="abe48-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="abe48-110">In This Section</span></span>  
  
- [<span data-ttu-id="abe48-111">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="abe48-111">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
- [<span data-ttu-id="abe48-112">XML ファイルの処理</span><span class="sxs-lookup"><span data-stu-id="abe48-112">Processing the XML File</span></span>](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
- [<span data-ttu-id="abe48-113">ドキュメント タグの区切り記号</span><span class="sxs-lookup"><span data-stu-id="abe48-113">Delimiters for Documentation Tags</span></span>](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
- [<span data-ttu-id="abe48-114">方法: XML ドキュメント機能を使用する</span><span class="sxs-lookup"><span data-stu-id="abe48-114">How to: Use the XML Documentation Features</span></span>](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a><span data-ttu-id="abe48-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="abe48-115">Related Sections</span></span>  
 <span data-ttu-id="abe48-116">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="abe48-116">For more information, see:</span></span>  
  
- [<span data-ttu-id="abe48-117">/doc (ドキュメント コメントの処理)</span><span class="sxs-lookup"><span data-stu-id="abe48-117">/doc (Process Documentation Comments)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="abe48-118">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="abe48-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="abe48-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="abe48-119">See also</span></span>

- [<span data-ttu-id="abe48-120">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="abe48-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)