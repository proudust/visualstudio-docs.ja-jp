---
title: Web サイトに発行する
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec5ea0b52c5d0708630a30b7d2b80be2275f3a9
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173693"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Visual Studio を使用して Web サイトに Web アプリを発行する

Visual Studio から Web サイトに ASP.NET、ASP.NET Core、.NET Core、および Python アプリを発行するには、 **[発行]** ツールを使用します。 Node.js では、この手順はサポートされていますが、ユーザー インターフェイスが異なります。

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> ネットワーク ファイル共有に Windows デスクトップ アプリケーションを発行する必要がある場合、[ClickOnce を使用したデスクトップ アプリの配置](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)に関するページ (C# または Visual Basic) を参照してください。 C++/CLR については、[ClickOnce を使用したネイティブ アプリの配置](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)に関するページを、C/C++ については、[セットアップ プロジェクトを使用したネイティブ アプリの配置](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)に関するページを参照してください。

## <a name="publish-to-a-web-site"></a>Web サイトに発行する

1. ソリューション エクスプローラーで、プロジェクトを右クリックして、 **[発行]** を選択します (または **[ビルド]**  >  **[発行]** メニュー項目を使用します)。

    ![ソリューション エクスプローラーのプロジェクト コンテキスト メニューにある [発行] コマンド](../deployment/media/quickstart-publish.png "[発行] を選択する")

1. 以前に発行プロファイルを構成してある場合、 **[発行]** ウィンドウが表示されます。 **[新しいプロファイルの作成]** を選択します。

1. **[発行]** ダイアログ ボックスで、 **[Web サーバー (IIS)]** を選択します。

    ![発行先を選択する](../deployment/media/quickstart-publish-iis.png "IIS や FTP などを選択します。")

1. デプロイ方法として **[Web 配置]** を選択します。 Web 配置を使用すると、Web アプリケーションと Web サイトを IIS サーバーの配置が簡単になります。Web 配置はアプリケーションとしてサーバーにインストールする必要があります。 インストールには [Web プラットフォーム インストーラー](https://www.microsoft.com/web/downloads/platform.aspx)を使用します。

    ![デプロイ方法を選択する](../deployment/media/quickstart-publish-iis-web-deploy.png "IIS や FTP などを選択します。")

1. 発行方法に必要な設定を構成し、 **[完了]** を選択します。 

    ![Web 配置接続の詳細](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. 発行するには、概要ページで **[発行]** を選択します。 [出力] ウィンドウに配置の進行状況と結果が表示されます。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Visual Studio を使用して発行プロファイルを作成する方法を学習しました。 発行設定をインポートして、発行プロファイルを構成することもできます。

> [!div class="nextstepaction"]
> [発行設定のインポートと IIS へのデプロイ](tutorial-import-publish-settings-iis.md)
