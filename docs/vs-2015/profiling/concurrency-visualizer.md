---
title: コンカレンシー ビジュアライザー | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e7061acabbe5ce18ff6e1f210fe0003bdaf88980
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586813"
---
# <a name="concurrency-visualizer"></a>コンカレンシー ビジュアライザー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

注意]
> コンカレンシー ビジュアライザーは、Visual Studio に対する任意の拡張機能です。 コンカレンシー ビジュアライザーとコンカレンシー ビジュアライザー コレクション ツールは、以下のリンクからダウンロードします。  
> 
> - [コンカレンシー ビジュアライザー](https://visualstudiogallery.msdn.microsoft.com/a6c24ce9-beec-4545-9261-293061436ee9) 拡張機能をダウンロードします。  
>   - [Visual Studio 2015 用の同時実行ビジュアライザーコレクションツールを](https://www.microsoft.com/download/details.aspx?id=49103)ダウンロードします。  
> 
>   [コンカレンシー ビジュアライザーのコマンド ライン ユーティリティ (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) を使用して、コマンド ラインからトレースを収集することで、Visual Studio 2015 用のコンカレンシー ビジュアライザーでトレースを表示できます。 このツールは、Visual Studio がインストールされていないコンピューターで使用できます。  
  
 コンカレンシー ビジュアライザーを使用すると、マルチスレッド アプリがどのように動作するかを確認することができます。 コンカレンシー ビジュアライザーのビューには、プログラム内のスレッドとシステム間の時間的な関係をまとめて示す、グラフィカルな表形式のテキスト データが表示されます。 コンカレンシー ビジュアライザーを使用すると、パフォーマンスのボトルネック、十分に活用されていない CPU、スレッドの競合、コア間のスレッドの移行、同期の遅延、DirectX のアクティビティ、重複 I/O の領域などの情報を検索できます。 これらのビューでは、グラフィカルな出力を呼び出し履歴とソース コードにリンクすることで、アクション可能なデータを使用できるようになります。  
  
 コンカレンシー ビジュアライザーは、[Windows イベント トレーシング](https://msdn.microsoft.com/library/bb968803(VS.85).aspx)の機能に依存しています。  
  
> [!NOTE]
> コンカレンシー ビジュアライザーでは、Web プロジェクトはサポートされません。  
  
## <a name="related-topics"></a>関連トピック  
  
|Title|説明|  
|-----------|-----------------|  
|[使用状況ビュー](../profiling/utilization-view.md)|すべてのプロセッサのシステム アクティビティを表示して分析する方法について説明します。|  
|[スレッド ビュー](../profiling/threads-view-parallel-performance.md)|プログラム内のスレッド間の対話を分析する方法について説明します。|  
|[コア ビュー](../profiling/cores-view.md)|コア間のスレッドの移行を分析する方法について説明します。|  
|[適切に動作しないマルチスレッドアプリケーションの一般的なパターン](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|いくつかの一般的なパターンについて説明し、それらがどのようにコンカレンシー ビジュアライザーに表示されるかを示します。|  
|[Visual Studio での並行開発に関するブログ](https://docs.microsoft.com/archive/blogs/visualizeparallel/)|コンカレンシー ビジュアライザーのヒントとベスト プラクティスについて説明します。|  
|[パフォーマンスレポートのビュー](../profiling/performance-report-views.md)|Visual Studio プロファイリング ツールのレポートおよびビューに関するリファレンス情報を提供します。|  
|[コンカレンシー ビジュアライザー SDK](../profiling/concurrency-visualizer-sdk.md)|ソース コードをインストルメント化してコンカレンシー ビジュアライザーに追加情報を表示する方法について説明します。|  
|[コンカレンシー ビジュアライザー コマンドライン ユーティリティ (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|コンカレンシー ビジュアライザーのコマンド ライン ユーティリティ (CVCollectionCmd.exe) を使用して、Visual Studio がインストールされていないコンピューター上でトレースを収集および処理する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [プロファイル ツール](../profiling/profiling-tools.md)
