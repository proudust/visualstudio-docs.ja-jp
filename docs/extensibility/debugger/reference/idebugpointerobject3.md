---
title: オブジェクト 3 |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPointerObject3 interface
ms.assetid: 11d26af4-1079-435e-96fa-d5269cbea8eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8605f1cdd50b6e98d6e30a7b550cce1d22543ff9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725469"
---
# <a name="idebugpointerobject3"></a>IDebugPointerObject3
> [!IMPORTANT]
> Visual Studio 2015 では、式エバリュエーターのこの実装方法は非推奨になりました。 CLR 式エバリュエーターの実装については、「 [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)」を参照してください。

 パース ツリー内のポインターを表し **、IDebugPointerObject**インターフェイスを拡張します。

## <a name="syntax"></a>構文

```
IDebugPointerObject3 : IDebugPointerObject
```

## <a name="notes-for-implementers"></a>実装者向けの注意事項
 式エバリュエーター (EE) は、このインターフェイスを実装します。

## <a name="methods"></a>メソッド
 [インターフェイスの](../../../extensibility/debugger/reference/idebugpointerobject.md)メソッドに加えて、このインターフェイスは、次のメソッドを実装します。

|Method|説明|
|------------|-----------------|
|[GetPointerAddress](../../../extensibility/debugger/reference/idebugpointerobject3-getpointeraddress.md)|ポインターのアドレスを取得します。|

## <a name="requirements"></a>必要条件
 ヘッダー: Ee.h

 名前空間: を使用します。

 アセンブリ:
