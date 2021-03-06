---
title: ビジュアルスタジオの複合パターン |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 500ea8ffe7c33c1d747590ea074bff43fa1a3ab3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698614"
---
# <a name="composite-patterns-for-visual-studio"></a>Visual Studio の複合パターン
複合パターンは、異なる構成で相互作用要素と設計要素を結合します。 Visual Studio での一貫性に関する最も重要な複合パターンには、次のようなものがあります。

- [データ可視化](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [オブジェクト上の UI とピーク](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [選択モデル](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [永続性と保存の設定](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [タッチ入力](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a>データの視覚化

### <a name="overview"></a>概要
 グラフは、データを集約して視覚化して意思決定を強化するための視覚的な方法です。 彼らは、ユーザーが多くのデータに直面するのを助けることができますが、注意に値するものとアクションが必要なものを見る意味はほとんどありません。

 次のいずれかの条件に該当する場合、ユーザーはグラフから利益を得ます。

- グラフは、ユーザーが自分が実行できるタスクを識別するのに役立ちますか。

- このグラフを使用すると、ユーザーは潜在的な変更の結果を予測できますか?

- グラフは、ユーザーが傾向を発見し、パターンを識別するのに役立ちますか。

- グラフを使用すると、ユーザーはより適切な意思決定を行うことができますか。

- グラフは、特定のコンテキストでユーザーが持つ可能性のある特定の質問に答えるのに役立ちますか?

#### <a name="general-rules-for-charts"></a>グラフの一般ルール

- データに明確なラベルを付けます。 説明のないイラストは、ただの可愛い写真です。

- 比率が歪むのを避けるため、軸をゼロから開始します。 線の長さとバーのサイズは、データ ポイント間の関係を理解するための重要な視覚的な手掛かりです。

- インフォグラフィックスではなく、グラフを作成します。 インフォグラフィックスはデータの芸術的表現であり、その主な目標は視覚的なストーリーテリングです。 グラフは視覚的に魅力的ですが、データ自体を代弁することができます。

- スケモフィズム、図棒グラフ、コントラスト ハッシュマーク、その他のインフォグラフィック タッチは避けてください。

- 装飾的な要素として 3D 効果を使用しないでください。 ユーザーが情報を理解する能力に本当に不可欠な場合にのみ使用してください。

- 3 色を超える色を使用すると、この種類のグラフの読み取りや解釈が正しく行われないようにします。

- 概念を理解したり、データを操作したりする唯一の手段として、チャート (またはイラストレーション) を使用しないでください。 これは、視覚障害を持つユーザーにとって困難を示します。

- ページ上の無償または装飾的な要素としてグラフを使用しないでください。 つまり、グラフに値が追加されない場合や、ユーザーが問題を解決する手助けをしていない場合は、そのグラフを使用しないでください。

### <a name="chart-types"></a>グラフの種類
 Visual Studio で使用されるグラフの種類には、棒グラフ、折れ線グラフ、変更された円グラフ (リング チャートまたはドーナツ グラフ)、タイムライン、散布図 ("クラスター チャート" とも呼ばれます)、ガント チャートなどがあります。 グラフの種類ごとに、異なる種類の情報を伝達するのに役立ちます。

### <a name="other-charting-considerations"></a>その他のグラフ作成に関する考慮事項

#### <a name="color"></a>Color
 Visual Studio で使用するために定義されたグラフ色の特定のパレットがあります。 パレットは色覚異常の主要なタイプのためにアクセス可能であり、色の非常に狭いスライスとして使用される場合でも色を区別することができます。 これらの色は、UI の任意の種類のグラフまたはグラフに対して、任意の組み合わせで使用できます。 その多くの異なる色を必要としない場合は、7つの色すべてを使用する必要はありません。 これらの色は前景要素と一緒に使用するようには設計されていないので、これらの色の上にテキストやグリフを配置しないでください。 これらの色相はハードコーディングされ、[**ツール > オプション]** の下でユーザーのカスタマイズに公開する必要があります (「[エンド ユーザーの色の公開](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)」を参照)。

|スウォッチ|Hex|RGB|
|------------|---------|---------|
|![見本 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|
|![見本 BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![見本 FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![見本 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![見本 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![見本 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![見本 B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a>オブジェクト上の UI とピーク
 このセクションでは、Visual Studio に固有のオブジェクト UI の種類である、コード ピーク ビューとも呼ばれる、ピークするコンテキストを示します。

### <a name="overview"></a>概要

- オブジェクト上の UI では、ユーザーのメイン タスクを損なうことなく、より多くの情報や対話機能をユーザーに提供する必要があります。

- Visual Studio のオンオブジェクト UI の主なパターンは、「注目のポイントでの情報」と呼ばれます。

- Visual Studio のオンオブジェクト UI は、インラインまたはフローティングで、永続性または一時的な UI です。

  - Visual Studio のオンオブジェクト UI の種類であるコード ピーク ビューは、インラインで耐久性があります。

  - コードレンズは、Visual Studio のオンオブジェクト UI の一種で、フローティングと一時的な

  コードの動作を理解したり、そのコードの詳細を見つけたりするには、多くの場合、開発者がコンテキストを切り替えて、他のコンテンツや別のウィンドウに移動する必要があります。 これらのコンテキストのシフトは、ユーザーがメイン ウィンドウを離れると元のタスクにフォーカスを失う可能性があるため、混乱を引き起こす可能性があります。 さらに、その元のコンテキストを元に戻すのは難しい場合があります、特にウィンドウを切り替えると、元のコードが他の UI によって隠される場合。

  オブジェクト上の UI は、「注目のポイントで情報」と呼ばれるパターンに従います。 これらのメッセージ、ポップアップ ウィンドウ、およびダイアログ ボックスは、ユーザーの主なタスクにフォーカスを失うことなく明確化または対話性を追加する追加の関連情報を提供します。 オブジェクト上の UI の例としては、ユーザーが通知領域のアイコンの上にポインターを置いたときに表示されるポップアップ ウィンドウ、スペル ミスのある単語の下の赤い波線、Visual Studio 2013 で導入されたピーク ビューなどがあります。

### <a name="decision-points"></a>決定ポイント
 Visual Studio では、注意点でこの情報パターンを使用する方法はいくつかあります。 適切なメカニズムを選択し、一貫した予測可能な方法で実装することは、全体的な経験にとって不可欠です。 そうしないと、ユーザーがコンテンツ自体に焦点を絞る、混乱や矛盾したエクスペリエンスを提供する可能性があります。

#### <a name="relationships-between-master-and-detail-content"></a>マスターコンテンツと詳細コンテンツの関係
 注目のポイントの情報は、ユーザーが注目しているコンテンツ (「マスター」コンテンツ) と追加の関連コンテンツ (「詳細」コンテンツ) との関係を表示するために使用されます。 このパターンでは、詳細コンテンツは、ユーザーが操作しているコンテンツに明確に関連しており、マスター コンテンツの近くに表示できます。 マスター コンテンツを圧倒せずに要約できない補足情報や情報は、ツール ウィンドウなどの別のパターンに従う必要があります。

- **マスター**コンテンツに近い場所に詳細コンテンツを常に表示します。

- **詳細**コンテンツを使用すると、ユーザーがマスター コンテンツに集中し続けられるようにしてください。 多くの場合、これを実現する最善の方法は、詳細コンテンツをマスター コンテンツにできるだけ近づけてレンダリングすることです。 これは、マスター コンテンツの横にあるポップアップ ウィンドウで詳細コンテンツをレンダリングするか、マスター コンテンツの下に詳細コンテンツをインラインで表示することによって行うことができます。

- ユーザーをマスタ コンテンツから遠ざける情報を注意点で使用**しないでください**。 ユーザーが詳細コンテンツを個別に表示する必要がある場合は、ユーザーがこれを行うための明示的なアクションを公開します。

#### <a name="design-details"></a>設計の詳細
 オブジェクト上の UI が正しい選択であると判断したら、主に設計上の考慮事項が 4 つあります。

1. **永続性:** コンテンツは持続性または一時的なものと想定されますか?
   ユーザーは、参照または操作する情報を表示したままにしますか? または、ユーザーは情報をすぐに確認し、メイン タスクを続行する必要がありますか。

2. **コンテンツタイプ:** コンテンツは情報、操作可能、またはナビゲーションになりますか?
   ユーザーは、マスター コンテンツに関する追加の詳細を必要としますか。 ユーザーは、マスタ コンテンツに影響を与えるタスクを完了する必要がありますか。 または、ユーザーが別のリソースに移動する必要がありますか?

3. **インジケータタイプ:** アンビエントインジケータは意味をなしますか?
   情報を便利な方法で要約し、マスターコンテンツを圧倒することなく表示できますか?

4. **ジェスチャ:** UI を呼び出して閉じるには、どのようなジェスチャを使用しますか。
   ユーザーはどのようにして詳細コンテンツを表示し、それを送り出すのですか? 一時的な状態と持続性のある状態を切り替えるピン留めなどのジェスチャを追加する価値はありますか?

   これら 4 つの決定ポイントは、オブジェクト上の UI の主要なコンポーネントに影響を与えます。

### <a name="on-object-ui-components"></a>オブジェクト上の UI コンポーネント

1. コンテナー (コンテンツプレゼンター) タイプ

    - フローティング

    - インライン

2. Content type

    - 情報提供: 静的または動的なデータ

    - 実行可能: マスターコンテンツを変更するコマンド

    - ナビゲーション: MSDN などの別のウィンドウまたはアプリケーションにユーザーを移動するリンク

3. ジェスチャ

    - [呼び出し]

    - 解雇

    - ピン留め

    - その他の相互作用

4. 永続性とコミット・モデル

    - 一時的

    - Durable

    - 自動

    - オンデマンド

5. アンビエントインジケータ(オプション)

    - 波線の下線

    - スマート タグ アイコン

    - その他のアンビエントインジケーター

#### <a name="container-content-presenter-type"></a>コンテナー (コンテンツプレゼンター) タイプ
 注目のポイントでコンテンツを表示するために利用可能な 2 つの主要なオプションがあります。

1. **インライン:** Visual Studio 2013 コード エディターで導入されたピーク ビューなどのインライン プレゼンターは、既存のコンテンツをシフトすることで新しいコンテンツのためのスペースを作ります。

    - ユーザーが、表示するコンテンツを参照したり、コンテンツを操作したりするのにかなりの時間を費やすことを期待する場合は、インラインプレゼンターを**使用**してください。

    - ユーザーが提示した情報を一目見たいと思う場合は、インライン発表者を**避**け、中断を最小限に抑えてメインタスクを続行します。

2. **フローティング:** フローティングプレゼンターは、選択したコンテンツにできるだけ近い位置に配置されますが、既存のコンテンツのレイアウトは変更されません。 選択したシンボルに最も近い空白の上にフローティング コンテンツ パネルを表示するなど、さまざまな方法を採用できます。

    - ユーザーが提示した情報を一目見たいと思う場合は、フローティングプレゼンターを**優先**し、中断を最小限に抑え、メインタスクを続行します。

    - ユーザーが、表示するコンテンツを参照したり、コンテンツを操作したりするのにかなりの時間を費やすことを期待する場合は、発表者の浮動を**避けてください**。

#### <a name="content-type"></a>Content type
 オブジェクト上の UI コンテナー内に表示できるコンテンツには、主に 3 種類あります。 これらのタイプの情報の任意の組み合わせを表示できます。 3 つのタイプは次のとおりです。

1. **情報提供:** ほとんどのオブジェクト UI コンテナは、何らかの情報コンテンツを表示します。 コンテンツは、環境の現在の状態に関する情報を表すか、将来の環境の潜在的な状態に関する情報を表す場合があります。 たとえば、リファクタリングなどの特定のコマンドが既存のコードに与える影響を示すために使用できます。

    - **表示**する情報の正規表現を常に使用します。 たとえば、コードはコードのように見え、構文の強調表示を含み、ユーザーが設定したフォントやその他の環境設定を尊重する必要があります。

    - 同じ情報がマスタ コンテンツとして表示される場合に可能な情報コンテンツに対して、常にアクションを**サポートすることを検討**してください。 たとえば、オブジェクト上の UI コンテナー内に既存のコードを表示する場合は、そのコードを参照および変更する機能をサポートすることを強くお勧めします。

    - 将来の状態を表す情報コンテンツを表示する場合は、**常**に別の背景色を使用することを検討してください。

2. アクション可能: 一部のオブジェクト UI コンテナーは、リファクタリング操作の実行など、マスター コンテンツに対して何らかのアクションを実行する機能を提供します。

    - **常に**、情報コンテンツとは別に、実行可能なコマンドを配置します。

    - **必要に応じて、常に**アクションを有効または無効にします。

    - ダイアログ ボックス内でコマンドを表現する場合は **、常**に標準のガイドラインを参照してください。

    - オブジェクト上の UI コンテナーで公開されるアクションの数は **、常**に最小限に抑えます。 オブジェクト上の UI と対話するは、軽量で高速なエクスペリエンスである必要があります。 ユーザーは、オブジェクト上の UI コンテナー自体の管理に費やす必要はありません。

    - **オブジェクト**上の UI コンテナーを閉じたり閉じたりするタイミングを常に考慮してください。 ベスト プラクティスとして、マスター コンテンツと詳細コンテンツの間のダイアログを終了するアクションは、そのアクションが呼び出されたときに、オブジェクト上の UI コンテナーも閉じる必要があります。

3. **ナビゲーション:** オブジェクト上の UI コンテナーには、ユーザーの Web ブラウザーで MSDN アーティクルを開くなどの別のウィンドウやアプリケーションにユーザーを移動するリンクが含まれています。

    - ユーザーが他のコンテンツに移動されることに驚かないように、**常**に「開く」でナビゲーションリンクを追加します。

    - ナビゲーション リンクとアクション可能なリンクは**常に**分離します。

#### <a name="ambient-indicators-optional"></a>アンビエントインジケータ(オプション)
 アンビエント インジケータは、コードの他の部分とは対照的な色で表示されるテキストや、波線の下線やスマート タグ アイコンなどのティック記号を含む明白なテキストを含め、微妙な場合があります。 アンビエントインジケータは、追加の関連情報の可用性を伝えます。 理想的には、ユーザーが対話しなくても有用な情報を提供します。

- **常に**アンビエント インジケーターを配置して、ユーザーの注意をそらしたり圧倒したりしないようにします。 そのような方法でアンビエントインジケーターを配置することが不可能な場合は、別の解決策を検討してください。

- **常に**アンビエント インジケーターを関連するコンテンツにできるだけ近づけます。

- **常に**、利用可能な情報をまとめた指標を作成するようにしてください。 使用できるデータ項目の数 (たとえば、単に 「参照」ではなく「3 参照」) を指定するか、データを要約する他の方法を考えることを検討してください。

  - インディケータのデータを常に計算して表示できない場合は、値が計算されるため、すぐにプログレッシブフィードバックを提供することを検討してください。 たとえば、未読メールの数が増えるにつれて Windows Phone の電子メール ライブ タイルが更新されるのと同様に、利用可能なデータの更新を反映する変更をアニメーション化することを検討します。

- **特定**のコンテンツに対してユーザーが合理的に取り込むことができる以上のインジケーターを追加しないでください。 アンビエントインジケータは、ユーザーからの操作を必要とせずに便利である必要があります。 指標は、オーバーフローや他の管理コントロールを必要とする場合、その雰囲気を失います。

#### <a name="gestures"></a>ジェスチャ
 ユーザーがマスター コンテンツにフォーカスを維持できるようにする重要な側面は、追加の詳細コンテンツを開いたり閉じたりするための適切なジェスチャをサポートすることです。

- **ユーザーは、追加**のコンテンツを開く際に、明示的なジェスチャを実行するように常に要求します。 一般的なオープン ジェスチャには次のものがあります。

  - **ホバー:** ツールチップまたは非インタラクティブな情報コンテンツ

  - **明示的なコマンド:** インライン プレゼンター

  - **アンビエント インジケータをダブルクリックします。** コードレンズ ポップアップ ウィンドウ

- ユーザーが Esc キーを押すたびに、**常**に詳細コンテンツを閉じてください。

- **常に**、オブジェクト上の UI のコンテキストを考慮してください。 コンテナー内での操作を可能にするコンテンツプレゼンターの場合は、ユーザーのワークフローに影響を与える可能性がある、ホバーに関する追加情報を表示するかどうかを慎重に検討します。

- **編集可能**と思われるコンテンツやユーザーの操作を招待するコンテンツは、ホバー時には表示しません。 ツールヒントの標準動作は、そのコンテンツを生成したマスター コンテンツ上にカーソルが表示されなくなったときにすぐに閉じるため、ユーザーが詳細コンテンツの上にカーソルを移動しようとすると、この動作はユーザーを苛立たせることができます。

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a>選択モデル

### <a name="overview"></a>概要
 選択モデルは、ユーザー インターフェイス内の対象となる 1 つ以上のオブジェクトに対する操作を示し、確認するために使用されるメカニズムです。 このトピックでは、Visual Studio ドキュメント エディター内の選択相互作用パターン (テキスト エディター、デザイン サーフェイス、およびモデリング サーフェス) について説明します。

 ユーザーは、自分が何に取り組んでいるかを Visual Studio に示す方法を持っている必要があり、Visual Studio は、その操作についてユーザーに対するフィードバックを予想通り返す必要があります。 ユーザーとユーザー インターフェイスの間の違いや誤った通信は、ユーザーがアクションに気づかず、意図しない結果を招く可能性があります。 多くの場合、何かが欠けているか、変更されたことがユーザーに表示されるまで、エラーは気付かれません。 したがって、選択モデルは、ユーザー インターフェイス設計の最も重要な要素の 1 つです。 Visual Studio の選択モデルは Windows と一致しますが、若干のバリエーションがあります。

 Visual Studio では、Windows と同様に、選択モデルは、対話が発生するコンテキストによって異なります。 選択は、次の 4 種類のオブジェクトで行うことができます。

- Text

- グラフィック オブジェクト

- リストとツリー

- グリッド

  これらのオブジェクト内には、次の 3 種類の選択があります。

- 連続

- 不整合

- リージョン

#### <a name="scope"></a>スコープ
 選択の最も重要なコンポーネントは、ユーザーが作業しているウィンドウ (アクティブ化) とフォーカスが配置されている場所 (選択) をユーザーが認識していることを確認することです。 Visual Studio では、ウィンドウ管理機能が拡張されていますが、アクティブ化のスキームは同じです。 Visual Studio には、アクティブ化用の 2 つのインジケーターがあります: ドキュメント ウィンドウ用とツール ウィンドウ用の 1 つ。

 ドキュメント ウィンドウの場合、アクティブ ウィンドウは、ドキュメント ウィンドウのタブが前面に表示され、背景色を変更することによって示されます。

 ![Visual Studio でのアクティブなタブの選択](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **アクティブなタブ選択**

 ツール ウィンドウの場合、アクティブ ウィンドウは、ツール ウィンドウのタイトル バー領域の色の変更によって示されます。

 ![Visual Studio でのアクティブなツール ウィンドウの選択](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **ノードの主な選択を示すアクティブツール ウィンドウ**

 ![Visual Studio での非アクティブなツール ウィンドウの選択](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **非アクティブなツール ウィンドウで、ノードの潜在選択を表示する**

 ウィンドウがアクティブになると、そのフォーカスは、ガイドラインのこのセクションで概説されている選択モデルに従って示されます。

#### <a name="context"></a>Context
 Visual Studio は、ユーザーが作業している場所を追跡しながら、コンテキストの強力な概念を保持するように設計されています。 ツール ウィンドウまたはドキュメント ウィンドウのいずれであっても、アクティブになっているウィンドウは 1 つだけです。 ただし、最上位のドキュメント ウィンドウは常に潜在選択を保持します。 フォーカスはツール ウィンドウにある場合もありますが、最後にアクティブだったドキュメント ウィンドウには、非アクティブ状態であっても選択範囲が表示されます。 これは、編集中のドキュメントにユーザーのコンテキストを保持し、Visual Studio がツール ウィンドウとドキュメント ウィンドウ間でシームレスに戻ってシフトできるように、状態が保持されていることを示すために行われます。

### <a name="text-selection"></a>テキストの選択
 組み込みのテキスト エディターなど、厳密にテキスト形式の Visual Studio エディターでは、MSDN の Windows ユーザー エクスペリエンス操作ガイドラインの[[マウスとポインター](/windows/desktop/uxguide/inter-mouse) ] ページで説明されているのと同じテキスト選択モデルと外観を使用します。 テキスト エディターの入力フォーカスは、挿入ポイントと呼ばれる縦線で示されます。 挿入ポイントは、その背後に表示される任意の逆数として、1 ピクセルの太さと色付けです。 コントロール パネルの**キーボード**アプレットの **[速度**] タブの **[カーソル点滅速度**] 設定で設定されたレートに従って点滅します。

#### <a name="contiguous-and-disjoint-selection"></a>連続的で不整合な選択
 テキスト エディタ内での選択は連続しているだけです。 不整合なテキスト選択は許可されていませんが、グラフィカルオブジェクトエディタで対処する必要があります。 ユーザーのマウス ポインタがテキスト領域上にある場合、カーソルは I ビームに変わります。 1 回クリックすると、テキスト エディタのクリック位置にカーソルが配置されます。 マウスボタンを押したまま選択ハイライトを開始し、マウスボタンを放すと選択のハイライトが終了します。

#### <a name="region-selection-box-selection"></a>リージョンの選択 (ボックス選択)
 Visual Studio では、テキスト エディターでの領域の選択がサポートされており、これはボックス選択と呼ばれます。 ボックス選択では、通常のテキスト ストリームに従わないテキストの領域を選択できます。 標準テキスト選択と同様に、選択範囲は連続している必要があります。 ボックス選択は、Alt キーを押しながらマウスでドラッグすることで開始されます。 ボックス選択は、Alt キーと Shift キーを押しながら矢印キーを使用して選択領域を示すことで開始することもできます。 ボックス選択では、通常の選択ハイライトが使用され、選択領域の終わりにカーソルが点滅します。

 ![Visual Studio での地域&#40;ボックス&#41;選択](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Visual Studio での領域 (ボックス) の選択**

#### <a name="text-selection-appearance"></a>テキスト選択の外観
 エディタでアクティブな選択と非アクティブな選択に使用される色はカスタマイズできます。 エディターの外観をカスタマイズするには、ツール **> オプション**に移動し、[**環境>フォントと色>テキスト エディタ**] を参照します。

### <a name="graphical-selection"></a>グラフィカルな選択

#### <a name="interaction"></a>相互作用
 グラフィカルオブジェクトの選択は複雑であり、いくつかの要因によって異なります。

- **エディターの主要な選択モデル。** グラフィカル オブジェクトを含むエディターを使用して、テキストやグリッドを編集することもできます。 たとえば、エディターは、Visual Studio XAML デザイナーなどのグラフィカル オブジェクトの配置もサポートするテキスト ベースのエディターです。 複数のオブジェクト タイプをサポートすると、ユーザーが異なる種類のオブジェクトで構成されるグループを選択する方法に影響を与える可能性があります。

- **プライマリおよびセカンダリ選択状態のサポート。** エディターは、オブジェクトを一致で編集したり、互いに整列させたり、サイズを合わせたりできるように、プライマリおよびセカンダリの選択状態を提供できます。

- **インプレース編集のサポート。** また、編集者は、グラフィカルオブジェクトのコンテンツを編集することもできます。 たとえば、四角形の図形には、ユーザーが変更できるテキストが内部に含まれている場合もあります。 また、テキストの中央揃えまたは両端揃えも可能です。 インプレース編集では、より詳細なレベルのユーザー操作が必要となるため、ユーザーに状態情報を表示するための適切な視覚的な手掛かりが必要です。

#### <a name="mouse-interaction"></a>マウス操作

|入力|結果|
|-----------|------------|
|選択されていないオブジェクトをクリックする|オブジェクトを選択し、オブジェクトの大きな値が変更可能な場合は、破線と選択ハンドルを表示します。|
|選択したオブジェクトをクリックします。|オブジェクトがサポートしている場合は、インプレイス編集をアクティブにします。 オブジェクトの外側をクリックすると、インプレイス編集モードが無効になります。|
|オブジェクトをダブルクリックする|オブジェクトの背後にあるコードを編集用に開き、必要に応じて既定のイベント ハンドラーを挿入する場合があります。|
|オブジェクトをポイントする|ポインターを移動カーソルに変更します。 明るさや色など、オブジェクトの外観が変わる場合があります。|
|選択ハンドルをポイントする|ポインタをサイズ変更カーソルに変更します。 回転をサポートするオブジェクトの場合、選択ハンドルに対してポインタの位置が異なる (たとえば、離れた位置に移動する) 場合に、選択ハンドルによってポインタが回転カーソルに変わる場合があります。|
|ドラッグ|オブジェクトが選択されていない場合でも、ポインタを移動カーソルに変更し、オブジェクトを移動します。|
|エディターがフォーカスを失う|オブジェクトは最後の操作/選択状態の間に保持されていたコンテンツと外観を保持しますが、インプレース編集モードを非アクティブにします。|
|オブジェクトの選択|オブジェクトの境界を強調するために、境界線、点線、またはその他の視覚的に区別された処理で示されます。|
|選択したオブジェクトのサイズを変更する|選択ハンドルで示されます。<br /><br /> サイズ変更可能なオブジェクトには 8 つのハンドルがあり、サイズを変更できる各方向を表します。 オブジェクトのサイズを特定の方向にしか変更できない場合は、使用できるハンドルが少なくなります。 ユーザーがオブジェクトのサイズを 8 つのハンドルが対話式でない場所にサイズ変更する場合、4 つのハンドルが使用されることがあります。 ハンドルのサイズは、表示解像度に比例してサイズを設定する**GetSystemMetrics** API 関数を使用して、ウィンドウ境界とエッジメトリックに関連付ける必要があります。<br /><br /> ![サイズ変更ハンドル](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|選択したオブジェクトを回転する|![回転ハンドル](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>キーボード操作

|入力|結果|
|-----------|------------|
|タブ|エディター内のオブジェクトの論理的な順序の間でフォーカス インジケーターを移動します。 **これは、TabIndex** (または同等の) プロパティ値、オブジェクトの作成順序、およびエディターの全体的な目的に応じて、左から右または上から下に設定できます。 Shift+Tab キーを押すと、フォーカスインジケーターの方向が反転します。|
|Space|キーストロークを維持しながら、パンモードをアクティブにします。 ビューポートの位置をパンするには、追加のマウス入力が必要です。|
|Ctrl + Space|キーストロークを維持しながらズームモードを有効にします。 ズーム倍率を増減するには、追加のマウス入力が必要です。|
|Ctrl キーを押しながら Alt キーを押しながらマイナス記号を押します。|ズーム倍率を 1 レベル下げます。|
|Ctrl キーを押しながら Alt キーを押しながらプラス記号を押す|ズーム倍率を 1 レベルずつ大きくします。|
|シフトまたは Ctrl|オブジェクトを選択グループに追加します。 Ctrl キーを押して、選択グループからオブジェクトを個別に削除することもできます。|
|次に、|オブジェクトの既定のコマンド (通常は開くまたは編集) を実行します。|
|F2|オブジェクトのインプレイス編集をアクティブにします。|
|方向キー|選択したオブジェクトを、矢印キーの方向に小さな増分 (1 ピクセルずつ) に移動します。|
|Ctrl キーを押しながら矢印キーを押す|選択したオブジェクトを、押された方向に大きく移動します (10 ピクセルなど)。|
|Shift キーを押しながら矢印キーを押す|選択したオブジェクトのサイズを、それぞれの方向に小さい増分 (たとえば、1 ピクセルずつ) に変更します。|
|Ctrl キーを押しながら Shift キーを押しながら矢印キーを押す|選択したオブジェクトのサイズを、それぞれの方向に大きく変更します (たとえば、10 ピクセルずつ)。|

 ユーザーがコントロールを編集する場合、オブジェクトがユーザー入力に合わせて自動的にサイズ変更されるのが適している場合があります。 たとえば、ユーザーがラベル コントロールを編集する場合、ラベルは、ユーザーが入力したテキストを表示するように拡大する必要があります。 この操作を行わない場合、ユーザーはテキストを編集した後にコントロールのサイズを手動で変更する必要があります。 ユーザーが多くのコントロールを持っている場合、これはローテで非生産的なタスクになります。

#### <a name="graphical-containers"></a>グラフィカルコンテナ
 場合によっては、グラフィカル エディターは、Windows フォーム パネル コントロールや HTML デザイナーのグリッド レイアウト コントロールなど、他のグラフィカル オブジェクトのコンテナーを提供します。 エディタが他のグラフィカルオブジェクトのコンテナを提供する場合は、コンテナにのみ次の選択モデルを使用する必要があります(コンテナ内のオブジェクトは、上記の標準モデルに従います)。

|入力|結果|
|-----------|------------|
|コンテナをシングルクリック|コンテナー オブジェクトを選択します。 コンテナは、(上記の説明に従って)標準のマウス入力とキーボード入力で移動またはサイズ変更できます。 コンテナに対して含まれるオブジェクトは移動されますが、含まれるオブジェクトも直接選択されない限り、サイズは変更されません。|
|コンテナの境界領域にカーソルを合わせます。|マウスを移動カーソルに変え、コンテナを移動できることを示します。|
|コンテナの境界領域をドラッグする|マウスを移動カーソルに変更し、コンテナ (および含まれているオブジェクト) を移動します。 コンテナーは、最初に 1 回のクリックで選択しないと移動できません。|
|コンテナ内のオブジェクトをシングルクリック|コンテナの選択を解除し(選択した場合)、クリックしたオブジェクトのみを選択します。|
|Shift キーを押しながら、または Ctrl キーを押しながら、包含オブジェクトまたはコンテナをクリックします。|クリックしたオブジェクトを既存の選択または選択グループに追加します。 クリックされたオブジェクトが既に選択グループのメンバーである場合、選択グループから削除されます。|

 含まれているオブジェクトは、前のセクションで説明したように、基本選択モデルに準拠している必要があります。 Windows フォーム デザイナーのユーザビリティ テストから、ユーザーは、(包含オブジェクトによって課される) 手順を介さずに、包含オブジェクトへのシームレスなアクセスを期待しました。

#### <a name="disjoint-and-region-selections"></a>分離と地域の選択
 グラフィカルオブジェクトエディタは、不整合な選択をサポートする必要があります。 この図は、Visual Studio のコントロールの外観を示していません。 詳細なビジュアル仕様については[、グラフィカルオブジェクトの選択の外観](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance)を参照してください。

 ![非結合セレクターと領域セレクター](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **分離選択**

 グラフィカルエディターは、マーキータイプの選択インジケータを使用してリージョンの選択を提供する必要があります。 グラフィカル・エディターが他のオブジェクト・タイプ (テキストなど) をサポートしている場合、その他のオブジェクト・タイプの制約によっては、領域選択ができない場合があります。

 ![マーキーの選択](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **マーキーの選択**

#### <a name="primary-and-secondary-selections"></a>プライマリおよびセカンダリの選択
 一部のグラフィカル オブジェクト エディタでは、ユーザがオブジェクトをグループで編集または整列できます。 この場合、プライマリおよびセカンダリ選択の概念を導入する必要があります。 主選択は、他のすべてのオブジェクトがグループ操作に応答するオブジェクトです。 ユーザーが最初に選択したオブジェクトがプライマリ コントロールになり、その後の選択が 2 番目の選択になります。 プライマリ選択は、プライマリオブジェクトを示す二次選択とは異なる視覚的処理を持ちます。

 ![プライマリとセカンダリ選択](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **2 つの二次選択を含む 1 次選択**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a>グラフィカルオブジェクト選択の外観
 選択ハンドルは、オブジェクトの境界ボックスの周囲に長方形のパターンで描画される四角形です。 次の図は、グラフィカル オブジェクトがハンドル、サイズ変更、およびインプレース編集の外観で使用できるさまざまな状態の例を示しています。 ハンドルのサイズは **、GetSystemMetrics** API を使用してウィンドウの境界とエッジメトリックに関連付ける必要があります。

| State | 外観 | 視覚的な詳細 |
|-------------------------|---------------| - |
| **未選択** | Default | ![既定のボタンの状態](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **プライマリ選択** | サイズ | ![サイズ変更ハンドルを使ったプライマリ選択](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **プライマリ選択** | 変更不可 | ![サイズ変更ハンドルを使わないプライマリ選択](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **プライマリ選択** | ロック | ![ロックされたプライマリ選択](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **二次選択** | サイズ | ![サイズ変更ハンドルを使ったセカンダリ選択](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **二次選択** | 変更不可 | ![サイズ変更ハンドルを使わないセカンダリ選択](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **二次選択** | ロック | ![ロックされたセカンダリ選択](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **アクティブな UI** | Default | ![UI のアクティブな状態](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>選択モデルの表示

#### <a name="tree-view"></a>[ツリー ビュー]
 ツリービューでの選択は、単純なハイライトで表示されます。 ユーザーがノード名またはノード アイコンをクリックすると、そのノードが選択されます。 ノードの左側にある三角形のグリフはツリー コントロールを展開または縮小しますが、ユーザーの選択には影響しません。

 ![Visual Studio での一般的なツリー ビュー](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Visual Studio での一般的なツリー ビュー**

 ツリー ビューは、ツリー内の複数のレベルにわたる場合でも、連続した選択と不整合な選択をサポートできます。 表示されているツリー ノードで、連続または不整合な複数の選択を行う必要があります。 ノードが折りたたまれている場合、不整合選択は失われ、折りたたまれたノードは選択を取得します。 この方法で、ユーザーは操作の影響を受けるノードを表示できます。 ノードが折りたたまれると、影響を受ける可能性のあるノードが不明になります。

 親ノードを選択すると、操作は親に適用される必要がありますが、操作が親とそのすべての子に適用される場合があります。 この場合は、操作中に、ユーザーに対して "すべての子に適用" オプションを明示的にするチェック ボックスや確認ダイアログなど、追加の UI を提供します。

##### <a name="renaming"></a>名前の変更
 ツリー内のノードが名前の変更をサポートしている場合は、名前の変更を行う必要があります。 インプレース操作は、Visual Studio のすべてのツリー コントロールの標準である必要があります。 インプレース編集モードを即座にアクティブにする名前変更コマンドを提供し、テキスト選択は、ユーザー入力を受け入れる準備ができて、ノードの名前全体をカバーします。 ノードがファイルを表す場合、ファイル名には拡張子が含まれている必要があります。 選択ハイライトにはファイル名の本文のみを含め、拡張子は含めないようにします。

|入力|結果|
|-----------|------------|
|Enter キー|名前の変更操作をコミットします。|
|Esc キー|名前の変更操作をキャンセルします。|
|インプレイス編集領域の外側をクリックする|名前の変更操作をコミットします。|
|元に戻す|名前の変更操作をキャンセルする簡単な元に戻すを提供します。|

#### <a name="selection-within-lists-and-grid-controls"></a>リストおよびグリッド コントロール内の選択
 リスト選択の重要な概念は、行ベースであり、選択時に行全体が 1 つの単位として選択されるということです。 対照的に、グリッドを使用すると、行の他の部分に影響を与えることなく、特定のセルを選択できます。 グリッドには、階層のブランチ全体を選択および選択解除できる、ネストされた行の階層 (TreeGrid など) も含まれます。 リスト内での選択は、データ行全体に単純な強調表示色で表示されます。 フォーカスは、現在編集可能な行またはセル (すべてのセルが読み取り専用の場合は行) の周囲に、1 ピクセルの点線枠で表示されます。

> [!NOTE]
> **フォーカス**と**選択**は異なる概念です。 *フォーカス*は、他のオブジェクトに明示的に向けられていない入力を受け取るためにどの UI 要素が対象にされているかを示しますが、*選択*は、後続の操作が行われる可能性のあるオブジェクトのセットにオブジェクトが含まれる状態を示します。

 リスト内の選択は、連続、不整合、またはリージョンである場合があります。 複数選択が許可されている場合は、連続した選択と不整合選択が常にサポートされ、領域 (ボックス) 選択のサポートはオプションです。 リージョンの選択は、リスト本文の空白部分をドラッグして開始されます。

| Object | [選択] |
|--------|------------|
| List | 連続 |
| List | 不整合 |
| List | リージョン |

 リストを 1 回クリックすると、クリックが発生した行が選択されます。 インプレイス編集をサポートするリスト セルをクリックすると、そのセルはインプレース編集のためにすぐにアクティブになります。 それ以外の場合は、行全体が直ちに選択され、ハイライトが表示されます。

 リスト本文でドラッグすると、次の 3 つのいずれかが実行されます。

- リストがサポートされ、マウスダウンが空白の場合にリージョン選択を開始します。

- リストセルまたは行がドラッグソースをサポートしている場合は、ドラッグ/ドロップ操作を開始します。

- 現在の行を選択します。

##### <a name="in-place-editing"></a>インプレース編集
 インプレース編集が許可されている場合、2 つの基本的なモデルがあります: 単純な編集コントロールとプロパティの選択。 シンプルなエディット コントロールを使用すると、コンテンツが強調表示され、インプレース編集がアクティブ化されるとすぐにユーザー入力が可能になります。 プロパティ ピッカーが実装されている場合、インプレース編集モードがアクティブになるとプロパティ ピッカーを呼び出すボタンが表示され、現在の選択は強調表示されません。 ピッカー ボタンは、セル内で右揃えで配置する必要があります。 インプレース編集の例については、Visual Studio の**プロパティ ウィンドウ**と**タスク一覧**を参照してください。

##### <a name="keyboard-support"></a>キーボードのサポート
 リストおよびグリッドでの選択のためのキーボードサポートは、Windows の標準の規則に従います。

- 矢印キーを押すと、フォーカスが移動するときに各行/セルが選択され、リストが移動します。

- Shift キーを押しながら矢印キーを押すと、方向キーの方向に連続した選択が実行されます。

- Ctrl + 矢印の後にスペースバーが表示され、選択項目のリスト項目の追加と削除が切り替えられ、不整合な選択が作成されます。

- ネストされた階層を含むグリッドの場合、右矢印キーは親行を展開し、左矢印キーは折りたたみます。

- Tab キーを押すと、セルが編集可能な場合、現在の行のセル間でフォーカスが移動します。

- Enter キーは、リスト内の項目に対して既定のコマンドを実行します (通常**は開きます**)。

- F2 キーを押して、現在選択されているセルのインプレース編集をアクティブにします。

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a>永続性と保存の設定

### <a name="overview"></a>概要
 Visual Studio の各ソフトウェア コンポーネントは、通常、独自の状態と永続性を担当しますが、Visual Studio では、ウィンドウのサイズや位置など、場合によっては設定が自動的に保存されます。 次の表は、自動的に保存された設定と、明示的なユーザーまたはプログラムされた操作を実行する必要がある設定の組み合わせです。

|Object|保存する内容|セーブするタイミング|保存する場所|
|------------|------------------|------------------|-------------------|
|選択可能なオブジェクト (コード行など)|コード行のブレークポイント<br /><br /> コード行に関連付けられたユーザー ショートカット|プロジェクトを保存したとき|プロジェクトの**ユーザー オプション (.suo)** ファイル|
|ダイアログ|ダイアログが移動された場合のダイアログの場所<br /><br /> ユーザーがダイアログで最後に使用したビュー|ダイアログが閉じるとき<br /><br /> セッションが終了したとき|メモリ内<br /><br /> **HKEY_Current_User**のレジストリ|
|ウィンドウ|ウィンドウのサイズと位置|ウィンドウが閉じたら<br /><br /> Visual Studio モードが変更されたとき<br /><br /> セッションが終了したとき|プロジェクトの**ユーザー オプション (.suo)** ファイル<br /><br /> ウィンドウ設定用のカスタム オプション ファイル|
|ドキュメント|ドキュメント内の現在の選択範囲<br /><br /> ドキュメントのビュー<br /><br /> ユーザーが訪問した最後の場所|ドキュメントを保存したとき|プロジェクトの**ユーザー オプション (.suo)** ファイル|
|Project|ファイルへの参照<br /><br /> ディスク上のディレクトリへの参照<br /><br /> 他のソフトウェアへの参照<br /><br /> Components<br /><br /> プロジェクト自体に関する状態情報|プロジェクトを保存したとき|プロジェクト ファイル|
|ソリューション|プロジェクトへの参照<br /><br /> ファイルへの参照|プロジェクトまたはソリューションを保存する場合|**ソリューション (.sln)** ファイル|
|**ツール>オプション**の設定|キーボードのカスタマイズ<br /><br /> ツールバーのカスタマイズ<br /><br /> カラースキーム|**[ツール>オプション]** ダイアログが閉じると<br /><br /> セッションが終了したとき|**HKEY_Current_User**のレジストリ|

 ユーザーが行っていること、および実行している場合、設定がメモリに保存されているかどうか (セッション中に)、ディスクに保存される (セッション間でのレジストリ設定)、プロジェクトまたはソリューション ファイル自体の一部として、**ソリューション オプション (.suo)** ファイルの一部として、またはソフトウェア コンポーネントだけが認識するカスタム設定ファイルとして指定します。 上の表は、設定を保存できるイベントをいくつか示しています。 ただし、状態を保存する必要がある場合は、他にもあります。

- ユーザーがダイアログまたはウィンドウ内の場所を変更したとき

- ユーザーがフォーカスを別のウィンドウに転送するとき

- ユーザーがデザイン モードからデバッグ モードに切り替えた場合

- ユーザーが自分のアカウントをログオフしたとき

- コンピュータが休止状態に入ったり、シャットダウンしたりしたとき

- コンピュータ/ハード ドライブが再フォーマットされ、もう一度設定される場合

### <a name="window-configurations"></a>ウィンドウ構成
 ウィンドウ構成は開発環境の基本的なプレゼンテーションです - それは、存在するツールウィンドウのリストとそれらが配置されている方法で構成されるスキームです。 IDE (IDE ウィンドウ) で管理されるウィンドウのレイアウト情報はユーザーごとに保持されるため、ユーザーが IDE を起動すると、ウィンドウレイアウトは Visual Studio を最後に終了したときと同じように表示されます。 IDE ウィンドウの状態と位置は、XML 形式のカスタム オプション ファイルに保存されます。 IDE に読み込まれたパッケージによって作成されたツール ウィンドウは、その状態情報をレジストリに保持し、ユーザーごとに表示される場合とない場合があります。

#### <a name="profile-specific-layouts"></a>プロファイル固有のレイアウト
 各プロファイルには、特定の開発者のペルソナになじみのある方法で編成されたツール ウィンドウのレイアウトが含まれています (Visual C++ 開発者は、IDE の左側に**ソリューション エクスプローラー**を表示し、C# の開発者は右側に**ソリューション エクスプローラー**を表示することを期待しています)。 プロファイル固有のウィンドウレイアウトは、ユーザーが起動時にプロファイルを選択した後に読み込まれます。 パッケージ作成者は、ユーザーがウィンドウ構成に加えた変更が保持されることを知りながら、顧客のエクスペリエンスに最適なウィンドウ レイアウトを決定する必要があります。

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a>タッチ入力
 ユーザーはタッチ デバイスで Microsoft 開発製品を使用するようになっています。 しかし、タッチデバイスで開発ツールを使用することが困難になる障壁があります。 ユーザーは、当社の製品が信頼性の高い、正確なタッチ体験を提供することを期待します。 これらのガイドラインの目的は、Visual Studio と関連製品間で、どのタッチ機能を組み込むかを決定し、一貫したタッチ エクスペリエンスを促進することです。

### <a name="levels-of-experience"></a>経験のレベル
 次のレベルの経験は、チームがタッチでの投資の関心の望ましいレベルに基づいて提供するタッチ機能を決定するためのガイドとして機能することを意図しています。

- **基本的な経験**は、仕事を通して行き止まりがないようにタッチ機能を提供したいチームのためのものです。

- **最適なエクスペリエンス**は、最も一般的なタッチ機能 (インターネット ブラウザー アプリケーションで通常利用できる機能など) を提供するチーム向けです。

- **高いレベルのエクスペリエンス**は、ジェスチャなどの機能や、アプリケーションをタッチファーストに対応できるその他のオプション機能を追加するチーム向けです。

||基本的な経験|最適化されたエクスペリエンス|高い経験|
|-|----------------------|--------------------------|-------------------------|
|ユーザーが..|コードとソリューション/プロジェクトレベルの読み取りを行き止めなしで修正|メンテナンス、リファクタ、およびナビゲーションタスクの実行|一貫性のある直感的で、かつ、安心して操作可能な操作|
|エディター|タッチパンと選択<br /><br /> スクロールバータッチをタップして、押し+ドラッグ|ピンチズーム<br /><br /> 高速スクロール<br /><br /> [選択]<br /><br /> コンテキストメニューの使いやすさ||
|上部ツール ウィンドウ|リストのパン<br /><br /> 項目の選択<br /><br /> スクロールバータッチをタップして、押し+ドラッグ|簡単な項目のスクロールと選択||
|ウィンドウ化||サイズ変更ウィンドウ<br /><br /> クイック アクセス||
|よく文書化する||開いているファイル間の簡単なナビゲーション||
|ジェスチャ||IDE 全体で一般的なジェスチャが機能することを確認する|ジェスチャベースのアクション<br /><br /> ドラッグ アンド ドロップとデザイナーのサポート|
|その他の考慮事項|||カスタムオンスクリーンキーボード|

#### <a name="gestures"></a>ジェスチャ
 ジェスチャを使用すると、より複雑な操作が必要になるコマンドへのショートカットがユーザーに提供されます。 [デスクトップ アプリケーションの一般的なタッチ ジェスチャ](/windows/desktop/wintouch/windows-touch-gestures-overview)に関する Windows ガイドラインを参照し、パンやズームなどの単純なジェスチャを含むほとんどのジェスチャについては、このガイダンスに従ってください。
