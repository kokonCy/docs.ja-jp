---
title: <param> - C# プログラミング ガイド
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: f9613a7373a829d2a52f3f56b8ea1ab35ebdcf5f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711728"
---
# <a name="param-c-programming-guide"></a>\<param> (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a>パラメーター  
 `name`  
 メソッド パラメーターの名前です。 名前は二重引用符 (" ") で囲みます。  
  
 `description`  
 パラメーターの説明です。  
  
## <a name="remarks"></a>Remarks  
 \<param> タグは、メソッドのいずれか 1 つのパラメーターを説明するためにメソッドの宣言のコメントで使用する必要があります。 複数のパラメーターをドキュメント化するには、複数の \<param> タグを使用します。  
  
 \<param> タグのテキストは、IntelliSense、オブジェクト ブラウザー、コード コメント Web レポートに表示されます。  
  
 コンパイル時に [-doc](../../language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ドキュメント コメントとして推奨されるタグ](./recommended-tags-for-documentation-comments.md)
