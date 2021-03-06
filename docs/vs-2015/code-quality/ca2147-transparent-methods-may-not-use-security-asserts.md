---
title: 'CA2147: Transparent メソッドは、security assert | を使用できません。Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f2bd0042b6f9a8e46939ab34c86294218fb79f4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610156"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: 透過コードは、セキュリティ アサートを使用してはならない
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 @No__t_0 としてマークされているコードには、アサートするための十分なアクセス許可が付与されていません。

## <a name="rule-description"></a>規則の説明
 このルールは、アセンブリ内のすべてのメソッドと型を分析します。これは、透過的に100%、transparent/critical が混在しているか、<xref:System.Security.CodeAccessPermission.Assert%2A> の宣言または命令型の使用にフラグを適用します。

 実行時に、透過的なコードから <xref:System.Security.CodeAccessPermission.Assert%2A> を呼び出すと、<xref:System.InvalidOperationException> がスローされます。 これは、100% の透過アセンブリでも、メソッドまたは型が透過的に宣言されているが、宣言型または命令型のアサートを含む、透過的またはクリティカルなアセンブリでも発生する可能性があります。

 @No__t_0 2.0 では、*透明性*という名前の機能が導入されました。 個々のメソッド、フィールド、インターフェイス、クラス、および型は、透過的または重大にすることができます。

 透過的なコードでは、セキュリティ特権を昇格することはできません。 したがって、このメソッドに付与または要求されるアクセス許可は、コードを通じて呼び出し元またはホストアプリケーションドメインに自動的に渡されます。 昇格の例としては、Assert、Linkdemand、SuppressUnmanagedCode、`unsafe` コードなどがあります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この問題を解決するには、Assert を呼び出すコードを <xref:System.Security.SecurityCriticalAttribute> でマークするか、アサートを削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則からのメッセージを抑制しないでください。

## <a name="example"></a>例
 @No__t_0 が透過的な場合、`Assert` メソッドが <xref:System.InvalidOperationException> をスローすると、このコードは失敗します。

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>例
 1つの方法として、次の例の SecurityTransparentMethod メソッドをコードレビューする方法があります。また、メソッドが昇格に対して安全であると見なされる場合は、セキュリティが強化された SecurityTransparentMethod をマークします。これには、詳細、完全、およびエラーなしのセキュリティが必要です。メソッドでは、Assert の下でメソッド内で発生するすべての呼び出しと共に、監査を実行する必要があります。

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 もう1つの方法として、コードからアサートを削除し、後続のファイル i/o のアクセス許可要求を SecurityTransparentMethod を超えて呼び出し元に渡すこともできます。 これにより、セキュリティチェックが有効になります。 この場合、アクセス許可要求は呼び出し元またはアプリケーションドメインにフローするため、セキュリティ監査は通常必要ありません。 アクセス許可の要求は、セキュリティポリシー、ホスト環境、およびコードソースのアクセス許可の付与によって厳密に制御されます。

## <a name="see-also"></a>参照
 [セキュリティの警告](../code-quality/security-warnings.md)
