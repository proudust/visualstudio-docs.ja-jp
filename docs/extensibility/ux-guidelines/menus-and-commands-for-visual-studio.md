---
title: ビジュアル スタジオのメニューとコマンド |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1f22b7ac4377b600208c079b6af1eff7fc3cbfc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698381"
---
# <a name="menus-and-commands-for-visual-studio"></a>Visual Studio のメニューとコマンド
## <a name="command-usage"></a>コマンドの使用法

### <a name="overview"></a>概要
 多くの別々の製品で構成されるスイートである Microsoft Office とは異なり、Visual Studio には、各製品がグローバルな Visual Studio IDE にコマンド セットを提供する多くの製品が含まれています。 IDE は、コンテキストに基づいてユーザーが使用できる機能をフィルター処理することで、数千ものコマンドの複雑さを管理します。

 デザイン ウィンドウからコード編集ウィンドウへの切り替えなど、ユーザーのコンテキストが変更されると、新しいコンテキストとは無関係の機能が失われます。 同時に、新しい機能は、プロパティやツールボックスオプションなどの関連する動的情報と一緒に表示されます。 ユーザーは、使用可能なコマンド セットのスワップに気付かないようにする必要があります。 ユーザーが表示または非表示にするコマンドに気を取られたり混乱したりする場合は、UI 設計を調整する必要があります。 ユーザーの現在のコンテキストは、IDE のタイトル バー、プロパティ ウィンドウ、プロパティ ページダイアログボックスなど、常に 1 つ以上の方法で示されます。

 コマンド バーを使用すると、UI の柔軟性が得られます。 Visual Studio 環境に固有のコマンド構造は、メイン メニューとメイン コマンド バーだけです。 他のコマンド バーは、アプリケーションの状態に基づいて表示および非表示になります。 ツール ウィンドウおよびドキュメント エディタは、ウィンドウの枠内に埋め込みツールバーを含めることもできます。

#### <a name="basic-guidelines"></a>基本的なガイドライン

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>可能な限り、既存の共有コマンド、コマンド グループ、およびメニューを使用します。
 コマンドは通常コンテキストに基づいて表示されるため、既存の共有メニューとコマンド グループを使用すると、コンテキストの変更の間でコマンド構造が比較的安定した状態になります。 共有コマンドを再利用し、関連する共有コマンドに近い新しいコマンドを配置すると、IDE の複雑さが軽減され、より使いやすい操作性が実現します。 新しいコマンドを定義する必要がある場合は、既存の共有コマンド グループに配置します。 新しいグループを定義する必要がある場合は、新しいトップレベルメニューを作成する前に、関連するコマンドグループの近くに既存の共有メニューにグループを配置します。

##### <a name="do-not-create-icons-for-every-command"></a>すべてのコマンドにアイコンを作成しないでください。
 コマンド アイコンを作成する前に、慎重に考えてください。 アイコンは、次のコマンドに対してのみ作成する必要があります。

- は、既定のツールバーに表示されます。

- は、[**カスタマイズ]** ダイアログを使用して、ユーザーがツールバーに追加される可能性があります。

- 別のマイクロソフト製品の同じアクションに関連付けられたアイコンが表示されます。

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>キーボード ショートカットの追加を制限する
 大多数のユーザーは、利用可能なすべてのショートカットのごく一部を採用しています。 疑わしい場合は、キーボード ショートカットに機能をバインドしないでください。 新しいショートカットを追加する前に、ユーザー エクスペリエンス チームと協力してください。

##### <a name="give-commands-a-default-menu-placement"></a>コマンドに既定のメニュー配置を指定します。
 コマンドは他のユーザーによってカスタマイズされ、それに応じて設計されます。 隠しコマンドのようなものはありません。 Visual Studio のすべてのコマンドは、[**ツール] >カスタマイズ**ダイアログ、コマンド ウィンドウ、オートコンプリート、[**キーボード] ダイアログ ボックス >>ツール>オプション**] ダイアログ ボックス、および [開発環境] ダイアログ ボックス (DTE) に表示されます。 ユーザーが簡単に見つけられるように、.ctc ファイルにコマンド名とツールチップを指定してください。

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>埋め込みツールバーの共有コマンドを複製しないでください。
 ユーザーのフォーカスの近くにコマンドを配置すると便利です。 これを行う方法の 1 つは、ツール ウィンドウまたはドキュメント エディターの上部に埋め込みツールバーを作成することです。 ツールバーに配置されるコマンドは、ウィンドウ内のコンテンツ領域に固有のコマンドにする必要があります。 これらのツールバー上の共有コマンドを複製しないでください。 たとえば、埋め込みツールバー内に 「保存」アイコンを配置しないでください。

### <a name="content-and-command-visibility"></a>コンテンツとコマンドの可視性
 コマンドは、**環境**、**階層**、およびドキュメント のスコープに存在**します**。 コマンドの配置に自信を持つために、各スコープを知る。

 **環境**スコープ内のコマンドは、プライマリ コンテキストを確立し、複数のコンテキストで共有されます。 ドキュメントやツール ウィンドウの表示/配置を変更します。 環境スコープのコマンドには、**新規プロジェクト**、**サーバーへの接続**、**アタッチプロセス**、**切り取り**、**コピー**、**貼り付け**、**検索**、**オプション**、**カスタマイズ**、**新しいウィンドウ**、**およびヘルプの表示**があります。

 **階層**スコープのコマンドは、**プロジェクト**、**チーム**、**およびデータ**を含む Visual Studio の階層を管理します。 プロジェクトのサブコンテキスト (**たとえば、デバッグ**、**ビルド**、**テスト**、**アーキテクチャ**、分析 など) に関連付**けられます**。 階層スコープのコマンドには、[**新しい項目の追加**]、[**新しいクエリ**]、[**プロジェクトの設定]、[****新しいデータ ソースの追加**]、[**パフォーマンス ウィザードの起動**]、[**ダイアグラムの新規作成**] があります。

 **ドキュメント**スコープのコマンドは、コード、デザイン、作業項目クエリ (WIQ) などのドキュメントの内容に対して機能します。 また、ツール ウィンドウのビューに対しても動作するか、そのツール ウィンドウに固有の機能を持っています。 ドキュメント スコープ コマンドは、階層固有のファイル オブジェクト **(Project から削除**など) にも作用します。 ドキュメント スコープのコマンドには、**リファクタリング >名前変更**、**作業項目のコピーの作成**、**すべて展開**、**すべて折りたたむ**、および**ユーザー タスクの作成**があります。

### <a name="command-placement-decisions"></a>コマンド配置の決定
 コマンドを作成したら、適切な配置とキーボード ショートカットを作成するかどうかを決定する必要があります。 次の決定パスに従って、コマンドを配置する場所を決定します。

 ![コマンド配置の意思決定グラフ](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Visual Studio でのコマンド配置の決定パス**

### <a name="command-placement-in-menus"></a>メニュー内でのコマンドの配置

#### <a name="main-menu-bar"></a>メイン メニュー バー
 メイン メニュー バーは、UI に貢献するコンテキスト固有のメニュー パッケージのコマンドの標準の場所である必要があります。 メイン メニュー バーは、表示するコマンドを制御するために使用されるという点で、他のコマンド構造とは異なります。 その他のすべてのコマンド バーは、メニューまたはツールバーに配置されているかどうかにかかわらず、コンテキストから外れているコマンドを無効にします。

 環境では、IDE 全体と複数のタスクドメインで共通のメインメニューバーに組み込まれたコマンドのセットを定義します。 これらのコマンドは、環境に読み込まれる VSPackage に関係なく常に表示されます。 VSPackages では、この一連のコマンドを拡張できますが、各製品のコマンド セットとそのコマンドの配置は、各チームの責任です。

 Visual Studio のメイン メニューの構造は、次のメニュー カテゴリに分類できます。

##### <a name="core-menus"></a>コアメニュー

- ファイル

- [編集]

- View

- ツール

- ウィンドウ

- Help

##### <a name="project-specific-menus"></a>プロジェクト固有のメニュー

- Project

- ビルド

- デバッグ

##### <a name="context-specific-menus"></a>コンテキスト固有メニュー

- チーム

- Data

- テスト

- Architecture

- 分析

##### <a name="document-specific-menus"></a>ドキュメント固有のメニュー

- Format

- テーブル

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>メインメニューを設計する場合は、次の規則に従ってください。

- 特定のコンテキストで 25 のトップレベル項目を超えないようにする

- メニューの高さは 600 ピクセルを超えないようにしてください。

- [Ultimate SKU] や [一般プロファイル] など、複数のコンテキストでメイン メニューを評価します。

- フライアウト メニューは受け付け可能です。

- フライアウト メニューには、少なくとも 3 つの項目と 7 つ以下の項目を含める必要があります。

- フライアウト メニューは 1 レベルの深さにのみ行く必要があります- いくつかの Visual Studio メニュー項目にはカスケード サブメニューがありますが、このパターンは推奨されません。

- 6 つ以下の区切り記号を使用してください。 グループ化は、次の図に従う必要があります。

     ![メイン メニューのグループ化のためのガイドライン](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- 各グループを図に含める必要はありませんが、グループ化を追加することは制限されています。

- 各グループには、2 ~ 7 つのメニュー項目を設定する必要があります。

#### <a name="main-menu-ordering"></a>メインメニューの順序付け
 新しいトップレベル項目を追加する前に、既存のトップレベルメニューにコマンドを配置することを検討してください。 新しいトップレベルメニューを追加する場合は、必ず正しい場所に配置してください。 メニューがプロジェクト、コンテキスト、またはドキュメントに固有のものかどうかを決定します。 トップレベルメニューの名前を簡潔にし、1語だけを使用してください。

 コアメニューは残りのコマンドを予約する必要があります。 ファイル、編集、およびビューは常に左側に、ツール、ウィンドウ、ヘルプは常に右にする必要があります。

#### <a name="context-menus"></a>コンテキスト メニュー
 コンテキスト メニュー内に機能を設定しすぎると、インターフェイスが学習しにくくなります。 主要な機能はすべてメインメニューバーから利用できる必要があります。 コマンドの配置は、コマンドの重複を避けるために既存のコマンドと調整する必要があります。 コンテキスト メニューの場合、シェルは、コンテキスト メニューがソリューション、プロジェクト ノード、またはプロジェクト項目のいずれに対して含まれる必要があるかに応じて、含める必要がある標準メニュー グループを定義します。

 コンテキストメニューをデザインする場合は、メインメニューと同じ規則に従います。

- 25 のトップレベルのメニュー項目を超えないようにします。

- フライアウト メニューは許容できますが、1 レベルを超えてはなりません - カスケード ポップアップを使用しないでください。

- 6 つ以下の区切り記号を使用してください。

### <a name="command-placement-in-toolbars"></a>ツールバーでのコマンドの配置

#### <a name="general-toolbars"></a>一般ツールバー
 ツールバーを設計および配置する場合は、次の標準に従ってください。

- ボタンごとに複数の動詞を使用しないでください。 1 つのボタン = 1 つのアクション。

- ラベルを付けて補強する必要がある場合にのみ、アイコンの横にテキストを使用します。

- 1 回のセッションで複数回切り替えられるプロパティ専用のコンボ ボックスを使用します。 それ以外の場合は、他の場所でプロパティを公開します。

- コンボ ボックスの幅は、ボックス内の最も長い項目の幅 + 30% に等しくする必要があります。 たとえば、最長の項目が 200 ピクセルの場合、コンボ ボックスの幅は 260 ピクセルになります。

- 区切り記号の使用を制限します。 ドロップダウンの形は視覚的な区切り文字として機能するため、ドロップダウンの横に区切り文字を使用すると、アンチパターンになります。

- アイコングループには、3 個から 6 個のアイコンを含める必要があります。

- 修飾子によって複数の便利なコマンドが発生する場合は、最後の設定を格納する分割ボタンを使用します。

     ![Visual Studio での分割ボタン](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **分割ボタンの例左側の 6 つのコマンドは、代わりに 1 つのボタンに収まります。**

#### <a name="product-specific-toolbars"></a>製品固有のツールバー
 各製品は、頻繁に使用される重要なコマンドを含む既定のツール バーを提供でき、各製品の既定のツール バーは、製品のインストール後に Visual Studio を初めて起動するときに表示されます。

 製品は、IDE が提供する共有コマンド グループとメニューも活用する必要があります。 各共有コマンド グループは、ユーザーにとって意味のある方法で関連するコマンドを整理するための共有メニューに配置されます。 複雑さを軽減するためには、この共有コマンド構造を活用することが重要です。

#### <a name="global-toolbars"></a>グローバル ツールバー
 グローバル ツールバーは、すぐに 1 行に収まるようにする必要があります。 新しいグローバル ツールバーを作成する場合は、そのツールバーの種類のガイドラインに従います。

 **ツールバーの一般的なガイドライン:**

- 各ツールバーには、共通のコントロール (グリッパー、オーバーフロー) で 24 ピクセルがあります。

- 各ツールバー ボタンは、パディングを含む幅 22 ピクセルです。 アイコンを分割ボタンに設定すると、さらに 11 ピクセルの幅が追加されます。

- ツールバー間でのコマンドの重複は許可されています。

  **ドキュメント固有のツールバーは、特定の**ファイルタイプがアクティブな場合に表示され、別のファイルタイプがアクティブになると消えます。

- ドキュメント固有のツールバーには、12 個以下のボタンを含む場合があります。

- ツールバーの幅の合計は 300 ピクセルを超えることはできません。

- 各ファイルの種類には、埋め込みツールバーを 1 つ、またはドキュメント固有のグローバル ツールバーを 1 つ持つことができますが、両方を含めないようにします。

  **コンテキスト固有のツールバーは、** 特定のコンテキストが設定されている場合に表示され、長期間アクティブな状態を維持する傾向があります。

- すべてのコンテキスト固有のツールバーのボタンの制限は 18 です。

- コンテキストがアクティブなときに、ほとんどのユーザーがこのツールバーのコマンドを一貫して使用しない場合は、このツールバーをコンテキストに関連付けないでください。

- コンテキストを終了するときにツールバーが消えてしまうことを確認します。 これらのツールバーは、起動時には表示されません。

  **コンテキストのないツールバーは**自動的に表示されません。 これらは、ユーザーがアクティブ化した場合にのみ表示されます。 最大幅を 200 ピクセル以下にします。

### <a name="general-organization-and-shell-defined-groups"></a>一般組織およびシェル定義グループ
 既存の共有コマンド、コマンド グループ、およびメニューを使用します。 新しいコマンドを定義する必要がある場合は、既存の共有コマンド グループに配置します。 新しいグループを定義する必要がある場合は、新しいトップレベルメニューを作成する前に、関連するコマンドグループの近くにある既存の共有メニューにグループを配置してみてください。 これにより、IDE でのコマンドの配置を一貫して確保しながら、コマンドの複雑さが軽減されます。

 デザイナー スタイルのドキュメント ウィンドウのコンテキストで表示される共有**の [書式]** メニューは、次の図に示されています。

 ![Visual Studio でのコールアウト付きの [書式] メニュー](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **メニュー グループ**

### <a name="reducing-and-reusing-commands"></a>コマンドの削減と再利用
 コマンドは通常、コンテキストに基づいて表示され、ユーザーが特定の時点で表示するコマンドの数を減らします。 ただし、コンテキストの変更の間でコマンド構造が比較的安定していることを確認するために、既存の共有メニューとコマンド グループを再利用する必要があります。

 共有コマンドを再利用し、関連する共有コマンドに近い新しいコマンドを配置すると、IDE の複雑さが軽減され、より使いやすい操作性が実現します。

## <a name="naming-commands"></a>名前付けコマンド

### <a name="naming-conventions"></a>名前付け規則
 コマンドの名前を一貫性のあるものにして、ユーザーがコマンド ラインを使用するか、キーボード ショートカットにバインドしてコマンドを検索して実行できるように、重要です。 コマンド名は、コマンドがツールバーやカスケード メニューやコンテキスト メニューに表示される場合に、コマンドがどのような目的で使用されているかをユーザーが理解するのにも役立ちます。

#### <a name="when-naming-commands"></a>コマンドに名前を付ける場合:

- テキストを作成して、簡単にローカライズできるようにします。 テキストのローカライズの詳細については、「[ローカリゼーションのベスト プラクティス](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices)」を参照してください。

- 簡潔にしてください。 コマンドは 3 語以下で使用してください。

- タイトル大文字小文字を使用する: 各単語の最初の文字は大文字にする必要があります。 Visual Studio でのテキストの書式設定の詳細については、「[テキスト スタイル](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)」を参照してください。

- コマンドの配置場所を考慮に入れてください。 トップレベルのメニューかポップアップか。 たとえば、フライアウトで整列コマンドをグループ化する場合、トップレベルのコマンドは「整列」、フライアウトコマンドは「左」、「右」、「中央」、「位置合わせ」などになります。 フライアウト コマンドに「左揃え」または「右揃え」という名前を付けるのは冗長です。

     ![Visual Studio での [書式] メニュー](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>コマンドでのアイコンの使用
 コマンドとアイコンのペアリングを使用して控え。 コマンドに固有のイメージを関連付けることによって、ユーザーがそのコマンドを識別する能力は高まりますが、画像の使い過ぎが発生すると、視覚的な混乱や非効率性が生じます。 コマンド アイコンを作成するかどうかを決定する際には、次のルールが役立ちます。

#### <a name="use-an-icon-with-a-command-only-if"></a>コマンドを含むアイコンは、次の場合にのみ使用します。

- 同じコマンドには、Microsoft Office アプリケーションなど、別の著名なマイクロソフト製品のアイコンが関連付けられます。

- コマンドは既定のツールバーに配置されます。

- このコマンドは、ユーザーが **[Customize..]** ダイアログボックスを使用してツールバーに追加する可能性が高い特殊なコマンドです。

## <a name="access-and-shortcut-keys"></a>アクセスキーとショートカットキー

### <a name="overview"></a>概要
 キーボードのキー割り当てには、次の 2 種類があります。

- **アクセス キー** (アクセラレータとも呼ばれます) は、コマンド用のメニューとダイアログ UI の各ラベルへのキーボード アクセスを許可します。 Access キーは、ほとんどのユーザー補助機能を目的として、すべてのメニューに割り当てられ、ほとんどのダイアログ ボックス コントロールは記憶されることではなく、現在のウィンドウにのみ影響を与え、ローカライズされます。

- **ショートカット キー**は、主に Ctrl キーとファンクション (Fn) キー シーケンスを使用します。 高度なユーザーのために、生産性を向上するために、より設計されています。 これらは、頻繁に使用されるコマンドにのみ割り当てられ、メインメニューをバイパスしながらすばやくアクセスできます。 ショートカット キーは記憶されるように意図されており、そのためにプロファイル スキームと一致して割り当てる必要があります。 ショートカット キースキームはプロファイルによって異なる場合があります。 ユーザーは、**キーボードのオプション>オプションを**使用してショートカット キー>カスタマイズできます。

### <a name="assigning-access-keys"></a>アクセスキーの割り当て
 アクセス キーは、Alt キーと英数字キーで構成されます。 例外なく、各メニュー項目にアクセスキーを割り当てます。 Windows と一般的な規則に従ってアクセス キーを割り当てます。 たとえば、**ファイル > New**のアクセス キーは、常に**Alt、F、N**にする必要があります。

 'i' (大文字または小文字) や小文字の 'l' などの単一ピクセル幅の文字を使用しないでください。

 可能な場合は、重複キーの使用を避けます。 重複が避けられない場合、メニュー システムは、キーを使用するすべてのコマンドを循環して競合を処理します。 たとえば、"N" アクセス キーを複製する [ファイル] メニューの下にある "Number" コマンドの場合 **、Alt、F、N**は新しいファイルを作成し **、Alt、F、N、N**は "Number" コマンドを実行します。

### <a name="assigning-shortcut-keys"></a>ショートカット キーの割り当て
 新しいショートカット キーは、すべてのコマンドに必要なものではなく、システム (およびユーザー メモリ) が過剰に使用される場合は、システムに対して課税を行うわけではないため、割り当ては避けてください。 カスタマー エクスペリエンス向上プログラム (CEIP) のデータは、Visual Studio ユーザーが統合されたショートカットのごく一部のみを使用することを示します。

 ショートカットを定義する場合は、次の規則に従います。

- **コントロール (Ctrl) キーとファンクション (Fn) キーシーケンスを使用します。**

- **頻繁に使用するショートカットを保持します。** 最も人気のあるショートカットを維持します。

- **エディタのショートカットを簡単に入力できます。** コードの記述時に開発者が最も必要とするコマンドに、簡単に入力できるショートカットをバインドします。 たとえば **、Edit.InvokeSmartTag**には、Alt + Shift + F10 ではなく、Ctrl+/ のようなクイック ショートカット キーが必要です。

- **一貫してテーマにしたショートカットを探します。**

- **Windows のガイドラインに従って、使用する修飾子キーを決定します。** ドキュメント全体に適用されるコマンドなど、大規模な効果を持つコマンドには、Ctrl キーを使用します。 標準ショートカットキーの動作を拡張または補完するコマンドには、Shift キーの組み合わせを使用します。 Ctrl キーを押しながら Alt キーを押す組み合わせを使用しないでください。

- **余分なショートカットを削除します。** レガシー機能がある場合は、アクセスキーが同じコマンドにすばやくアクセスできる場合は、極端な頻度(CEIPデータから10回未満)または中程度の頻度(CEIPデータから100回未満)で使用されるショートカットを削除することを検討してください。 たとえば、Alt、H、C はヘルプ/コンテンツを開きます。

  ショートカットの可用性を確認する簡単な方法はありません。 ショートカットを追加する場合は、次の手順を実行します。

1. Visual Studio [2013 のショートカット](http://visualstudioshortcuts.com/2013/)の一覧をチェックして、グループ化に類似したコマンドがあるかどうかを確認します。

2. **[ツール] >オプション>環境キーボード>ショートカット**をテストします。 「次の追加のキーボード マップ スキームを適用する」に一覧表示されている各キーボード マッピング スキームを確認します。 一意のショートカットを共有する一般、C#、VB、および C++ プロファイルを確認します。 ショートカットは、これらの場所のいずれにもマップされていない場合に使用できます。
