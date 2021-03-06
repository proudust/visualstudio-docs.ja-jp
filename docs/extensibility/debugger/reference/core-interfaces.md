---
title: コアインタフェース |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bf01ffceb122ad99d5ecca8fabfaa102a8fc505
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737581"
---
# <a name="core-interfaces"></a>コア インターフェイス
を使用してデバッガーを拡張するためのコア インターフェイスを次に示[!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]します。

## <a name="discussion"></a>ディスカッション
 これらのインターフェイスは、主にデバッグ エンジン (DE) を作成するために使用されます。 これらは、カテゴリ別に次の方法で構成されています。

- [[ブレークポイント]](#Breakpoints)

- [コンテキスト](#Contexts)

- [コアサーバー](#CoreServer)

- [デバッグ エンジン](#DebugEngines)

- [ドキュメント](#Documents)

- [イベント](#Events)

- [式](#Expressions)

- [メモリ](#Memory)

- [モジュール](#Modules)

- [ポート](#Ports)

- [プロセス](#Processes)

- [Programs](#Programs)

- [プロパティ](#Properties)

- [スタック フレーム](#StackFrames)

- [スレッド](#Threads)

- [型ビジュアライザー](#TypeVisualizers)

  インターフェイスを実装できるエンティティは次のとおりです。

- デバッグ エンジン (DE)

- ポートサプライヤー(PS)

- 式エバリュエーター (EE)

- ビジュアル スタジオ (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a>ブレークポイント
 これらのインターフェイスは、ブレークポイントの実装と追跡に関連しています。

|インターフェイス|によって実装される|説明|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|メモリ位置にバインドされたブレークポイントを表します。|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|ブレークポイントがメモリ位置にバインドされている場合に DE によって送信されます。|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|ブレークポイント要求のドキュメントチェックサムを表します。|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|ブレークポイントがメモリ位置にバインドされない場合に DE によって送信されます。|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|ブレークポイントに達したときに DE によって送信されます。|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|ブレークポイントの要求を表します。保留中のブレークポイントの作成に使用されます。|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|ブレークポイントの要求を表します。保留中のブレークポイントの作成に使用されます。|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|ブレークポイントのバインドに使用する情報を表します。|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|ブレークポイントがメモリ位置からバインド解除されたときに DE によって送信されます。|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|無効なブレークポイントを表します`IDebugBreakpointErrorEvent2`( によって返されます)。|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|無効なブレークポイントに関する解決情報を表します。|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|ブレークポイントが設定されている関数内の位置を表します。|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|バインドされるブレークポイントを表します。バインドされたブレークポイントの作成に使用されます。|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|バインドされたブレークポイントのセットに対する列挙を表します。|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|メモリの場所にバインドできなかったブレークポイントのセットに対する列挙を表します。|

## <a name="contexts"></a><a name="Contexts"></a>コンテキスト
 これらのインターフェイスは、デバッグ対象のプログラム内のさまざまな種類のコンテキストを表します。

|インターフェイス|によって実装される|説明|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|コード命令の開始位置を表します。|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)インターフェイスを拡張して、モジュール インターフェイスとプロセス インターフェイスの取得を有効にします。|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|ドキュメント内の位置を表します。|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|式を評価するコンテキストを表します。|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|バイトのコレクションのメモリ内の開始位置を表します。|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|ブレークポイントまたは例外のスタック フレーム コンテキストを表します。|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|ブレークポイントまたは例外のスタック フレーム コンテキストを表します。|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|一連のコード コンテキストに対する列挙を表します。|

## <a name="core-server"></a><a name="CoreServer"></a>コアサーバー
 これらのインタフェースは、プログラムがデバッグされるマシンを表します。 これらはによって実装されますが[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]、デバッグ エンジンによって呼び出すことができます。

|インターフェイス|によって実装される|説明|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|ポートおよびポートの供給業者、およびコンピューターに関する情報へのアクセスを提供します。|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|リモート デバッグをサポートする[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)を表します。|

## <a name="debug-engines"></a><a name="DebugEngines"></a>デバッグ エンジン
 これらのインターフェイスは、デバッグ エンジンと関連するイベントを表します。

|インターフェイス|によって実装される|説明|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|カスタム デバッグ エンジンを表します。|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|シンボル、JustMyCode、および例外の読み込みをサポートするカスタム デバッグ エンジンを表します。|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|デの新しい各インスタンスが、デバッグ タスクを処理する準備ができていることを示すために送信されます。|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|プログラムの起動をサポートするカスタム デバッグ エンジンを表します。|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|デ、PS|複数のデバッグ エンジンを処理するプログラム ノードを表します。|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|スレッド、プログラム、またはスタック フレームからデバッグ エンジンへのインターフェイスを取得する方法を提供します。|

## <a name="documents"></a><a name="Documents"></a>ドキュメント
 これらのインターフェイスは、ドキュメント (ソース ファイル) と関連付けられた要素を表します。

|インターフェイス|によって実装される|説明|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|ドキュメントを開く要求するために DE によって送信されます。|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|ドキュメントから逆アセンブルされた命令のストリームを表します。|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|名前とクラス ID (CLSID) を指定して、DE によって提供されるドキュメントを表します。|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE,EE|デバッグ ドキュメントのチェックサムを表し、コンポーネント間でチェックサムを渡すことを有効にします。|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|ドキュメント コンテキスト、特定のステートメントおよびコード コンテキストに対応するドキュメント内の位置を表します。|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|ドキュメント内の一般的な位置を表します。|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|ソース ファイル内の位置を文字オフセットとして表します。|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|実際のテキストを提供する 、DE によって提供されるテキスト[ドキュメント](../../../extensibility/debugger/reference/idebugdocument2.md)を表します 。|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|メモリ内のソース ファイルへの変更を指定するために DE によって送信されます。|

## <a name="events"></a><a name="Events"></a>イベント
 これらのインターフェイスは、DE とセッション デバッグ マネージャー (SDM) の間で送信されるすべてのイベントを表します。

| インターフェイス | によって実装される | 説明 |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | ドキュメントを開く要求するために DE によって送信されます。 |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | デバッグ エンジン (DE) は、シンボルの読み込み中にステータス バー メッセージを設定するセッション デバッグ マネージャー (SDM) にこのインターフェイスを送信します。 |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | プログラムの中断が完了したときに DE によって送信されます。 |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | ブレークポイントがバインドされている場合に DE によって送信されます。 |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | ブレークポイントのバインドに失敗したときに DE によって送信されます。 |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | ブレークポイントに達したときに DE によって送信されます。 |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | ブレークポイントがバインドされていない場合に DE によって送信されます。 |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | DE が特定の場所で停止するかどうかを判断するために送信されます。 |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | メモリ内のソース ファイルへの変更を指定するために DE によって送信されます。 |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | デの新しい各インスタンスが、デバッグ タスクを処理する準備ができていることを示すために送信されます。 |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | デによって送信され、デバッグ中のプログラムが最初の命令を実行する準備が整うことを示します。 |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | 他のイベント インターフェイスで使用されるインターフェイス。 |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | デ、PS | 他のすべてのイベント インターフェイスの派生元となる基本インターフェイス。 |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | (特定のイベント インターフェイスを実装するオブジェクトとして表される) イベントが送信される、SDM によって実装されるインターフェイスを表します。 |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | デバッグ中のプログラムで例外が発生したときに DE によって送信されます。 |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | 非同期式の評価が完了したときに DE によって送信されます。 |
| イベント 2 | | 廃止。 使用しないでください。 |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | インターセプトされた例外の処理が完了したときに DE によって送信されます。 |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | プログラムの読み込みが完了したときに DE によって送信されます。 |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | IDE がユーザーに情報メッセージを表示するように DE によって送信されます。 |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | モジュールがロードまたはアンロードされたときに DE によって送信されます。 |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | 起動された[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]実行可能ファイルのシンボルが見つからないことをユーザーに警告するようにデバッガー UI に通知します。 |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | IDE に任意の文字列を表示するために DE によって送信されます。 |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, DE | ポート イベントを任意のリスナーに通知するためにポートによって送信されます。 |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | デ、PS | プロセスが作成されたときに DE またはポートによって送信されます。 |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | デ、PS | プロセスが破棄されたときに DE またはポートによって送信されます。 |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | デ、PS | プログラムが作成されたときに DE またはポートによって送信されます。 |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | デ、PS | プログラムが破棄されたときに DE またはポートによって送信されます。 |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | デバッグ セッションを終了するときに、デバッグ エンジンが[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI の既定の動作をオーバーライドできるようにします。 |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | プログラムの名前が変更されたときに、デバッグ エンジン (DE) からセッション デバッグ マネージャー (SDM) に送信されます。 |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | 新しいプロパティ (`IDebugProperty2`インターフェイスで表される) が作成されたときに、DE によって送信されます。 |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | プロパティが破棄されたときに DE によって送信されます。 |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | 関数のステップ アウト時または関数上での戻り値を正しく表示するために、DE によって送信されます。 |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | デバッグ エンジンがメトリック設定をリモートで読み取ることを可能にします。 |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | 命令のステップが完了した場合、または命令のステップが完了したときに DE によって送信されます。 |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | モジュールのシンボルの読み込みの成功または失敗を示すために DE によって送信されます。 |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | スレッドが作成されたときに DE によって送信されます。 |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | スレッドが破棄されたときに DE によって送信されます。 |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | スレッドの名前が変更されたときに DE によって送信されます。 |

## <a name="expressions"></a><a name="Expressions"></a> 式
 これらのインターフェイスは、特定のコンテキストで評価される式を表します。

|インターフェイス|によって実装される|説明|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|評価する式を表します。 [インターフェイスから](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)取得します。|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|式が評価されるコンテキストを表します。 [インターフェイス](../../../extensibility/debugger/reference/idebugstackframe2.md)から取得します。|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|非同期式の評価が完了したときに DE によって送信されます。|

## <a name="memory"></a><a name="Memory"></a>メモリ
 これらのインターフェイスは、メモリ内のバイト シーケンスを表します。

|インターフェイス|によって実装される|説明|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|読み取りまたは書き込み可能なメモリ内のバイト シーケンスを表します。|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|バイトシーケンスのメモリ内の位置を表します。|

## <a name="modules"></a><a name="Modules"></a>モジュール
 これらのインターフェイスは、実行可能ファイルまたは に対応するモジュールを表します。DLL ファイル。

|インターフェイス|によって実装される|説明|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|単一の実行可能ファイルまたは DLL を表します。|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|シンボルをサポートする[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)を表します。|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|モジュールがロードまたはアンロードされたときに DE によって送信されます。|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|PDB ファイルに含まれるソース サーバー情報を表します。|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)によって認識されるモジュールのセットに対する列挙を表します。|

## <a name="ports"></a><a name="Ports"></a>ポート
 これらのインターフェイスは、ポートとポート サプライヤーを表します。

| インターフェイス | によって実装される | 説明 |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | ローカル コンピューターの既定のポートを表します。 |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | DCOM を使用して、ファイアウォールがリモート[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]デバッグをブロックしないように UI に要求するデバッグ エンジンを有効にします。 |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | ポートを表します。 |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | ポート イベントを任意のリスナーに通知するためにポートによって送信されます。 |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | プロセスを起動および終了できるポートを表します。 |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | ポートを使用してプログラムを登録および登録解除するために使用します。ポートは、現在デバッグ中のプログラムを追跡できます。 |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | ポートを選択するためのカスタマイズされた UI を表します。 |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | 新しいポートの作成元または配置元のポートの要求を表します。 |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | ポートの供給元を表します。 |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | 作成したポートに関する情報を保持 (ディスクに保存) できるポートの供給元を表します。 |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | [プロセス[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]に**アタッチ]** ダイアログ ボックスの [**トランスポート情報**] セクション内にテキストを表示する UI を有効にします。 |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | ターゲット コンピューターに関する情報を照会できます。 |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | 一連のポートに対する列挙を表します。 |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | ポート サプライヤーのセットに対する列挙を表します。 |

## <a name="processes"></a><a name="Processes"></a>プロセス
 これらのインタフェースは、プロセスを表し、1 つ以上のプログラムを含む単一の実行可能ファイルです。

|インターフェイス|によって実装される|説明|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS、デ|コンピューターで実行されているプロセスを表します。|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS、デ|デバッグをアクティブにサポートするプロセスを表します[(IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイスのステップ、続行、および実行の各メソッドを置き換えるために使用されます)。|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|デ、PS|プロセスが作成されたときに DE またはポートによって送信されます。|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|デ、PS|プロセスが破棄されたときに DE またはポートによって送信されます。|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|どのセッションが関連付けられているかを追跡する必要があるプロセスを表します。|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|ポート上の一連のプロセスの列挙体を表します。|

## <a name="programs"></a><a name="Programs"></a>プログラム
 これらのインタフェースは、プログラム、実行の論理単位を表し、必ずしも物理実行可能またはモジュールに対応する必要はありません。

|インターフェイス|によって実装される|説明|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|同時にデバッグされている他のプログラムと連携して動作する必要がある[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)を表します。|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|デ、PS|実行の論理単位を表します。|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|デ、PS|プログラムが作成されたときに DE またはポートによって送信されます。|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|デ、PS|プログラムが破棄されたときに DE またはポートによって送信されます。|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|デ、PS|複数のデバッグ エンジンで処理できる[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)を表します。|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|どのセッションが接続されているかを追跡できる必要がある[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)を表します。|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|デ、PS|実行中のプロセスに関する情報を返すことができる[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)を表します。|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|デ、PS|デバッグできるプログラムを表します。|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|デ、PS|関連付けられたプログラムへの接続試行をプログラム ノードに通知できるようにします。|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|SDM が DE によって制御されるプログラムに関する DE を照会する方法を提供します。|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|DEs がプログラムを SDM に登録して、デバッグ中であることを示すために使用します。|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|デ、PS|スレッドまたはプロセスの境界を越えてインターフェイスをマーシャリングできる[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)を表します。|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|デ、PS|プログラムのセットの列挙体を表します。|

## <a name="properties"></a><a name="Properties"></a> プロパティ
 これらのインタフェースは、プロパティ、特定のコンテキストに関連付けられた値、通常は式の評価の結果を表します。

|インターフェイス|によって実装される|説明|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|カスタムの方法でその値を表示できる[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)を表します。|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|スタック フレーム、ドキュメント、または式の評価結果の値を表します。|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|任意の長い文字列をサポートする[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)を表します。|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|新しいプロパティ[(IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)インターフェイスで表される) が作成されたときに、DE によって送信されます。|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|プロパティが破棄されたときに DE によって送信されます。|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|特定のスタック フレームの外側に存在できるプロパティへの参照を表します。|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|変数、レジスタ、パラメーター、および式を記述する[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)構造体のセットに対する列挙体を表します。|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)構造体のセットに対する列挙体を表します。|

## <a name="stack-frames"></a><a name="StackFrames"></a>スタック フレーム
 これらのインターフェイスは、ブレークポイントまたは例外が発生したコンテキストであるスタック フレームを表します。

|インターフェイス|によって実装される|説明|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|ブレークポイントまたは例外が発生したコンテキストを表します。|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|インターセプトされた例外を処理できる[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)を表します。|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|特定のスタック フレームに到達するために使用される関数呼び出しシーケンスを指定する[CODE_PATH](../../../extensibility/debugger/reference/code-path.md)構造体のセットに対する列挙体を表します。|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|スタック フレームを記述する一連の[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)構造体に対する列挙を表します。|

## <a name="threads"></a><a name="Threads"></a>スレッド
 これらのインターフェイスは、スレッドと、関連するイベントを表します。

|インターフェイス|によって実装される|説明|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|実行のスレッドを表します。|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|スレッドが作成されたときに DE によって送信されます。|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|スレッドが破棄されたときに DE によって送信されます。|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|スレッドの名前が変更されたときに DE によって送信されます。|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|スレッドのセットに対する列挙を表します。|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a>型ビジュアライザー
 これらのインターフェイスは、型のビジュアライザーをサポートします。 これらのインターフェイスは、通常、式エバリュエーターによって実装されます。

|インターフェイス|によって実装される|説明|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|型ビジュアライザーに表示されるバイト配列を表します。|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|型ビジュアライザーに渡されるデータにアクセスするためのメソッドを提供します。|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|[実装](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)へのアクセスを提供するプロパティを表します。|

## <a name="see-also"></a>関連項目
- [API リファレンス](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [カスタム デバッグ エンジンの作成](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
