---
title: BP_ERROR_RESOLUTION_INFO |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d48c4bc888db0ad8be6a0d6e98eeea2223a27e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738088"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
場所、プログラム、スレッドなど、エラー ブレークポイントの解決方法について説明します。

## <a name="syntax"></a>構文

```cpp
typedef struct _BP_ERROR_RESOLUTION_INFO {
    BPERESI_FIELDS         dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
    BSTR                   bstrMessage;
    BP_ERROR_TYPE          dwType;
} BP_ERROR_RESOLUTION_INFO;
```

```csharp
public struct BP_ERROR_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
    public string                 bstrMessage;
    public uint                   dwType;
};
```

## <a name="members"></a>メンバー
`dwFields`\
この構造体のどのフィールドに入力するかを指定する[BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)列挙体の値の組み合わせ。

`bpResLocation`\
ブレークポイント解決の位置を指定する[BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)共用体。

`pProgram`\
ブレークポイント エラーが発生したアプリケーションを表す[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)オブジェクト。

`pThread`\
ブレークポイント エラーを生成したアプリケーションが実行されているスレッドを表す[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)オブジェクト。

`bstrMessage`\
このエラー解決の結果として発生する警告メッセージまたはエラー メッセージを含む文字列。

`dwType`\
ブレークポイントエラーの種類を指定する[BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)列挙体の値。

## <a name="remarks"></a>Remarks
この構造体は[、メソッドから](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)返されます。

## <a name="requirements"></a>必要条件
ヘッダー: msdbg.h

名前空間: を使用します。

アセンブリ:

## <a name="see-also"></a>関連項目
- [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
