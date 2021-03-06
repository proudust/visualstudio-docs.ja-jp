---
title: ストアビューアーを使用したデバッグ |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a870c66b1c14dc6ddf3e38fb6e5be8c116be3573
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654884"
---
# <a name="debugging-by-using-the-store-viewer"></a>ストア ビューアーを使用したデバッグ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ストアビューアーでは、[!INCLUDE[dsl](../includes/dsl-md.md)] によって使用される*ストア*の状態を調べることができます。 ストアビューアーには、特定のストアにあるすべてのドメインモデル要素が、要素のプロパティと要素間のリンクと共に表示されます。

## <a name="opening-store-viewer"></a>ストアビューアーを開く
 実験用ビルド [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] では、ストアのインスタンスにモデル情報が含まれているブレークポイントでコードを停止します。 次に、 **[イミディエイト]** ウィンドウで次のコマンドを入力して、ストアビューアーを開きます。

```
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
> @No__t_0 をストアインスタンスの名前に置き換える必要があります。 また、コードに名前空間を追加した場合は、完全修飾名前空間を使用せずに、ストアビューアーを表示するためのコマンドを入力できます。
>
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
> `…`
>
> `StoreViewer.Show(mystore);`

 @No__t_0 メソッドにはいくつかのオーバーロードがあります。 パラメーターとして、ストアまたはパーティションのインスタンスを指定できます。

 別の方法として、`Show` メソッドに渡すパラメーターがスコープ内にあるコード内の任意の場所に、ストアビューアーを表示するコード行を配置することもできます。 この操作により、コード行がストアのコンテンツのスナップショットとして実行されるときに、ストアビューアーが表示されます。

### <a name="using-store-viewer"></a>ストアビューアーの使用
 次の図に示すように、ストアビューアーが開くと、モードレス Windows フォームウィンドウが表示されます。

 ![](../modeling/media/storeviewer2.png "storeviewer2")ストアビューアー

 ストアビューアーには、左ペイン、右上のペイン、右下のペインの3つのペインがあります。 左側のウィンドウは、ストアの `DomainDataDirectory` メンバーの型のツリービューです。 パーティションノードを展開して要素をクリックすると、右上のペインに要素のプロパティが表示されます。 要素が他の要素にリンクされている場合は、追加の要素が右下のペインに表示されます。 右下のペインで要素をダブルクリックすると、左側のウィンドウで要素が強調表示されます。

## <a name="see-also"></a>参照
 [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)
