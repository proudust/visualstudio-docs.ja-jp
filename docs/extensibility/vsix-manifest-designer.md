---
title: VSIX マニフェスト デザイナー |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30620e0fe91d0e90995d2d2f721950f878c65fdc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697892"
---
# <a name="vsix-manifest-designer"></a>VSIX マニフェスト デザイナー
Visual Studio 拡張機能のインストール動作を設定する VSIX パッケージ マニフェスト ファイルを変更します。

 **VSIX マニフェスト デザイナー**は、基になる VSIX スキーマにマップされます。 スキーマ内のすべての要素は、デザイナーで対応するコントロールを使用して設定できます。 スキーマの詳細については、「 [VSIX 拡張スキーマ 2.0 リファレンス](../extensibility/vsix-extension-schema-2-0-reference.md)」を参照してください。

 **VSIX マニフェスト デザイナー**を開くには、ソリューション**エクスプローラー**で*source.extension.vsixmanifest*ファイルを見つけて、ファイルを開きます。 ファイルに有効な XML が含まれていない場合、マニフェスト デザイナーは開きません。

> [!NOTE]
> パッケージがビルドされると *、source.extension.vsixmanifest*ファイルが*拡張子.vsixmanifest*に出力されます。

## <a name="uielement-list"></a>UIElement の一覧
 **VSIX マニフェスト デザイナー**には、スキーマの次の最上位要素に対応する 4 つのセクションが含まれています。

- Metadata

- ターゲットのインストール

- アセット

- 依存関係

  見出し領域には、次のコントロールが含まれています。

  **製品名**拡張機能の名前を記述します。

  **製品 ID**このパッケージの固有の ID 情報を指定します。

  **著者**拡張機能の作成者の名前を指定します。

  **バージョン**拡張機能のバージョン番号を指定します。

  [**メタデータ**] タブには、次のコントロールがあります。

  **説明****拡張機能マネージャー**に表示される拡張機能の説明を提供します。

  **言語**マニフェストのテキスト データに対応するパッケージの既定の言語を指定します。 この`Language`属性は、リソース アセンブリの共通言語ランタイム (CLR) のロケール コード規則に従います。 既定では、この値はニュートラルで、パッケージは任意の言語バージョンの Visual Studio で実行されます。

  **ライセンス**ユーザー ライセンスが存在する場合は、そのユーザー ライセンスを含むテキスト ファイルを指定します。

  **アイコン****拡張マネージャ**に表示されるアイコンが存在する場合は、.png、.bmp、.jpeg、.ico などのグラフィック ファイルを指定します。*.png* *.bmp* *.jpeg* *.ico* アイコン イメージは 32 x 32 ピクセルにする必要があります。 アイコンが指定されていない場合、**拡張機能マネージャー**は既定のアイコンを使用します。

  **プレビュー画像**プレビュー イメージが存在する場合は、**拡張機能マネージャー**に表示されるプレビュー イメージを含むグラフィックス ファイル (*.png*、 *.bmp*、 *.jpeg*、 *.ico*) を指定します。 プレビューイメージは 200x200 ピクセルである必要があります。 プレビュー イメージが指定されていない場合、**拡張機能マネージャー**は既定のイメージを使用します。

  **タグ**検索ヒントに使用するテキスト タグを追加します。

  **リリースノート**リリース ノートを含むファイル (*.txt*, *.rtf*) を指定します。 また、リリース ノートが表示される Web サイトの URL を取得します。

  **はじめにガイド**拡張子または VSIX パッケージのコンテンツの使用方法に関する情報を含むファイル (*.txt*、 *.rtf*) を指定します。 このガイドは、拡張機能のインストールが完了すると表示されます。 また、ガイドを表示する Web サイトの URL を取ります。

  **詳細情報の URL**製品に関する追加情報を含む Web サイトの URL を指定します。

  [**ターゲットのインストール**] タブには、次のコントロールがあります。

  **インストールの種類**ターゲット インストールの種類として**Visual Studio 拡張機能**と拡張**SDK**を一覧表示します。 オプションは、選択するタイプによって異なります。

  **ビジュアル スタジオ拡張機能**パッケージのインストール方法と、この拡張機能をインストールできる Visual Studio 製品を記述する**InstallationTarget**要素を一覧表示します。 各製品は、名前とバージョンまたはバージョン範囲によって個別に識別されます。 製品は、リストに追加、変更、削除できます。 製品の名前とバージョンは、関連付けられた**InstallationTarget**要素の**Id**属性と**バージョン**属性に対応します。

  **バージョン範囲**は[12.0,14.0]で、次の表記法を使用します。

- [ - 最小バージョンを含む

- ] - 最大バージョン (含む)

- ( - 最小バージョン限定

- ) - 最大バージョン限定

- 単一バージョン # - 指定されたバージョンのみ

  **拡張 SDK**特定の製品とバージョンを対象としないグローバル インストールを指定します。 **ターゲット プラットフォーム識別子**は、対象とするプラットフォーム ("Windows" など) です。 **ターゲット プラットフォームバージョン**は、ターゲット プラットフォームのバージョン (8.0 など) です。 **SDK 名**と**SDK バージョン**は、それぞれ SDK の名前とバージョン番号です。

  **この VSIX はすべてのユーザーにインストールされます (インストール時に昇格が必要です)** このチェック ボックスをオンにすると、すべてのユーザーに対して拡張機能がインストールされます。それ以外の場合は、現在のユーザーに対してのみインストールされます。

  **この VSIX は Windows インストーラによってインストールされます。** このチェック ボックスをオンにすると、Windows インストーラ *(.msi*ファイル) によって拡張機能がインストールされます。それ以外の場合は、一般的な VSIX パッケージ *(.vsix*ファイル) としてインストールされます。

  [**資産]** タブには、次のコントロールがあります。

  **資産一覧**このパッケージが表面化する拡張要素またはコンテンツ要素を記述する Asset 要素を一覧表示します。 各拡張機能またはコンテンツ要素は、ソース、種類、およびパスごとに個別にリストされます。 拡張機能とコンテンツ要素は、リストに追加、変更、および削除できます。 拡張要素またはコンテンツ要素の型とパスは、関連付けられた`Type``Asset`要素`Path`の 属性および 属性に対応します。 次の種類が知られています。

- パッケージ

- Microsoft.VisualStudio.MefComponent

- ツールボックスコントロール

- サンプル

- テンプレート

- 項目テンプレート

- アセンブリ

- マイクロソフトエクステンションSDK

  アセットを追加または編集するには、アセットタイプ、アセットが現在のソリューションのプロジェクトかファイル システムのファイルか、プロジェクトの名前を指定する必要があります。 埋め込まれるフォルダの名前を指定することもできます。

  独自の型を作成し、一意の名前を付けることもできます。

  [**依存関係**] タブには、次のコントロールがあります。

  **名前、ソース、バージョンの範囲**このパッケージの依存関係要素 (このパッケージが依存するその他のパッケージ) を一覧表示します。 依存関係パッケージを指定する場合は、このパッケージをインストールする前にインストールする必要があります。それ以外の場合は、このパッケージをインストールする必要があります。

  依存関係パッケージは、識別子、名前、バージョン範囲、ソース、および依存関係の解決方法によって指定されます。 各依存関係パッケージは、名前、バージョン、およびソース別に個別にリストされます。 依存関係パッケージは、リストに追加、変更、および削除できます。

  識別子は、依存関係パッケージ`ID`メタデータの属性と一致する必要があります。 ソースは、現在のソリューション内のプロジェクト、現在インストールされている拡張機能、またはファイルです。 **依存関係解決方法**設定は、入れ子になったパッケージの相対パス、または依存関係のダウンロード場所の URL です。 依存関係パッケージの ID、バージョン、および解決は、`Id`関連付けられた`Version``Location``Dependency`要素の 、 、および 属性に対応します。

## <a name="see-also"></a>関連項目
- [VSIX 拡張スキーマ 2.0 リファレンス](../extensibility/vsix-extension-schema-2-0-reference.md)
- [VSIX パッケージの解剖学](../extensibility/anatomy-of-a-vsix-package.md)
