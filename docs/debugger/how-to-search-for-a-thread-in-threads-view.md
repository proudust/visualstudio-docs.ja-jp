---
title: '方法: スレッド ビューでスレッドを検索する | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd4014ca9eb99dce383b9de34e26794555b9fbef
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2019
ms.locfileid: "64798520"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>方法: スレッド ビューでスレッドを検索する
スレッド ID またはモジュール文字列を検索条件として使用することで、スレッド ビューで特定のスレッドを検索できます。 検索の最初の方向を指定することもできます。 ダイアログ ボックスのフィールドには、スレッド ツリー内の選択されたスレッドの属性が表示されます。

### <a name="to-search-for-a-thread-in-threads-view"></a>スレッド ビューでスレッドを検索するには

1. Spy++ およびアクティブな [[スレッド ビュー]](../debugger/threads-view.md) ウィンドウが表示されるように、ご利用のウィンドウを配置します。

2. **[検索]** メニューから、 **[スレッドの検索]** を選択します。

    [[スレッド検索] ダイアログ ボックス](../debugger/thread-search-dialog-box.md)が開きます。

3. 検索条件として、スレッド ID またはモジュール文字列を入力します。

4. 値を指定しないフィールドはいずれもクリアします。

   > [!TIP]
   > モジュールによって所有されているすべてのスレッドを検索するには、 **[スレッド]** テキスト ボックスをクリアし、 **[モジュール]** ボックスにモジュール名を入力します。 その後、 **[次を検索]** を使用してスレッドの検索を続行します。

5. 検索の最初の方向として、 **[上]** または **[下]** を選択します。

6. **[OK]** をクリックします。

   一致するスレッドが見つかった場合は、[スレッド ビュー] ウィンドウで強調表示されます。