---
title: MODULE_INFO |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59ab4d0bb2a7aaa4b08f616ea0a99be85b521bb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714311"
---
# <a name="module_info"></a>MODULE_INFO
特定のモジュール (DLL、EXE、またはアセンブリ) について説明します。

## <a name="syntax"></a>構文

```cpp
typedef struct tagMODULE_INFO { 
   MODULE_INFO_FIELDS dwValidFields;
   BSTR               m_bstrName;
   BSTR               m_bstrUrl;
   BSTR               m_bstrVersion;
   BSTR               m_bstrDebugMessage;
   UINT64             m_addrLoadAddress;
   UINT64             m_addrPreferredLoadAddress;
   DWORD              m_dwSize;
   DWORD              m_dwLoadOrder;
   FILETIME           m_TimeStamp;
   BSTR               m_bstrUrlSymbolLocation;
   MODULE_FLAGS       m_dwModuleFlags;
} MODULE_INFO;
```

```csharp
public struct MODULE_INFO { 
   public uint     dwValidFields;
   public string   m_bstrName;
   public string   m_bstrUrl;
   public string   m_bstrVersion;
   public string   m_bstrDebugMessage;
   public ulong    m_addrLoadAddress;
   public ulong    m_addrPreferredLoadAddress;
   public uint     m_dwSize;
   public uint     m_dwLoadOrder;
   public FILETIME m_TimeStamp;
   public string   m_bstrUrlSymbolLocation;
   public uint     m_dwModuleFlags;
};
```

## <a name="members"></a>メンバー
 `dwValidFields`\
 入力するフィールドを指定する[MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)列挙体のフラグの組み合わせ。

 `m_bstrName`\
 モジュール名。

 `m_bstrUrl`\
 モジュールの URL。

 `m_bstrVersion`\
 モジュールのバージョン。

 `m_bstrDebugMessage`\
 モジュールに関するオプションのメッセージ(例: 「シンボルを読み込めません。.」)。

 `m_addrLoadAddress`\
 モジュールのロード アドレス。

 `m_addrPreferredLoadAddress`\
 モジュールの優先ロード アドレス。

 `m_dwSize`\
 モジュールのサイズ。

 `m_dwLoadOrder`\
 モジュールの読み込み順序。

 `m_TimeStamp`\
 シンボル ファイルが最後に変更された時刻。

 `m_bstrUrlSymbolLocation`\
 モジュールで指定されたシンボル ファイルの場所\\("" など)。 モジュールのシンボルを検索する開始位置として使用されます。

 `m_dwModuleFlags`\
 モジュールを説明する[MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)列挙体のフラグの組み合わせ。

## <a name="remarks"></a>Remarks
 この構造体は[、GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)メソッドに渡され、そこで格納されます。

 この構造体は、[モジュール] ウィンドウに表示される各**モジュール**に対応します。

## <a name="requirements"></a>必要条件
 ヘッダー: msdbg.h

 名前空間: を使用します。

 アセンブリ:

## <a name="see-also"></a>関連項目
- [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
