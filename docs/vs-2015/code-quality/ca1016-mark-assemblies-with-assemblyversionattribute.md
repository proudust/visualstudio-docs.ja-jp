---
title: 'CA1016: AssemblyVersionAttribute | を使用してアセンブリをマークします。Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f1498624d4f79a60854a624ee5c4053a3343f515
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663167"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: アセンブリに AssemblyVersionAttribute を設定します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|カテゴリ|Microsoft Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 アセンブリにバージョン番号がありません。

## <a name="rule-description"></a>規則の説明
 アセンブリの id は、次の情報で構成されます。

- [アセンブリ名]

- バージョン番号

- culture

- 公開キー (厳密な名前を持つアセンブリの場合)。

  [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] では、バージョン番号を使用してアセンブリを一意に識別し、厳密な名前を持つアセンブリの型にバインドします。 バージョン番号は、バージョンと発行者のポリシーと共に使用されます。 既定で、アプリケーションは、ビルドされたアセンブリのバージョンでのみ実行されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、<xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> 属性を使用してバージョン番号をアセンブリに追加します。 次の例を参照してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 サードパーティまたは運用環境で使用されているアセンブリについては、この規則による警告を抑制しないでください。

## <a name="example"></a>例
 次の例は、<xref:System.Reflection.AssemblyVersionAttribute> 属性が適用されているアセンブリを示しています。

 [!code-cpp[FxCop.Design.AssembliesVersion#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cpp/FxCop.Design.AssembliesVersion.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cs/FxCop.Design.AssembliesVersion.cs#1)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/vb/FxCop.Design.AssembliesVersion.vb#1)]

## <a name="see-also"></a>参照
 [アセンブリのバージョン管理](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903)[方法: 発行者ポリシーを作成する](https://msdn.microsoft.com/library/8046bc5d-2fa9-4277-8a5e-6dcc96c281d9)
