---
ms.date: 05/16/2020
description: Internet Explorer 11 を使用して Office アドインをテストします。
title: Internet Explorer 11 のテスト
localization_priority: Normal
ms.openlocfilehash: 697c87d90df9aa70a7b20da5cd4c91d4445fb850
ms.sourcegitcommit: 54e2892c0c26b9ad1e4dba8aba48fea39f853b6c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/18/2020
ms.locfileid: "44275949"
---
# <a name="test-your-office-add-in-using-internet-explorer-11"></a><span data-ttu-id="aedbb-103">Internet Explorer 11 を使用して Office アドインをテストする</span><span class="sxs-lookup"><span data-stu-id="aedbb-103">Test your Office Add-in using Internet Explorer 11</span></span>

<span data-ttu-id="aedbb-104">アドインの仕様によっては、以前のバージョンの Windows および Office をサポートすることを計画している場合があります。これには、Internet Explorer 11 でのテストが必要になります。</span><span class="sxs-lookup"><span data-stu-id="aedbb-104">Depending on the specifications of your add-in, you may plan to support older versions of Windows and Office, which require testing on Internet Explorer 11.</span></span> <span data-ttu-id="aedbb-105">これは、多くの場合、アドインを AppSource に提出する際に必要になります。</span><span class="sxs-lookup"><span data-stu-id="aedbb-105">This is often necessary as part of submitting your add-in to AppSource.</span></span> <span data-ttu-id="aedbb-106">このテストでは、次のコマンドラインツールを使用して、アドインで使用されるより新しいランタイムを Internet Explorer 11 ランタイムに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="aedbb-106">You can use the following command line tooling to switch from more modern runtimes used by add-ins to the Internet Explorer 11 runtime for this testing.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="aedbb-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="aedbb-107">Pre-requisites</span></span>

- <span data-ttu-id="aedbb-108">[Node.js](https://nodejs.org/) (最新 [LTS](https://nodejs.org/about/releases) バージョン)</span><span class="sxs-lookup"><span data-stu-id="aedbb-108">[Node.js](https://nodejs.org/) (the latest [LTS](https://nodejs.org/about/releases) version)</span></span>
- <span data-ttu-id="aedbb-109">コード エディター。</span><span class="sxs-lookup"><span data-stu-id="aedbb-109">A code editor.</span></span> <span data-ttu-id="aedbb-110">[Visual Studio コード](https://code.visualstudio.com/)をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="aedbb-110">We recommend [Visual Studio Code](https://code.visualstudio.com/)</span></span>
- [<span data-ttu-id="aedbb-111">Office Insider program の一部である</span><span class="sxs-lookup"><span data-stu-id="aedbb-111">Be part of the Office Insider program</span></span>](https://insider.office.com)

<span data-ttu-id="aedbb-112">これらの手順では、その前に Yo Office ジェネレータープロジェクトを設定していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="aedbb-112">These instructions assume you have set up a Yo Office generator project before.</span></span> <span data-ttu-id="aedbb-113">これを実行していない場合は、「 [Excel アドインの](../quickstarts/excel-quickstart-jquery.md)場合」などのクイックスタートを読むことを検討してください。</span><span class="sxs-lookup"><span data-stu-id="aedbb-113">If you haven't done this before, consider reading a quick start, such as [this one for Excel add-ins](../quickstarts/excel-quickstart-jquery.md).</span></span>

## <a name="using-ie11-tooling"></a><span data-ttu-id="aedbb-114">IE11 ツールを使用する</span><span class="sxs-lookup"><span data-stu-id="aedbb-114">Using IE11 tooling</span></span>

1. <span data-ttu-id="aedbb-115">Yo Office ジェネレータープロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="aedbb-115">Create a Yo Office generator project.</span></span> <span data-ttu-id="aedbb-116">選択するプロジェクトの種類に関係なく、このツールはすべてのプロジェクトの種類で機能します。</span><span class="sxs-lookup"><span data-stu-id="aedbb-116">It doesn't matter what kind of project you select, this tooling will work with all project types.</span></span>

> <span data-ttu-id="aedbb-117">!こと既存のプロジェクトがあり、新しいプロジェクトを作成せずにこのツールを追加する場合は、この手順をスキップして次の手順に進みます。</span><span class="sxs-lookup"><span data-stu-id="aedbb-117">![NOTE] If you have an existing project and want to add this tooling without creating a new project, skip this step and move to the next step.</span></span> 

2. <span data-ttu-id="aedbb-118">新しいプロジェクトのルートフォルダーで、コマンドラインで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="aedbb-118">In the root folder of your new project, run the following in the command line:</span></span>

```command&nbsp;line
office-add-dev-settings webview manifest.xml ie
```
<span data-ttu-id="aedbb-119">Web ビューの種類が IE に設定されていることを示すメモがコマンドラインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="aedbb-119">You should see a note in the command line that the web view type is now set to IE.</span></span>

> <span data-ttu-id="aedbb-120">!部このツールを使用する必要はありませんが、Internet Explorer 11 ランタイムに関連する問題の大部分をデバッグするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="aedbb-120">![TIP] It isn't necessary to use this tooling, but it should help debug the majority of issues related to the Internet Explorer 11 runtime.</span></span> <span data-ttu-id="aedbb-121">堅牢性を完全にするには、Windows 7 および Office 2013 のコピーがインストールされたコンピューターを使用してテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="aedbb-121">For complete robustness, you should test using a computer with a copy of Windows 7 and Office 2013 installed.</span></span>

## <a name="command-settings"></a><span data-ttu-id="aedbb-122">コマンドの設定</span><span class="sxs-lookup"><span data-stu-id="aedbb-122">Command settings</span></span>

<span data-ttu-id="aedbb-123">マニフェストパスが異なる場合は、次のようにコマンドでこれを指定します。</span><span class="sxs-lookup"><span data-stu-id="aedbb-123">Should you have a different manifest path, specify this in the command, as shown in the following:</span></span>

`office-add-dev-settings webview [path to your manifest] ie`

<span data-ttu-id="aedbb-124">また、このコマンドは、 `office-addin-dev-settings webview` 引数としていくつかのランタイムを取ることができます。</span><span class="sxs-lookup"><span data-stu-id="aedbb-124">The `office-addin-dev-settings webview` command can also take a number of runtimes as arguments:</span></span>

- <span data-ttu-id="aedbb-125">internet</span><span class="sxs-lookup"><span data-stu-id="aedbb-125">ie</span></span>
- <span data-ttu-id="aedbb-126">下辺</span><span class="sxs-lookup"><span data-stu-id="aedbb-126">edge</span></span>
- <span data-ttu-id="aedbb-127">既定値です。</span><span class="sxs-lookup"><span data-stu-id="aedbb-127">default</span></span>

## <a name="see-also"></a><span data-ttu-id="aedbb-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="aedbb-128">See also</span></span>
* [<span data-ttu-id="aedbb-129">Office アドインのテストとデバッグ</span><span class="sxs-lookup"><span data-stu-id="aedbb-129">Test and debug Office Add-ins</span></span>](test-debug-office-add-ins.md)
* [<span data-ttu-id="aedbb-130">テスト用に Office アドインをサイドロードする</span><span class="sxs-lookup"><span data-stu-id="aedbb-130">Sideload Office Add-ins for testing</span></span>](create-a-network-shared-folder-catalog-for-task-pane-and-content-add-ins.md)
* [<span data-ttu-id="aedbb-131">Windows 10 で開発者ツールを使用してアドインをデバッグする</span><span class="sxs-lookup"><span data-stu-id="aedbb-131">Debug add-ins using developer tools on Windows 10</span></span>](debug-add-ins-using-f12-developer-tools-on-windows-10.md)
* [<span data-ttu-id="aedbb-132">作業ウィンドウからデバッガーをアタッチする</span><span class="sxs-lookup"><span data-stu-id="aedbb-132">Attach a debugger from the task pane</span></span>](attach-debugger-from-task-pane.md)