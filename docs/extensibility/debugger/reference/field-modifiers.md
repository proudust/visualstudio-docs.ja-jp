---
title: FIELD_MODIFIERS |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7a24345174854462a2118df626223a8a299cd7f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736858"
---
# <a name="field_modifiers"></a>FIELD_MODIFIERS
フィールド型の修飾子を指定します。

## <a name="syntax"></a>構文

```cpp
enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
typedef DWORD FIELD_MODIFIERS;
```

```csharp
public enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
```

## <a name="fields"></a>フィールド
`FIELD_MOD_ACCESS_TYPE`\
フィールドにアクセスできないことを示します。

`FIELD_MOD_ACCESS_PUBLIC`\
フィールドにパブリック アクセスがあることを示します。

`FIELD_MOD_ACCESS_PROTECTED`\
フィールドに保護されたアクセス権があることを示します。

`FIELD_MOD_ACCESS_PRIVATE`\
フィールドにプライベート アクセスがあることを示します。

`FIELD_MOD_NOMODIFIERS`\
フィールドに修飾子がないことを示します。

`FIELD_MOD_STATIC`\
フィールドが静的であることを示します。

`FIELD_MOD_CONSTANT`\
フィールドが定数であることを示します。

`FIELD_MOD_TRANSIENT`\
フィールドが一時的であることを示します。

`FIELD_MOD_VOLATILE`\
フィールドが揮発性であることを示します。

`FIELD_MOD_ABSTRACT`\
フィールドが抽象フィールドであることを示します。

`FIELD_MOD_NATIVE`\
フィールドがネイティブであることを示します。

`FIELD_MOD_SYNCHRONIZED`\
フィールドが同期されていることを示します。

`FIELD_MOD_VIRTUAL`\
フィールドが仮想であることを示します。

`FIELD_MOD_INTERFACE`\
フィールドがインターフェイスであることを示します。

`FIELD_MOD_FINAL`\
フィールドが最終フィールドであることを示します。

`FIELD_MOD_SENTINEL`\
フィールドがセンチネルであることを示します。

`FIELD_MOD_INNERCLASS`\
フィールドが内部クラスであることを示します。

`FIELD_TYPE_OPTIONAL`\
フィールドが省略可能であることを示します。

`FIELD_MOD_BYREF`\
フィールドが参照引数であることを示します。 これは、メソッド引数に特化しています。

`FIELD_MOD_HIDDEN`\
フィールドを非表示にするか、別のコンテキストで表示する必要があることを示します。たとえば、[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]静的なローカル。

`FIELD_MOD_MARSHALASOBJECT`\
フィールドが`IUnknown`インターフェイスを持つオブジェクトを表すことを示します。

`FIELD_MOD_SPECIAL_NAME`\
フィールドに特殊な名前があることを示します (コンストラクター`.ctor`の[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]場合のみ)。

`FIELD_MOD_HIDEBYSIG`\
フィールドにキーワードが`Overloads`適用されていることを示します ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]のみ)。

`FIELD_MOD_WRITEONLY`\
フィールドが書き込み専用であることを示します。 この値は、このような書`FIELD_MOD_ALL`き込み専用フィールドの唯一の使用が関数評価のためであるため、に含まれていません。 ユーザーは、フィールドを明示的に`FIELD_MOD_WRITEONLY`要求する必要があります。

`FIELD_MOD_ACCESS_MASK`\
フィールド アクセス用のマスクを示します。

`FIELD_MOD_MASK`\
フィールド修飾子のマスクを示します。

## <a name="remarks"></a>Remarks
FIELD_INFO構造体の`dwModifiers`メンバーに使用[FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)されます。

これらの値は[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)メソッドにも渡され、特定のフィールドをフィルター処理します。

## <a name="requirements"></a>必要条件
ヘッダー: sh.h

名前空間: を使用します。

アセンブリ:

## <a name="see-also"></a>関連項目
- [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
