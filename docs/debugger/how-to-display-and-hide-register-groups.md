---
title: '方法: レジスタ グループの表示と非表示を切り替える | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.registergroups
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, displaying and hiding register groups
- register groups, displaying and hiding
ms.assetid: 6be5dfb4-4cfe-4daf-b538-60405640857d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a904bfcf147d72dde16ffe0fbf9e754c2c356bb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62847796"
---
# <a name="how-to-display-and-hide-register-groups-c-c-visual-basic-f"></a>方法: レジスタ グループの表示と非表示を切り替える (C#、C++、Visual Basic、F#)

**[レジスタ]** ウィンドウは、 **[オプション]** ダイアログ ボックスにある **[デバッグ]** ノードの **[全般]** カテゴリで、アドレスレベルのデバッグが有効な場合にのみ、使用できます。

**[レジスタ]** ウィンドウでは、見やすいようにレジスタがグループ別に表示されます。 **[レジスタ]** ウィンドウを右クリックすると、ショートカット メニューがグループと共に表示され、必要に応じて表示と非表示を切り替えることができます。以下に手順を示します。

> [!NOTE]
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[リセット設定](../ide/environment-settings.md#reset-settings)」を参照してください。

## <a name="display-or-hide-register-groups"></a>レジスタ グループの表示と非表示を切り替える

1. **[レジスタ]** ウィンドウを右クリックします。

2. ショートカット メニューで、表示または非表示にするレジスタ グループをクリックします。

     デバッグ中のハードウェアでサポートされていないレジスタ グループは、ショートカット メニューで無効になっているため選択できません。

## <a name="see-also"></a>関連項目

- [方法: [レジスタ] ウィンドウを使用する](../debugger/how-to-use-the-registers-window.md)