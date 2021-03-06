---
title: SEEK_START |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca1c38027123ca5147a6a7ab1fa6a3f92966409a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713600"
---
# <a name="seek_start"></a>SEEK_START
逆アセンブリ ストリームでシークを開始する位置を指定します。

## <a name="syntax"></a>構文

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
```

## <a name="fields"></a>フィールド
 `SEEK_START_BEGIN`\
 現在のドキュメントの先頭からシークを開始します。

 `SEEK_START_END`\
 現在のドキュメントの末尾からシークを開始します。

 `SEEK_START_CURRENT`\
 現在のドキュメントの現在位置でシークを開始します。

 `SEEK_START_CODECONTEXT`\
 現在のドキュメントの指定されたコード コンテキストでシークを開始します。

 `SEEK_START_CODELOCID`\
 指定されたコードの場所識別子でシークを開始します。 コードの場所の識別子は[、GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)を呼び出すことによって取得されます。

## <a name="remarks"></a>Remarks
 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)メソッドに引数として渡されます。

## <a name="requirements"></a>必要条件
 ヘッダー: msdbg.h

 名前空間: を使用します。

 アセンブリ:

## <a name="see-also"></a>関連項目
- [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
