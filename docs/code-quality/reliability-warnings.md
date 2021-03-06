---
title: 信頼性に関する警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d45deadc48445e043535e84b36718a14f5b391f6
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182808"
---
# <a name="reliability-warnings"></a>信頼性に関する警告

信頼性の警告は、正しいメモリやスレッドの使用など、ライブラリとアプリケーションの信頼性をサポートします。 信頼性の規則は次のとおりです。

|ルール|説明|
|----------|-----------------|
|[CA2000:スコープを失う前にオブジェクトを破棄](../code-quality/ca2000.md)|例外的なイベントが発生するとオブジェクトのファイナライザーを実行できないため、オブジェクトに対するすべての参照がスコープ外になる前に、オブジェクトを明示的に破棄する必要があります。|
|[CA2001:問題が発生する可能性のあるメソッドは呼び出しません](../code-quality/ca2001.md)|メンバーが危険性または問題のあるメソッドを呼び出します。|
|[CA2002:弱い ID を伴うオブジェクト上でロックしません](../code-quality/ca2002.md)|アプリケーション ドメインの境界を越えてオブジェクトに直接アクセスできる場合、そのオブジェクトの ID は不十分と表現されます。 スレッドで ID が不十分なオブジェクトをロックしようとすると、ブロックされることがあります。たとえば、異なるアプリケーション ドメインの別スレッドで、既に同じオブジェクトがロックされている場合です。|
|[CA2003:ファイバーをスレッドとして扱いません](../code-quality/ca2003.md)|マネージスレッドは Win32 スレッドとして扱われています。|
|[CA2004:GC.KeepAlive への呼び出しを削除します](../code-quality/ca2004.md)|SafeHandle の使用法に変換する場合は、GC のすべての呼び出しを削除します。KeepAlive (オブジェクト)。 この場合、クラスは GC を呼び出す必要がありません。KeepAlive。ファイナライザーがなくても、SafeHandle に依存してそれらの OS ハンドルを最終処理することを前提としています。|
|[CA2006:SafeHandle を使用して、ネイティブ リソースを要約します](../code-quality/ca2006.md)|マネージド コードで IntPtr を使用すると、セキュリティ上の問題および信頼性の問題が発生する可能性があります。 すべての IntPtr の使用状況をレビューして、SafeHandle または類似のテクノロジに置き換える必要があるかどうかを判断してください。|
|[CA2007:タスクを直接待機しないでください](../code-quality/ca2007.md)|非同期メソッドは[awaits](/dotnet/csharp/language-reference/keywords/await) 、を <xref:System.Threading.Tasks.Task> 直接待機します。|
|[CA2009: ImmutableCollection 値で ToImmutableCollection を呼び出さないでください](../code-quality/ca2009.md)|`ToImmutable`メソッドは、名前空間から変更できないコレクションで不必要に呼び出されました <xref:System.Collections.Immutable> 。|
|[CA2011: setter 内でプロパティを割り当てません](../code-quality/ca2011.md) | プロパティに、独自の[set アクセサー](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor)内で誤って値が割り当てられました。 |
|[CA2015: MemoryManager T から派生した型に対してファイナライザーを定義しません &lt;&gt;](../code-quality/ca2015.md) | から派生した型にファイナライザーを追加する <xref:System.Buffers.MemoryManager%601> と、メモリがによってまだ使用されている間は解放される可能性があり <xref:System.Span%601> ます。 |
