---
title: Idiasymbol::get_typeids |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 410f8afdac24139791c19c3936049c855a51d4f9
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2019
ms.locfileid: "64798169"
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このシンボルのコンパイラ固有の型識別子の値の配列を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cTypeIds`  
 [in]データを保持するバッファーのサイズ。  
  
 `pcTypeIds`  
 [out]数を返します`typeIds`書き込まれると、または、`typeIds`は`NULL`、使用可能な型識別子の総数、します。  
  
 `typeIds[]`  
 [out]型識別子を使用して格納する配列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
> 戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
