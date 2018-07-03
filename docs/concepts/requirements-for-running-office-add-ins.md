---
title: Office アドインを実行するための要件
description: ''
ms.date: 02/09/2018
ms.openlocfilehash: 944ac0c26b864124a8c86b46e023609120d8ea75
ms.sourcegitcommit: 3e4e3a45a07ed91176cab182c44184c196c23d35
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "20159678"
---
# <a name="requirements-for-running-office-add-ins"></a>Office アドインを実行するための要件

この記事では、Office アドインを実行するためのソフトウェアとデバイスの要件について説明します。

> [!NOTE]
> AppSource にアドインを[公開](../publish/publish.md)し、Office エクスペリエンスで利用できるようにする予定がある場合は、[AppSource の検証ポリシー](https://docs.microsoft.com/en-us/office/dev/store/validation-policies)に準拠していることを確認してください。たとえば、検証に合格するには、定義したメソッドをサポートするすべてのプラットフォームでアドインが動作する必要があります (詳細については、[セクション 4.12](https://docs.microsoft.com/en-us/office/dev/store/validation-policies#4-apps-and-add-ins-behave-predictably) と [Office アドインを使用できるホストおよびプラットフォーム](../overview/office-add-in-availability.md)のページを参照してください)。 

現時点での Office アドインのサポート状況について、概要は「[Office アドインを使用できるホストおよびプラットフォーム](../overview/office-add-in-availability.md)」を参照してください。

## <a name="server-requirements"></a>サーバーの要件

Office アドインをインストールおよび実行できるようにするには、まずアドインの UI とコードのマニフェストと Web ページ ファイルを、適切なサーバーの場所に展開する必要があります。

すべての種類のアドイン (コンテンツ、Outlook、作業ウィンドウの、アドインとアドイン コマンド) で、アドインの Web ページ ファイルを Web サーバーや [Microsoft Azure](../publish/host-an-office-add-in-on-microsoft-azure.md) などの Web ホスティング サービスに展開する必要があります。

[!include[HTTPS guidance](../includes/https-guidance.md)]

> [!TIP]
> Visual Studio でアドインを開発およびデバッグする際、Visual Studio は IIS Express を使用してアドインの Web ページ ファイルをローカルで展開および実行するので、追加の Web サーバーは必要ありません。 

サポートされている Office ホスト アプリケーション (Access Web アプリ、Word、Excel、PowerPoint、または Project) のコンテンツ アドインと作業ウィンドウ アドインでは、アドインの XML マニフェスト ファイルをアップロードするために、SharePoint の [アドイン カタログ](../publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog.md)も必要になります。

Outlook アドインをテストおよび実行するには、ユーザーの Outlook 電子メール アカウントが、Office 365、Exchange Online、またはオンプレミスのインストールから使用できる Exchange 2013 以降のバージョン上に存在する必要があります。ユーザーまたは管理者は、サーバー上に Outlook アドインのマニフェスト ファイルをインストールします。

> [!NOTE]
> Outlook の POP および IMAP 電子メール アカウントは、Office アドインをサポートしていません。

## <a name="client-requirements-windows-desktop-and-tablet"></a>クライアントの要件: Windows デスクトップおよびタブレット

Windows ベースのデスクトップ、ノート PC、または タブレット デバイス上で実行されるサポート対象の Office デスクトップ クライアントまたは Web クライアント向けの Office アドインを開発するには、以下のソフトウェアが必要です。


- Windows x86 および x64 デスクトップおよび Surface Pro などのタブレット:
    - Windows 7 以降のバージョンで実行している Office 2013 以降のバージョンの、32 ビットまたは 64 ビット バージョン。
    - Excel 2013、Outlook 2013、PowerPoint 2013、Project Professional 2013、Project 2013 SP1、Word 2013、またはそれ以降の Office クライアントのバージョン (特にこれらの Office デスクトップ クライアントを対象として Office アドインをテストまたは実行する場合)。Office デスクトップ クライアントはオンプレミスでインストールすることも、クイック実行によってクライアント コンピューターにインストールすることもできます。
    
  有効な Office 365 サブスクリプションがあり、Office 2013 へのアクセス権がない場合は、次の CDN リンクのいずれかからダウンロードすることができます。       
    - [Office 2013 for Business (.exe)](https://c2rsetup.officeapps.live.com/c2r/download.aspx?productReleaseID=O365BusinessRetail&platform=X86&language=en-us&version=O15GA&source=O15OLSO365) 
    - [Office 2013 for Home (.exe)](https://c2rsetup.officeapps.live.com/c2r/download.aspx?productReleaseID=O365HomePremRetail&platform=X86&language=en-us&version=O15GA&source=O15OLSO365) 

- Internet Explorer 11 以降をインストールする必要がありますが、必ずしも既定のブラウザーにする必要はありません。Office アドインをサポートするために、ホストとして動作する Office のクライアントは、Internet Explorer 11 以降に組み込まれているブラウザー コンポーネントを使用します。

  > [!NOTE]
  > Office Web アドインが機能するには、Internet Explorer のセキュリティ強化の構成 (ESC) を無効にする必要があります。 アドインの開発時に Windows Server コンピュータをクライアントとして使用している場合、Windows Server では既定値で ESC がオンになっていることに注意してください。

- 既定のブラウザーとして次のいずれか:Internet Explorer 11 以降、Microsoft Edge、Chrome、Firefox、Safari (Mac OS) の最新バージョンのうちいずれか。
- メモ帳などの HTML および JavaScript エディター、[Visual Studio および Microsoft Developer Tools](https://www.visualstudio.com/features/office-tools-vs)、またはサードパーティの Web 開発ツール。

## <a name="client-requirements-os-x-desktop"></a>クライアントの要件: OS X デスクトップ

Outlook for Mac は Office 365 に付属していて、Outlook アドインをサポートします。Outlook アドインを Outlook for Mac で実行するための要件は、Outlook for Mac そのものの要件と同じです。オペレーティング システムは、少なくとも OS X v10.10 "Yosemite" である必要があります。Outlook for Mac はレイアウト エンジンとして WebKit を使用して、アドイン ページを表示するので、追加のブラウザーの依存関係はありません。

次は、Office アドインをサポートする Office for Mac の最小クライアント バージョンです。

- Word for Mac バージョン 15.18 (160109) 
- Excel for Mac バージョン 15.19 (160206) 
- PowerPoint for Mac バージョン 15.24 (160614)

## <a name="client-requirements-browser-support-for-office-online-web-clients-and-sharepoint"></a>クライアントの要件: Office Online Web クライアントと SharePoint のブラウザー サポート

Internet Explorer 11 以降、Microsoft Edge、Chrome、Firefox、Safari (Mac OS) の最新バージョンなど ECMAScript 5.1、HTML5、および CSS3 をサポートする任意のブラウザー。


## <a name="client-requirements-non-windows-smartphone-and-tablet"></a>クライアントの要件: Windows 以外のスマートフォンおよびタブレット

特に、スマートフォンや Windows 以外のタブレット デバイス上のブラウザーで動作する デバイス用 OWA と Outlook Web App の場合、Outlook アドインをテストおよび実行するのに以下のソフトウェアが必要です。


| ホスト アプリケーション | デバイス | オペレーティング システム | Exchange アカウント | モバイル ブラウザー |
|:-----|:-----|:-----|:-----|:-----|
|OWA for Android|Android スマートフォン。技術的には、「 [Android OS](https://developer.android.com/guide/practices/screens_support.html)」によって「小型」または「標準」に分類されるデバイス。|Android 4.4 KitKat 以降|Office 365 for Business または Exchange Online の最新の更新プログラムが対象|Android 用のネイティブ アドイン、ブラウザーは適用外|
|OWA for iPad|iPad 2 以降|iOS 6 以降|Office 365 for Business または Exchange Online の最新の更新プログラムが対象|iOS 用のネイティブ アドイン、ブラウザーは適用外|
|OWA for iPhone|iPhone 4S 以降|iOS 6 以降|Office 365 for Business または Exchange Online の最新の更新プログラムが対象|iOS 用のネイティブ アドイン、ブラウザーは適用外|
|Outlook Web アプリ|iPhone 4 以降、iPad 2 以降、iPod Touch 4 以降|iOS 5 以降|Office 365、Exchange Online、または Exchange Server 2013 以降の社内型が対象|Safari|


## <a name="see-also"></a>関連項目

- [Office アドイン プラットフォームの概要](../overview/office-add-ins.md)
- [Office アドインを使用できるホストおよびプラットフォーム](../overview/office-add-in-availability.md)