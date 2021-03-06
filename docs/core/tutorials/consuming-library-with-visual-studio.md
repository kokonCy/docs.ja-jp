---
title: Visual Studio での .NET Standard ライブラリの使用
description: Visual Studio 2019 を使用して別のクラス ライブラリのメンバーを呼び出す .NET Core アプリケーションを構築します。
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: ec9c6f992bcd4a76e2f70018f3facca42b7b660c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714067"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a>Visual Studio での .NET Standard ライブラリの使用

.NET Standard クラス ライブラリを作成してテストし、そのライブラリのリリース バージョンを構築したら、次のステップとして、それを呼び出し元が使用できるようにします。 これは次の 2 つの方法で実行できます。

- ライブラリが 1 つのソリューションで使われる場合 (たとえば、1 つの大規模なアプリケーションのコンポーネントである場合)、1 つのプロジェクトとしてソリューションに含めることができます。
- ライブラリが一般に公開される場合は、NuGet パッケージとして配布できます。

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
>
> - .NET Standard ライブラリ プロジェクトを参照するコンソール アプリをソリューションに追加します。
> - .NET Standard ライブラリ ロジェクトを含む NuGet パッケージを作成します。

## <a name="add-a-console-app-to-your-solution"></a>ソリューションにコンソール アプリを追加する

「[Visual Studio での .NET Standard ライブラリのテスト](testing-library-with-visual-studio.md)」で、単体テストをクラス ライブラリと同じソリューションに含めたのと同様に、アプリケーションをそのソリューションの一部として含めることができます。 たとえば、文字列を入力するようにユーザーに要求して、最初の文字が大文字かどうかを報告するコンソール アプリケーションで、このクラス ライブラリを使うことができます。

1. [Visual Studio での .NET Standard ライブラリの構築](library-with-visual-studio.md)に関する記事で作成した `ClassLibraryProjects` ソリューションを開きます。

1. "ShowCase" という名前の新しい .NET Core コンソール アプリケーションをソリューションに追加します。

   1. **ソリューション エクスプローラー**で、ソリューションを右クリックし、 **[追加]**  >  **[新しいプロジェクト]** の順に選択します。

   1. **[新しいプロジェクトの追加]** ページで、検索ボックスに「**コンソール**」と入力します。 言語の一覧から **[C#]** または **[Visual Basic]** を選択し、次に、プラットフォームの一覧から **[すべてのプラットフォーム]** を選択します。 **[コンソール アプリ (.NET Core)]** テンプレートを選択し、 **[次へ]** を選択します。

   1. **[新しいプロジェクトの構成]** ページで、 **[プロジェクト名]** ボックスに「**ShowCase**」と入力します。 次に、 **[作成]** を選択します。

1. **ソリューション エクスプローラー**で、**ShowCase** プロジェクトを右クリックして、コンテキスト メニューで **[スタートアップ プロジェクトに設定]** を選びます。

   ![スタートアップ プロジェクトを設定する Visual Studio プロジェクトのコンテキスト メニュー](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. 初期状態では、プロジェクトにはクラス ライブラリへのアクセス権がありません。 プロジェクトでクラス ライブラリのメソッドを呼び出すことができるようにするには、クラス ライブラリへの参照を作成します。 **ソリューション エクスプローラー**で、`ShowCase` プロジェクトの **[依存関係]** ノードを右クリックして、 **[参照の追加]** を選びます。

   ![Visual Studio の [参照の追加] コンテキスト メニュー](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. **[参照マネージャー]** ダイアログ ボックスで、クラス ライブラリ プロジェクト **StringLibrary** を選び、 **[OK]** ボタンを選びます。

   ![StringLibrary が選択された [参照マネージャー] ダイアログ](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. *Program.cs* または *Program.vb* ファイルのコード ウィンドウで、すべてのコードを次のコードに置き換えます。

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   このコードでは、`row` 変数を使って、コンソール ウィンドウに書き込まれるデータの行数のカウントを維持します。 これが 25 以上になると、コードによってコンソール ウィンドウがクリアされ、ユーザーにメッセージが表示されます。

   プログラムは、ユーザーに文字列の入力を要求し、 文字列が大文字で始まるかどうかを示します。 ユーザーが文字列を入力せずに Enter キーを押すと、アプリケーションが終了し、コンソール ウィンドウが閉じます。

1. 必要に応じて、ツールバーを変更して、`ShowCase` プロジェクトの**デバッグ** リリースをコンパイルします。 **ShowCase** の緑色の矢印を選び、プログラムをコンパイルして実行します。

   ![[デバッグ] ボタンを示している Visual Studio プロジェクトのツールバー](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

「[Visual Studio を使用して C# または Visual Basic .NET Core の Hello World アプリケーションをデバッグする](debugging-with-visual-studio.md)」および「[Visual Studio での .NET Core Hello World アプリケーションの発行](publishing-with-visual-studio.md)」の手順に従って、このライブラリを使うアプリケーションをデバッグして発行できます。

## <a name="create-a-nuget-package"></a>NuGet パッケージの作成

NuGet パッケージとして発行すると、クラス ライブラリが広く利用可能になります。 NuGet パッケージの作成は Visual Studio ではサポートされていません。 作成するには、.NET Core CLI コマンドを使用する必要があります。

1. コンソール ウィンドウが開きます。

   たとえば、Windows タスク バーの検索ボックスに「**コマンド プロンプト**」と入力します。 **[コマンド プロンプト]** デスクトップ アプリを選択するか、検索結果で既に選択されている場合は、**Enter** キーを押します。

1. ライブラリのプロジェクト ディレクトリに移動します。 このディレクトリには、ソース コードおよびプロジェクト ファイル *StringLibrary.csproj* または *StringLibrary.vbproj* が含まれています。

1. [dotnet pack](../tools/dotnet-pack.md) コマンドを実行して、 *.nupkg* 拡張子を持つパッケージを生成します。

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > *dotnet.exe* を含むディレクトリが PATH になくても、コンソール ウィンドウで「`where dotnet.exe`」と入力して、場所を検索できます。

NuGet パッケージの作成の詳細については、「[クロスプラットフォーム ツールを使用して NuGet パッケージを作成する方法](../deploying/creating-nuget-packages.md)」を参照してください。
