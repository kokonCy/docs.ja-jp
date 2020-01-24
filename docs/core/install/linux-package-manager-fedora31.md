---
title: Fedora 31 に .NET Core をインストールする - パッケージ マネージャー - .NET Core
description: パッケージ マネージャーを使用して、.NET Core SDK とランタイムを Fedora 31 にインストールします。
author: thraka
ms.author: adegeo
ms.date: 12/17/2019
ms.openlocfilehash: 25c670694ed2d9e89fe37cedf0b06efd8bc93293
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116952"
---
# <a name="fedora-31-package-manager---install-net-core"></a><span data-ttu-id="262c1-103">Fedora 31 パッケージ マネージャー - .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="262c1-103">Fedora 31 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="262c1-104">この記事では、パッケージ マネージャーを使用して Fedora 31 に .NET Core をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="262c1-104">This article describes how to use a package manager to install .NET Core on Fedora 31.</span></span> <span data-ttu-id="262c1-105">ランタイムをインストールする場合は、[ASP.NET Core ランタイム](#install-the-aspnet-core-runtime)をインストールすることをお勧めします。これには、.NET Core ランタイムと ASP.NET Core ランタイムの両方が含まれているためです。</span><span class="sxs-lookup"><span data-stu-id="262c1-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="262c1-106">Microsoft キーとフィードを登録する</span><span class="sxs-lookup"><span data-stu-id="262c1-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="262c1-107">.NET をインストールする前に、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="262c1-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="262c1-108">Microsoft キーを登録する。</span><span class="sxs-lookup"><span data-stu-id="262c1-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="262c1-109">製品リポジトリを登録する。</span><span class="sxs-lookup"><span data-stu-id="262c1-109">Register the product repository.</span></span>
- <span data-ttu-id="262c1-110">必要な依存関係をインストールする。</span><span class="sxs-lookup"><span data-stu-id="262c1-110">Install required dependencies.</span></span>

<span data-ttu-id="262c1-111">これは、コンピューターごとに 1 回実行する必要があるだけです。</span><span class="sxs-lookup"><span data-stu-id="262c1-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="262c1-112">ターミナルを開き、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="262c1-112">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="262c1-113">.NET Core SDK をインストールする</span><span class="sxs-lookup"><span data-stu-id="262c1-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="262c1-114">インストール可能な製品を更新してから、.NET Core SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="262c1-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="262c1-115">ご利用のターミナルで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="262c1-115">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="262c1-116">ASP.NET Core ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="262c1-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="262c1-117">インストール可能な製品を更新してから、ASP.NET ランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="262c1-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="262c1-118">ご利用のターミナルで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="262c1-118">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="262c1-119">.NET Core ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="262c1-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="262c1-120">インストール可能な製品を更新してから、.NET Core ランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="262c1-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="262c1-121">ご利用のターミナルで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="262c1-121">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="262c1-122">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="262c1-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]