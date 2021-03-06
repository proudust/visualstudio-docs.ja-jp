---
title: イベントの説明 |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c2582717fd4da3b833da90a951f9b8f72a59f71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738790"
---
# <a name="event-descriptions"></a>イベントの説明
イベントの種類ごとに、特定の目的があります。

## <a name="events-and-the-reasons-for-their-use"></a>イベントとその使用理由

|Event|説明|
|-----------|-----------------|
|ドキュメント イベントのアクティブ化|デバッグ エンジン (DE) が IDE を開くか、または前面にドキュメントを持って来る必要があるときに発生します。|
|ブレークポイントバインドまたはブレークポイント エラー イベント|ブレークポイントがバインドされている場合、またはブレークポイントがバインドできず、エラーが返されたときに送信されます。|
|ブレークポイントのバインドされていないイベント|バインドされたブレークポイントがコードからバインド解除されるときに発生します。|
|イベントを停止できる|ユーザーがコード内の指定したポイントで停止するかどうかを判断するために IDE に送信されます。|
|ブレークポイント イベント|コードまたはデータ ブレークポイントにヒットしたときに発生します。|
|テキスト イベントの文書化|文書内のテキストが変更されたときに発生します。 これらのイベントはメソッドを`IDebugEventCallBack2::Event`通じて送信されません。|
|エンジン作成イベント|エンジンが最初に作成されたときに送信されます。|
|エントリ ポイント イベント|デバッグ中のプログラムが初期化コードを実行し、最初のユーザー・エントリー・ポイントに達したときに送信されます。|
|例外イベント|実行中のプログラムが例外に達したときに送信されます。|
|式の評価完了イベント|非同期式の評価が完了したときに送信されます。|
|シンボルイベントの検索|DE がモジュールのシンボルを見つけるユーザーを求める必要がある場合に送信されます。|
|完全なイベントを読み込む|最初のプログラムの読み込みが完了し、最初のコードがプログラムで実行される場合にのみ送信されます。|
|メッセージイベント|メッセージがユーザーに送信されたときに送信されます。|
|モジュールのロード イベント|新しいモジュールがロードまたはアンロードされたときに送信されます。|
|出力文字列イベント|プログラムがデバッグ出力を書き込むときに送信されます。|
|イベントの作成と破棄|プロセス、プログラム、プロパティ、セッション、およびスレッドの作成または破棄を通知するために送信され、Visual Studio IDE がデバッグ中のプログラムの状態を追跡できるようにします。|
|ステップ完了イベント|ステップが完了したときに送信されます。|
|スレッド名変更イベント|ユーザーがスレッドの名前を変更したときに送信されます。|
|プログラム名変更イベント|ユーザーがプログラムの名前を変更したときに送信されます。|

## <a name="see-also"></a>関連項目
- [イベントの送信](../../extensibility/debugger/sending-events.md)
