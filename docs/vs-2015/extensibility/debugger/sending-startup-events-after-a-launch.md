---
title: 起動の後のスタートアップ イベントの送信 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caf36e6713e49bb1470cd720ba2d04f689abba43
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436661"
---
# <a name="sending-startup-events-after-a-launch"></a>起動の後のスタートアップ イベントの送信
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

デバッグ エンジン (DE) がプログラムにアタッチされると、デバッグ セッションに、一連のスタートアップ イベントを送信します。  
  
 スタートアップ イベントが、デバッグ セッションに送信される、次のとおりです。  
  
- エンジンの作成イベントです。  
  
- プログラムの作成イベントです。  
  
- スレッドの作成とモジュール読み込みイベント。  
  
- コードが読み込まれ、実行する準備がすべてのコードが実行される前に、送信、読み込み完了イベント  
  
  > [!NOTE]
  > このイベントを続行すると、グローバル変数を初期化し、スタートアップ ルーチンを実行します。  
  
- 可能なその他のスレッドの作成とモジュール読み込みイベント。  
  
- 通知プログラムに達したことのメイン エントリ ポイントなどのエントリ ポイント イベント**Main**または`WinMain`します。 このイベントは通常、DE が既に実行されているプログラムにアタッチする場合は送信されません。  
  
  セッション デバッグ マネージャー (SDM) が最初に送信、DE プログラムで、 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)後に、エンジンの作成イベントを表すインターフェイスを[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)、プログラムの作成イベントを表します。  
  
  これは通常、その後 1 つまたは複数[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)スレッド作成イベントと[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)モジュール読み込みイベント。  
  
  コードが読み込まれ、実行する準備がデが、SDM を送信するすべてのコードが実行される前に、 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)完了イベントをロードします。 最後に、プログラムが既に実行されていない場合、ドイツが送信します。、 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)エントリ ポイント イベント、通知プログラムのメイン エントリ ポイントに達した、およびデバッグの準備ができています。  
  
## <a name="see-also"></a>関連項目  
 [実行の制御](../../extensibility/debugger/control-of-execution.md)   
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)
