---
title: XML スキーマ エクスプローラー内での並べ替え、フィルター処理、およびグループ化
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd288171cd8713e6b403f71a4eee6ba09d3f6ea9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592517"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>並べ替え、フィルター処理、およびグループ化 (XML スキーマ エクスプローラー)

このトピックでは、**XML スキーマ エクスプローラー**のツール バーの **[並べ替え、フィルター処理、およびグループ化オプション]** メニューで使用できるオプションについて説明します。

## <a name="filter-options"></a>フィルター オプション

次のフィルター オプションがあります。 既定では、 **[名前空間の表示]** オプションと **[スキーマ ファイルの表示]** オプションが選択されます。

- **[名前空間の表示]** 。

- **[スキーマ ファイルの表示]** 。

- **[コンポジターの表示 (sequence/choice/all)]** 。

## <a name="sorting-options"></a>並べ替えオプション

次の並べ替えオプションがあります。 既定の設定は、 **[種類で並べ替え]** です。 ファイルと名前空間には、 **[並べ替え]** オプションは適用されません。

- **[種類で並べ替え]** 。

- **[名前で並べ替え]** 。

- **[ドキュメントの順序]** 。

### <a name="sort-by-type"></a>[種類で並べ替え]

**[種類で並べ替え]** オプションが選択されている場合、グローバル ノードは次の順序で並べ替えられます。 さらに、各グループ内でアルファベット順に並べ替えられます。

1. `import` ノード

2. `include` ノード

3. `redefine` ノード

4. `attribute` ノード

5. `attributeGroup` ノード

6. `complexType` ノード

7. `simpleType` ノード

8. `element` ノード

9. `group` ノード

### <a name="sort-by-name"></a>[名前で並べ替え]

**[名前で並べ替え]** オプションが選択されている場合、グローバル ノードは次の順序で並べ替えられます。

1. `import` ノード (名前空間のアルファベット順)。

2. `include` ノード (`schemaLocation` 属性のアルファベット順)

3. `redefine` ノード (`schemaLocation` 属性のアルファベット順)

4. その他のグローバル ノード (アルファベット順)

### <a name="document-order"></a>[ドキュメントの順序]

**[ドキュメントの順序]** オプションは、 **[スキーマ ファイルの表示]** オプションが選択されている場合に使用できます。 **[ドキュメントの順序]** が選択されている場合、グローバル ノードはスキーマ ファイル内での順序で表示されます。

## <a name="persisting-sortfilter-options"></a>並べ替えおよびフィルター オプションの保存

設定の変更時に開かれていたソリューションやファイルにかかわらず、並べ替え、フィルター処理、およびグループ化のオプションは各ユーザーのレジストリに保存されます。
