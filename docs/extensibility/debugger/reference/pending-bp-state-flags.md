---
title: PENDING_BP_STATE_FLAGS |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_FLAGS
helpviewer_keywords:
- PENDING_BP_STATE_FLAGS enumeration
ms.assetid: 85522449-3fd8-4da5-b0fe-a43160e0c33b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6da1a956ac958a95dd0c433283a71af0a9b29d1e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714087"
---
# <a name="pending_bp_state_flags"></a>PENDING_BP_STATE_FLAGS
保留中のブレークポイントの状態フラグを指定します。

## <a name="syntax"></a>構文

```cpp
enum enum_PENDING_BP_STATE_FLAGS { 
   PBPSF_NONE        = 0x0000,
   PBPSF_VIRTUALIZED = 0x0001
};
typedef DWORD PENDING_BP_STATE_FLAGS;
```

```csharp
public enum enum_PENDING_BP_STATE_FLAGS { 
   PBPSF_NONE        = 0x0000,
   PBPSF_VIRTUALIZED = 0x0001
};
```

## <a name="fields"></a>フィールド
 `PBPSF_NONE`プレース ホルダー。

 `PBPSF_VIRTUALIZED`新しいコードが読み込まれるたびにバインドされる、仮想化された保留中のブレークポイントを指定します。

## <a name="remarks"></a>Remarks
 PENDING_BP_STATE_INFO構造体の`flags`メンバーに使用[PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)されます。

## <a name="requirements"></a>必要条件
 ヘッダー: msdbg.h

 名前空間: を使用します。

 アセンブリ:

## <a name="see-also"></a>関連項目
- [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
