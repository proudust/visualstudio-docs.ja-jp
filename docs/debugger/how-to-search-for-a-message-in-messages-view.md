---
title: '方法: メッセージ ビューでメッセージを検索する | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37f99c30c23461ada406bb0650f86d45d2a4a2e9
ms.sourcegitcommit: 3fe6bed9ef8fb1478106645f655c7472009ae43a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64832446"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>方法: メッセージ ビューでメッセージを検索する
メッセージ ビューで特定のメッセージを検索するには、そのハンドル、種類、またはメッセージ ID を検索条件として使用します。 これらのいずれか (または組み合わせ) が有効な検索条件になります。 検索の最初の方向を指定することもできます。 ダイアログ ボックス内のフィールドは、現在選択されているメッセージの属性で事前に読み込まれます。

### <a name="to-search-for-a-message-in-messages-view"></a>メッセージ ビューでメッセージを検索するには

1. Spy++ およびアクティブな [メッセージ ビュー](../debugger/messages-view.md) ウィンドウが表示されるようにご利用のウィンドウを配置します。

2. **[検索]** メニューから、 **[メッセージの検索]** を選択します。

    [[メッセージの検索] ダイアログ ボックス](../debugger/message-search-dialog-box.md)が開きます。

3. 目的のウィンドウに **[ファインダー ツール]** をドラッグします。 そのツールをドラッグすると、 **[メッセージの検索]** ダイアログ ボックスに、選択したウィンドウの詳細が表示されます。

   - または

     確認するメッセージが含まれているウィンドウのハンドルがある場合は、 **[ハンドル]** テキストボックスにそれを入力します。

   - または

     必要なメッセージの種類やメッセージ ID がわかっている場合は、 **[種類]** および **[メッセージ]** ドロップダウン メニューでそれらを選択し、 **[ハンドル]** テキスト ボックスをクリアします。

4. 値を指定しないフィールドはいずれもクリアします。

   > [!TIP]
   > 画面が乱雑にならないようにするには、 **[Spy を非表示]** オプションを選択します。 このオプションを選択すると、Spy++ のメイン ウィンドウが非表示になり、 **[ウィンドウ検索]** ダイアログ ボックスだけが他のアプリケーションの上に表示されます。 **[OK]** または **[キャンセル]** をクリックした場合、または **[Spy++ を非表示]** オプションをオフにした場合は、Spy++ のメイン ウィンドウが復元されます。

5. 検索の最初の方向として、 **[上]** または **[下]** を選択します。

6. **[OK]** をクリックします。

   一致するメッセージが見つかった場合は、[メッセージ ビュー] ウィンドウで強調表示されます。 「[メッセージ ビュー](../debugger/messages-view.md)」を参照してください。