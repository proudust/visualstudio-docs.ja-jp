---
title: VSIX 言語パックスキーマ2.0 リファレンス |Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: zorio
author: zoeyr
manager: jillfra
ms.openlocfilehash: f97fd5aee27cdc97cf6eb5731da9fad9cb999e18
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78169340"
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSIX 言語パックスキーマ2.0 リファレンス

VSIX 言語パックのスキーマには、VSIX パッケージのローカライズされたインストール情報が含まれています。 このスキーマのバージョン2.0 では、追加のローカライズ要素がサポートされています。

## <a name="language-pack-schema"></a>言語パックスキーマ

言語パックファイルのルート要素は、言語パック形式の `Version`の属性を持つ `<PackageLanguagePackManifest>`になります。 この記事では、`Version` 属性を `Version="2.0.0"`の値に設定することによって、マニフェストに指定されている言語パック形式のバージョン2.0 について説明します。 ルート要素には、子 `<Metadata>` 要素が1つだけ含まれます。

### <a name="packagelanguagepackmanifest-element"></a>PackageLanguagePackManifest 要素

`<PackageLanguagePackManifest>` 要素内には、次の要素が存在している必要があります。

|タイトル|説明|
|-----------|-----------------|
|`<Metadata>`| ローカライズされたすべてのパッケージメタデータのコンテナー要素

### <a name="metadata-element"></a>Metadata 要素

`<Metadata>` 要素内には、次の要素を含めることができます。

|タイトル|説明|
|-----------|-----------------|
|`<DisplayName>`|インストールする拡張機能のローカライズされた名前|
|`<Description>`|インストールする拡張機能のローカライズされた説明|
|`<License>`| 拡張機能のライセンスのローカライズ版へのパス|
|`<MoreInfo>`| 拡張機能に関するローカライズされた情報へのリンク|
|`<ReleaseNotes>`| リリースノートのパスまたはローカライズされたバージョンへのリンク|
|`<Icon>`| 拡張機能アイコンのローカライズ版へのパス|

### <a name="sample-manifest"></a>サンプルマニフェスト

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>参照

|タイトル|説明|
|-----------|-----------------|
|[VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)|VSIX パッケージのローカライズされたインストールをサポートする方法を示します。|
|[VSIX 拡張機能スキーマ2.0 リファレンス](../extensibility/vsix-extension-schema-2-0-reference.md)|VSIX マニフェストは、 *.vsix*配置ファイルの内容を記述します。 配置ファイルを使用すると、 **[拡張機能と更新プログラム]** ダイアログボックスを使用して、Visual Studio 拡張機能をインストールできます。|
|[Visual Studio 拡張機能の検索と使用](../ide/finding-and-using-visual-studio-extensions.md)|**[拡張機能と更新プログラム]** ダイアログボックスを使用して、拡張機能のインストール、削除、アクティブ化、および非アクティブ化を行う方法について説明します。|
