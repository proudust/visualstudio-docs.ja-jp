---
title: 使用コマンド要素 |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76732b2a9700f1737af495098c8c23aa4b618819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698751"
---
# <a name="usedcommands-element"></a>UsedCommands 要素
要素は、使用コマンド要素とその他の UsedCommands グループ化をグループ化します。

 要素は省略可能です。 パッケージの外部で定義されたコマンドを呼び出さない場合は、.vsct ファイルにこのセクションを含める必要はありません。

## <a name="syntax"></a>構文

```
<UsedCommands condition="Defined(DEBUG)">
  <UsedCommand ... />
</UsedCommands>
```

## <a name="attributes-and-elements"></a>属性および要素
 以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|条件|省略可能。 [「条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)」を参照してください。|

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|[UsedCommand 要素](../extensibility/usedcommand-element.md)|他のコードによって実装されるコマンド。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[CommandTable 要素](../extensibility/commandtable-element.md)|VSPackage が統合開発環境 (IDE) に提供するコマンド (メニュー項目、メニュー、ツールバー、コンボ ボックスなど) を表す要素をすべて定義します。|

## <a name="example"></a>例

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>関連項目
- [UsedCommand 要素](../extensibility/usedcommand-element.md)
- [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
