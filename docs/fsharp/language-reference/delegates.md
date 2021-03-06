---
title: デリゲート
description: でF#デリゲートを使用する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 65875897d5fc4b2ac66f1dfbe913f29fb74137cd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630372"
---
# <a name="delegates"></a>デリゲート

デリゲートは、関数呼び出しをオブジェクトとして表します。 でF#は、関数を最初のクラスの値として表すために、通常は関数の値を使用する必要があります。ただし、デリゲートは .NET Framework で使用されるため、想定される Api と相互運用するときに必要になります。 また、他の .NET Framework 言語から使用できるように設計されたライブラリを作成するときにも使用できます。

## <a name="syntax"></a>構文

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>Remarks

前の構文では`type1` 、は引数の型または`type2`型を表し、戻り値の型を表します。 によって`type1`表される引数の型は、自動的にカリー化されます。 これにより、この型では、対象の関数の引数がカリー化されている場合は組形式を使用し、既にタプル形式の引数にはかっこで囲まれたタプルを使用することが推奨されます。 自動カリー化は、対象のメソッドに一致するタプル引数を残して、一連のかっこを削除します。 各ケースで使用する構文については、コード例を参照してください。

デリゲートは、F# 関数値、および静的に接続できるまたはインスタンス メソッド。 デリゲート コンストラクターに引数として直接 F# 関数値を渡すことができます。 静的メソッドの場合は、クラスの名前とメソッドを使用してデリゲートを構築します。 インスタンスメソッドの場合は、1つの引数にオブジェクトのインスタンスとメソッドを指定します。 どちらの場合も、メンバーアクセス演算子 (`.`) が使用されます。

デリゲート`Invoke`型のメソッドは、カプセル化された関数を呼び出します。 また、デリゲートを関数値として渡すには、呼び出しメソッド名をかっこで囲んで参照します。

次のコードは、クラス内のさまざまなメソッドを表すデリゲートを作成するための構文を示しています。 メソッドが静的メソッドとインスタンスメソッドのどちらであるか、また、タプル形式またはカリー化形式の引数があるかどうかによって、デリゲートの宣言と割り当ての構文は少し異なります。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

次のコードは、デリゲートを操作するためのさまざまな方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

前のコード例の出力は次のようになります。

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [パラメーターと引数](parameters-and-arguments.md)
- [イベント](./members/events.md)
