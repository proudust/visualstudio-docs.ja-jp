---
title: デバッグ用 SDK ヘルパー |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9edb7c508fdea6736a71c0f70c0d2ff305d4a399
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713648"
---
# <a name="sdk-helpers-for-debugging"></a>デバッグ用の SDK ヘルパー
これらの関数と宣言は、C++ でデバッグ エンジン、式エバリュエーター、およびシンボル プロバイダーを実装するためのグローバル なヘルパー関数です。

> [!NOTE]
> 現時点では、これらの関数と宣言のマネージ バージョンはありません。

## <a name="overview"></a>概要
 Visual Studio で使用するデバッグ エンジン、式エバリュエーター、およびシンボル プロバイダーを登録する必要があります。 これは、レジストリ サブキーとエントリを設定することで行われます。 以下のグローバル関数は、これらのメトリックの更新プロセスを容易にするように設計されています。 これらの機能によって更新される各レジストリ サブキーのレイアウトについては、レジストリの場所に関するセクションを参照してください。

## <a name="general-metric-functions"></a>一般的なメトリック関数
 これらは、デバッグ エンジンで使用される一般的な関数です。 式エバリュエーターとシンボル プロバイダーの特殊な関数については、後で詳しく説明します。

### <a name="getmetric-method"></a>メトリックメソッド
 レジストリからメトリック値を取得します。

```cpp
HRESULT GetMetric(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   DWORD * pdwValue,
   LPCWSTR pszAltRoot
);
```

|パラメーター|説明|
|---------------|-----------------|
|マシン|[in]レジスタが書き込まれる可能性のあるリモート マシンの`NULL`名前 (ローカル マシンを意味します)。|
|タイプ|[in]メトリックの種類の 1 つ。|
|guidセクション|[in]特定のエンジン、エバリュエーター、例外などの GUID。これは、特定の要素のメトリックタイプの下のサブセクションを指定します。|
|メトリック|[in]取得するメトリック。 これは、特定の値名に対応します。|
|値|[in]メトリックからの値の格納場所。 GetMetric には、DWORD (この例のように)、BSTR、GUID、または GUID の配列を返すことができるいくつかの種類があります。|
|ルート|[in]使用する代替レジストリ ルート。 デフォルト`NULL`を使用するように に設定します。|

### <a name="setmetric-method"></a>セットメトリックメソッド
 レジストリ内の指定されたメトリック値を設定します。

```cpp
HRESULT SetMetric(
         LPCWSTR pszType,
         REFGUID guidSection,
         LPCWSTR pszMetric,
   const DWORD   dwValue,
         bool    fUserSpecific,
         LPCWSTR pszAltRoot
);
```

|パラメーター|説明|
|---------------|-----------------|
|タイプ|[in]メトリックの種類の 1 つ。|
|guidセクション|[in]特定のエンジン、エバリュエーター、例外などの GUID。これは、特定の要素のメトリックタイプの下のサブセクションを指定します。|
|メトリック|[in]取得するメトリック。 これは、特定の値名に対応します。|
|値|[in]メトリック内の値の格納場所。 DWORD (この例では)、BSTR、GUID、または GUID の配列を格納できる SetMetric のいくつかのフレーバーがあります。|
|特定のユーザー|[in]メトリックがユーザー固有であり、ローカル コンピューター ハイブではなくユーザーのハイブに書き込まれる場合は TRUE。|
|ルート|[in]使用する代替レジストリ ルート。 デフォルト`NULL`を使用するように に設定します。|

### <a name="removemetric-method"></a>メトリックメソッドの削除
 指定したメトリックをレジストリから削除します。

```cpp
HRESULT RemoveMetric(
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   LPCWSTR pszAltRoot
);
```

|パラメーター|説明|
|---------------|-----------------|
|タイプ|[in]メトリックの種類の 1 つ。|
|guidセクション|[in]特定のエンジン、エバリュエーター、例外などの GUID。これは、特定の要素のメトリックタイプの下のサブセクションを指定します。|
|メトリック|[in]削除するメトリック。 これは、特定の値名に対応します。|
|ルート|[in]使用する代替レジストリ ルート。 デフォルト`NULL`を使用するように に設定します。|

### <a name="enummetricsections-method"></a>メソッド
 レジストリのさまざまなメトリック セクションを列挙します。

```cpp
HRESULT EnumMetricSections(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   GUID *  rgguidSections,
   DWORD * pdwSize,
   LPCWSTR pszAltRoot
);
```

|パラメーター|説明|
|---------------|-----------------|
|マシン|[in]レジスタが書き込まれる可能性のあるリモート マシンの`NULL`名前 (ローカル マシンを意味します)。|
|タイプ|[in]メトリックの種類の 1 つ。|
|ルギッドセクション|[イン、アウト]入力する GUID の事前割り当て配列。|
|サイズを変更します。|[in]`rgguidSections`配列に格納できる GUID の最大数。|
|ルート|[in]使用する代替レジストリ ルート。 デフォルト`NULL`を使用するように に設定します。|

## <a name="expression-evaluator-functions"></a>式エバリュエーター関数

|機能|説明|
|--------------|-----------------|
|ゲットメトリック|レジストリからメトリック値を取得します。|
|セットイーメトリック|レジストリ内の指定されたメトリック値を設定します。|
|Eメトリックを削除します。|指定したメトリックをレジストリから削除します。|
|GetEEMetricFile|指定したメトリックからファイル名を取得し、読み込んでファイルの内容を文字列として返します。|

## <a name="exception-functions"></a>例外関数

|機能|説明|
|--------------|-----------------|
|メトリック|レジストリからメトリック値を取得します。|
|メトリック|レジストリ内の指定されたメトリック値を設定します。|
|例外メトリックを削除します。|指定したメトリックをレジストリから削除します。|
|すべての例外メトリック|すべての例外メトリックをレジストリから削除します。|

## <a name="symbol-provider-functions"></a>シンボル プロバイダー関数

|機能|説明|
|--------------|-----------------|
|スプリメトリ|レジストリからメトリック値を取得します。|
|スメトリクスを設定します。|レジストリ内の指定されたメトリック値を設定します。|
|スプメトリックを削除します。|指定したメトリックをレジストリから削除します。|

## <a name="enumeration-functions"></a>列挙関数

|機能|説明|
|--------------|-----------------|
|列挙セクション|指定したメトリックの種類のすべてのメトリックを列挙します。|
|列挙型エンジン|登録されているデバッグ エンジンを列挙します。|
|EnumEEs|登録された式エバリュエーターを列挙します。|
|列挙例外メトリック|すべての例外メトリックを列挙します。|

## <a name="metric-definitions"></a>メトリック定義
 これらの定義は、定義済みのメトリック名に使用できます。 名前はさまざまなレジストリ キーと値の名前に対応し、ワイド文字列として定義されます`extern LPCWSTR metrictypeEngine`。

|定義済みのメトリックタイプ|説明: の基本キーです。|
|-----------------------------|---------------------------------------|
|メトリックタイプエンジン|すべてのデバッグ エンジンメトリック。|
|メトリックタイプポートサプライヤー|すべてのポート サプライヤー メトリック。|
|メトリックタイプ例外|すべての例外メトリック。|
|メトリックタイプEE拡張|すべての式エバリュエーター拡張。|

|デバッグ エンジンのプロパティ|説明|
|-----------------------------|-----------------|
|メトリックアドレスBP|アドレス ブレークポイントのサポートを示すには、0 以外に設定します。|
|メトリック常にローカルに負荷がかかる|常にデバッグ エンジンをローカルに読み込むように、ゼロ以外に設定します。|
|メトリックロードインデバッグジーセッション|使用しない|
|メトリックロードバイデバッグジー|デバッグ エンジンが常に読み込まれるか、またはデバッグ中のプログラムによって読み込まれることを示すには、0 以外に設定します。|
|メトリックアタッチ|既存のプログラムへの添付ファイルのサポートを示すには、ゼロ以外に設定します。|
|メトリックコールスタックBP|呼び出し履歴ブレークポイントのサポートを示すには、0 以外に設定します。|
|メトリックコンディショナルBP|条件付きブレークポイントの設定をサポートする場合は、0 以外に設定します。|
|メトリックデータBP|データの変更に対するブレークポイントの設定をサポートするには、0 以外に設定します。|
|メトリックディスアセンブリ|逆アセンブリ リストの生成のサポートを示すには、0 以外に設定します。|
|メトリックダンプ書き込み|ダンプ書き込み (出力デバイスへのメモリのダンプ) のサポートを示すには、ゼロ以外に設定します。|
|メトリックエンク|エディット コンティニュのサポートを示すには、0 以外に設定します。 **注:** カスタム デバッグ エンジンでは、この値を設定しないでください。|
|メトリック例外|例外のサポートを示すには、0 以外に設定します。|
|メトリックファンクションBP|名前付きブレークポイント (特定の関数名が呼び出されたときに中断するブレークポイント) のサポートを示すには、ゼロ以外に設定します。|
|メトリックヒットカウントBP|"ヒット ポイント" ブレークポイント (一定回数に達した後にのみトリガーされるブレークポイント) の設定をサポートするには、0 以外に設定します。|
|メトリック JIT デバッグ|Just-In-Time デバッグのサポートを示すには、0 以外に設定します (実行中のプロセスで例外が発生したときにデバッガーが起動します)。|
|メトリックメモリ|使用しない|
|メトリックポートサプライヤー|ポート サプライヤーが実装されている場合は、これをポート サプライヤの CLSID に設定します。|
|メトリックレジスター|使用しない|
|メトリックセット次ステートメント|次のステートメント (中間ステートメントの実行をスキップする) の設定をサポートするには、ゼロ以外に設定します。|
|メトリックサスペンドスレッド|スレッド実行の中断をサポートする場合は、ゼロ以外に設定します。|
|メトリックウォーンIfNoシンボル|シンボルが存在しない場合にユーザーに通知を受け取るようにするには、0 以外に設定します。|
|メトリックプログラムプロバイダー|これをプログラム・プロバイダーの CLSID に設定します。|
|ローカルに対して常にプログラムを読み込む|プログラム プロバイダーが常にローカルに読み込まれるようにするには、これをゼロ以外に設定します。|
|メトリックエンジンスキャンウォッチプロセス|デバッグ エンジンがプログラム プロバイダーではなくプロセス イベントを監視することを示すには、これをゼロ以外に設定します。|
|メトリックリモートデバッグ|リモート デバッグのサポートを示すには、これをゼロ以外に設定します。|
|メトリクスエンスユースネイティブビルダー|エディット コンティニュ マネージャがエディット コンティニュ用にビルドするためにデバッグ エンジンの encbuild.dll を使用する必要があることを示すには、これをゼロ以外に設定します。 **注:** カスタム デバッグ エンジンでは、この値を設定しないでください。|
|メトリックロードアンダーワウ64|64 ビット プロセスをデバッグするときに、WOW のデバッグ対象プロセスにデバッグ エンジンを読み込む必要があることを示すには、これをゼロ以外に設定します。それ以外の場合、デバッグ エンジンは Visual Studio プロセス (WOW64 で実行されている) に読み込まれます。|
|メトリックロードプログラムプロバイダーアンダーワウ64|WOW で 64 ビット プロセスをデバッグするときに、プログラム プロバイダーをデバッグ対象プロセスに読み込む必要があることを示すには、これをゼロ以外に設定します。それ以外の場合は、Visual Studio プロセスに読み込まれます。|
|管理境界を越えるメトリックストップオン例外|マネージ コード境界またはアンマネージ コード境界を越えて未処理の例外がスローされた場合にプロセスを停止する必要があることを示すには、これをゼロ以外に設定します。|
|メトリック自動選択優先順位|デバッグ エンジンの自動選択の優先順位に設定します (高い値は高い優先順位に等しい)。|
|メトリック自動選択互換性のあるリスト|自動選択で無視されるデバッグ エンジンの GUID を指定するエントリを含むレジストリ キー。 これらのエントリは、文字列として表される GUID を持つ数値 (0、1、2 など) です。|
|メトリック非互換リスト|このデバッグ エンジンと互換性のないデバッグ エンジンの GUID を指定するエントリを含むレジストリ キー。|
|最適化を無効にする|デバッグ中に Just-In-Time 最適化 (マネージ コードの場合) を無効にする必要があることを示すには、これを 0 以外に設定します。|

|式エバリュエータープロパティ|説明|
|-------------------------------------|-----------------|
|メトリックエンジン|これは、指定された式エバリュエーターをサポートするデバッグ エンジンの数を保持します。|
|メトリックプレロードモジュール|プログラムに対して式エバリュエーターが起動されたときにモジュールをプリロードする必要があることを示すには、これをゼロ以外に設定します。|
|このオブジェクト名のメトリック|これを"this"オブジェクト名に設定します。|

|式エバリュエーター拡張プロパティ|説明|
| - |-----------------|
|メトリックエクステンションDll|この拡張機能をサポートする dll の名前。|
|メトリック拡張レジスタサポート|サポートされているレジスタの一覧。|
|メトリック拡張レジスタエントリポイント|レジスターにアクセスするためのエントリ ポイント。|
|メトリック拡張の種類サポート|サポートされる型の一覧。|
|メトリック拡張タイプエントリポイント|タイプにアクセスするためのエントリ ポイント。|

|ポート サプライヤーのプロパティ|説明|
|------------------------------|-----------------|
|メトリックポートピッカークラスSID|ポート ピッカーの CLSID (ユーザーがポートを選択し、デバッグに使用するポートを追加するために使用できるダイアログ ボックス)。|
|メトリックディスアローユーザー入力ポート|ユーザーが入力したポートをポートサプライヤーに追加できない場合は 0 以外です (ポートピッカーダイアログボックスは基本的に読み取り専用になります)。|
|メトリックピッドベース|プロセス ID の割り当て時にポート サプライヤーが使用する基本プロセス ID。|

|定義済みの SP ストアの種類|説明|
|-------------------------------|-----------------|
|ストアタイプファイル|シンボルは別のファイルに保存されます。|
|ストアタイプメタデータ|シンボルは、アセンブリ内のメタデータとして格納されます。|

|その他のプロパティ|説明|
|------------------------------|-----------------|
|メトリックショー非ユーザーコード|ユーザー以外のコードを表示するには、これをゼロ以外に設定します。|
|メトリックジャストマイコードステッピング|ユーザー コードでのみステップ実行できることを示すには、これをゼロ以外に設定します。|
|メトリックCLSID|特定のメトリックタイプのオブジェクトの CLSID。|
|metricName|特定のメトリックタイプのオブジェクトのわかりやすい名前。|
|メトリック言語|言語名。|

## <a name="registry-locations"></a>レジストリの場所
 メトリックは、レジストリに対して読み取られ、特に`VisualStudio`サブキーに書き込まれます。

> [!NOTE]
> ほとんどの場合、メトリックはHKEY_LOCAL_MACHINE キーに書き込まれます。 ただし、HKEY_CURRENT_USERが宛先キーになる場合があります。 両方のキーを処理します。 メトリックを取得すると、最初にHKEY_CURRENT_USER検索してから、HKEY_LOCAL_MACHINE。 メトリックを設定する場合、パラメーターは使用するトップレベル キーを指定します。

 *[レジストリ キー]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[バージョンルート]*\

 *[メトリックルート]*\

 *[メトリックの種類]*\

 *[メトリック] = [メトリック値]*

 *[メトリック] = [メトリック値]*

 *[メトリック] = [メトリック値]*

|プレースホルダー|説明|
|-----------------|-----------------|
|*[レジストリ キー]*|`HKEY_CURRENT_USER` または `HKEY_LOCAL_MACHINE`。|
|*[バージョンルート]*|Visual Studio のバージョン ( `7.0`、 `7.1`、、または`8.0`など ) 。 ただし、このルートは **、/rootsuffix**スイッチを使用して**devenv.exe**に変更することもできます。 VSIP の場合、この修飾子は通常**Exp**なので、バージョン ルートは 8.0Exp のようになります。|
|*[メトリックルート]*|これは、dbgmetric.lib のデバッグバージョンが使用されているかどうかに応じて、または`AD7Metrics``AD7Metrics(Debug)`のいずれかです。 **注:** dbgmetric.lib を使用するかどうかにかかわらず、レジストリに反映する必要があるデバッグ バージョンとリリース バージョンの間に違いがある場合は、この名前付け規則に従う必要があります。|
|*[メトリックの種類]*|書き込むメトリックのタイプ: `Engine` `ExpressionEvaluator`、 `SymbolProvider`、、など。これらはすべて dbgmetric.h で`metricTypeXXXX`定義されていますが、`XXXX`これは特定の型名です。|
|*[メトリック]*|メトリックを設定するために値を割り当てるエントリの名前。 メトリックの実際の構成は、メトリックの種類によって異なります。|
|*[メトリック値]*|メトリックに割り当てられた値。 値の型 (文字列、数値など) はメトリックによって異なります。|

> [!NOTE]
> すべての GUID は、 の形式で`{GUID}`格納されます。 たとえば、「 `{123D150B-FA18-461C-B218-45B3E4589F9B}` 」のように入力します。

### <a name="debug-engines"></a>デバッグ エンジン
 レジストリ内のデバッグ エンジンのメトリックの構成を次に示します。 `Engine`は、デバッグ エンジンのメトリックの種類の名前で、上記のレジストリ サブツリーの *[メトリックの種類] に*対応します。

 `Engine`\

 *[エンジンガイド]*\

 `CLSID` = *[クラスガイド]*

 *[メトリック] = [メトリック値]*

 *[メトリック] = [メトリック値]*

 *[メトリック] = [メトリック値]*

 `PortSupplier`\

 `0` = *[ポートサプライヤーの案内]*

 `1` = *[ポートサプライヤーの案内]*

|プレースホルダー|説明|
|-----------------|-----------------|
|*[エンジンガイド]*|デバッグ エンジンの GUID。|
|*[クラスガイド]*|このデバッグ エンジンを実装するクラスの GUID。|
|*[ポートサプライヤーの案内]*|ポート サプライヤーの GUID (存在する場合)。 多くのデバッグ エンジンは既定のポート サプライヤーを使用するため、独自の供給業者を指定しません。 この場合、サブキー`PortSupplier`は存在しません。|

### <a name="port-suppliers"></a>ポート サプライヤー
 レジストリ内のポート サプライヤー メトリックの構成を次に示します。 `PortSupplier`はポート サプライヤのメトリック タイプ名で *、[メトリックタイプ]* に対応します。

 `PortSupplier`\

 *[ポートサプライヤーの案内]*\

 `CLSID` = *[クラスガイド]*

 *[メトリック] = [メトリック値]*

 *[メトリック] = [メトリック値]*

|プレースホルダー|説明|
|-----------------|-----------------|
|*[ポートサプライヤーの案内]*|ポート サプライヤーの GUID|
|*[クラスガイド]*|このポート サプライヤーを実装するクラスの GUID|

### <a name="symbol-providers"></a>シンボル プロバイダー
 以下は、レジストリ内のシンボルサプライヤーのメトリックの構成です。 `SymbolProvider`は、シンボル プロバイダーのメトリックの種類の名前で *、[メトリックの種類]* に対応します。

 `SymbolProvider`\

 *[シンボル プロバイダー guid]*\

 `file`\

 `CLSID` = *[クラスガイド]*

 *[メトリック] = [メトリック値]*

 *[メトリック] = [メトリック値]*

 `metadata`\

 `CLSID` = *[クラスガイド]*

 *[メトリック] = [メトリック値]*

 *[メトリック] = [メトリック値]*

|プレースホルダー|説明|
|-----------------|-----------------|
|*[シンボル プロバイダー guid]*|シンボル プロバイダーの GUID|
|*[クラスガイド]*|このシンボル プロバイダーを実装するクラスの GUID|

### <a name="expression-evaluators"></a>式エバリュエーター
 レジストリ内の式エバリュエーター メトリックの構成を次に示します。 `ExpressionEvaluator`は式エバリュエーターのメトリックタイプ名で *、[メトリックタイプ]* に対応します。

> [!NOTE]
> 式エバリュ`ExpressionEvaluator`エーターのすべてのメトリック変更は適切な式エバリュエーターメトリック関数を通過すると想定されるため、メトリックタイプは dbgmetric.h では定義されていません (`ExpressionEvaluator`サブキーのレイアウトはやや複雑なので、詳細は dbgmetric.lib の中に隠されています)。

 `ExpressionEvaluator`\

 *[言語ガイド]*\

 *[ベンダーのガイド]*\

 `CLSID` = *[クラスガイド]*

 *[メトリック] = [メトリック値]*

 *[メトリック] = [メトリック値]*

 `Engine`\

 `0` = *[デバッグ エンジン GUID]*

 `1` = *[デバッグ エンジン GUID]*

|プレースホルダー|説明|
|-----------------|-----------------|
|*[言語ガイド]*|言語の GUID|
|*[ベンダーのガイド]*|仕入先の GUID|
|*[クラスガイド]*|この式エバリュエーターを実装するクラスの GUID|
|*[デバッグ エンジン GUID]*|この式エバリュエーターが動作するデバッグ エンジンの GUID|

### <a name="expression-evaluator-extensions"></a>式エバリュエーター拡張
 次に示しているのは、レジストリ内の式エバリュエータ拡張メトリックの構成です。 `EEExtensions`は式エバリュエーター拡張のメトリックタイプ名で *、[メトリックタイプ]* に対応します。

 `EEExtensions`\

 *[拡張 GUID]*\

 *[メトリック] = [メトリック値]*

 *[メトリック] = [メトリック値]*

|プレースホルダー|説明|
|-----------------|-----------------|
|*[拡張 GUID]*|式エバリュエーター拡張の GUID|

### <a name="exceptions"></a>例外
 レジストリ内の例外メトリックの構成を次に示します。 `Exception`は例外のメトリックタイプ名で *、[メトリックタイプ]* に対応します。

 `Exception`\

 *[デバッグ エンジン GUID]*\

 *[例外の種類]*\

 *[例外]*\

 *[メトリック] = [メトリック値]*

 *[メトリック] = [メトリック値]*

 *[例外]*\

 *[メトリック] = [メトリック値]*

 *[メトリック] = [メトリック値]*

|プレースホルダー|説明|
|-----------------|-----------------|
|*[デバッグ エンジン GUID]*|例外をサポートするデバッグ エンジンの GUID。|
|*[例外の種類]*|処理できる例外のクラスを識別するサブキーの一般的なタイトル。 一般的な名前は **、C++ 例外** **、Win32 例外**、**共通言語ランタイム例外**、および**ネイティブ ランタイム チェック です**。 これらの名前は、ユーザーに対する特定の例外クラスを識別するためにも使用されます。|
|*[例外]*|例外の名前 :**たとえば、_com_error**または**制御ブレーク**。 これらの名前は、ユーザーに対する特定の例外を識別するためにも使用されます。|

## <a name="requirements"></a>必要条件
 これらのファイルは、SDK[!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)]のインストール ディレクトリにあります (既定では、[*ドライブ]* \プログラム ファイル\Microsoft Visual\\Studio 2010 SDK )。

 ヘッダー: を含む\dbgmetric.h

 ライブラリ: libs\ad2de.lib, リブ\dbgmetric.lib

## <a name="see-also"></a>関連項目
- [API リファレンス](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
