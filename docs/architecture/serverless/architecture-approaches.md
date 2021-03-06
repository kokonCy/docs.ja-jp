---
title: アーキテクチャ アプローチ - サーバーレス アプリ
description: N 層アーキテクチャからサーバーレスへ、クラウドベースのエンタープライズ アプリケーションを構築するためのアーキテクチャのアプローチについて説明します。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522901"
---
# <a name="architecture-approaches"></a>アーキテクチャのアプローチ

エンタープライズ アプリを設計するための既存のアプローチを理解することは、サーバーレスが果たす役割を明らかにするのに役立ちます。 数十年にわたるソフトウェア開発で進化した多くのアプローチとパターンがあり、それぞれに固有の長所と短所があります。 多くの場合、最終的な解決策は 1 つのアプローチに決定することではなく、複数のアプローチを統合することです。 移行シナリオでは、ハイブリッド アプローチを使用して 1 つのアーキテクチャ アプローチから別のアプローチに切り替えることがよくあります。

この章では、エンタープライズ アプリケーションの論理アーキテクチャと物理アーキテクチャの両方の概要について説明します。

## <a name="architecture-patterns"></a>アーキテクチャのパターン

最新のビジネス アプリケーションは、さまざまなアーキテクチャ パターンに従います。 このセクションでは、一般的なパターンの調査について説明します。 ここに記載されているパターンは、必ずしもすべてがベスト プラクティスではありませんが、さまざまなアプローチを示しています。

詳細については、「[Azure アプリケーション アーキテクチャ ガイド](https://docs.microsoft.com/azure/architecture/guide/)」を参照してください。

## <a name="monoliths"></a>モノリス

多くのビジネス アプリケーションは、モノリス パターンに従います。 レガシ アプリケーションは、多くの場合、モノリスとして実装されています。 モノリス パターンでは、すべてのアプリケーションの問題が単一の展開に含まれています。 ユーザー インターフェイスからデータベースの呼び出しまで、すべてが同じコードベースに含まれています。

![モノリス アーキテクチャ](./media/monolith-architecture.png)

モノリス アプローチにはいくつかの利点があります。 多くの場合、単一のコード ベースを開いて作業を開始するのは簡単です。 準備期間は短くなる可能性があり、テスト環境の作成は新しいコピーを提供するのと同じように簡単です。 モノリスは、複数のコンポーネントとアプリケーションを含むように設計されている場合があります。

残念ながら、モノリス パターンは大規模に破綻する傾向があります。 モノリス アプローチの主な欠点は次のとおりです。

- 同じコード ベースで並行して作業することは困難です。
- 変更を行った場合、どれだけ些細な変更であったとしても、アプリケーション全体の新しいバージョンを展開する必要があります。
- リファクタリングを行うと、アプリケーション全体に影響を及ぼす可能性があります。
- 多くの場合、スケーリングするための唯一の解決策は、リソースを大量に消費するモノリスの複数のコピーを作成することです。
- システムの拡大や他のシステムの獲得に伴い、統合が困難な場合があります。
- モノリス全体を構成する必要があるため、テストが困難な場合があります。
- コードを再利用することは容易でなく、他のアプリで独自のコードのコピーが作成されることがよくあります。

多くの企業は、モノリス アプリケーションを移行すると同時にもっと使いやすいパターンにリファクタリングする機会として、クラウドに注目しています。 個々のアプリケーションとコンポーネントを分割して個別に管理、展開、およびスケーリングできるようにするのが一般的です。

## <a name="n-layer-applications"></a>N 層アプリケーション

N 層アプリケーションでは、アプリケーション ロジックを特定のレイヤーに分割します。 最も一般的なレイヤーは次のとおりです。

- ユーザー インターフェイス
- ビジネス ロジック
- データ アクセス

その他のレイヤーには、ミドルウェア、バッチ処理、API などがあります。 重要なこととして、レイヤーは論理的なものである点に注意してください。 これらは分離して開発されますが、すべて同じターゲット プラットフォームに展開される可能性があります。

![N 層アーキテクチャ](./media/n-layer-architecture.png)

N 層アプローチには、次のようないくつかの利点があります。

- リファクタリングはレイヤーに分離されます。
- チームは別々のレイヤーを個別にビルド、テスト、展開、維持できます。
- レイヤーをスワップ アウトすることができます。たとえばデータ レイヤーから、UI レイヤーを変更することなく複数のデータベースにアクセスできます。

サーバーレスを使用して 1 つまたは複数のレイヤーを実装できます。

## <a name="microservices"></a>マイクロサービス

**[マイクロサービス](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** アーキテクチャには、次のような一般的な特性があります。

- アプリケーションは複数の小さいサービスで構成されています。
- 各サービスは独自のプロセスで実行されます。
- サービスはビジネス ドメインに合わせて調整されます。
- サービス間の通信は軽量の API を介して行われ、通常はトランスポートとして HTTP が使用されます。
- サービスは個別に展開およびアップグレードできます。
- サービスは 1 つのデータ ストアに依存していません。
- システムはエラーを考慮して設計されており、特定のサービスにエラーが発生した場合でもアプリを実行できます。

マイクロサービスは、他のアーキテクチャ アプローチと相互に排他的である必要はありません。 たとえば、N 層アーキテクチャでは、中間層にマイクロサービスを使用できます。 また、IIS ホスト上の仮想ディレクトリからコンテナーまで、さまざまな方法でマイクロサービスを実装することが可能です。 マイクロサービスの特性は、サーバーレス実装に特に適しています。

![マイクロサービス アーキテクチャ](./media/microservices-architecture.png)

マイクロサービス アーキテクチャの長所は次のとおりです。

- リファクタリングは、多くの場合、1 つのサービスに分離されます。
- サービスは互いに独立してアップグレードできます。
- 回復性と弾力性は、個々のサービスの需要に合わせて調整できます。
- 開発は、異なるチームやプラットフォーム間で並行して行うことができます。
- 分離されたサービスの包括的なテストを作成する方が簡単です。

マイクロサービスには、次のような固有の課題があります。

- 使用可能なサービスとその呼び出し方法の決定。
- サービスのライフサイクルの管理。
- サービスがアプリケーション全体にどのように適合するかの理解。
- 異なるサービス間で行われる呼び出しの完全なシステム テスト。

最終的には、これらすべての課題に対処するための解決策があります。これには、後で説明するサーバーレスの利点を活用することが含まれます。

>[!div class="step-by-step"]
>[前へ](index.md)
>[次へ](architecture-deployment-approaches.md)
