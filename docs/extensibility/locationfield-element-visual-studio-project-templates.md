---
title: ロケーションフィールド要素 (Visual Studio プロジェクト テンプレート) |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d993e84bec41486ef4dce6ad98c61f23ab2a46bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702884"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>場所フィールド要素
プロジェクト テンプレートの [**新しいプロジェクト**] ダイアログ ボックスの **[場所**] テキスト ボックスを有効にするか、無効にするか、非表示にするかを指定します。

 \<VS テンプレート\<>\<テンプレートデータ>ロケーション フィールド>

## <a name="syntax"></a>構文

```
<LocationField> Enabled/Disabled/Hidden </LocationField>
```

## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性
 [なし] :

### <a name="child-elements"></a>子要素
 [なし] :

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必須の要素です。<br /><br /> テンプレートを分類し、**新しいプロジェクト**での表示方法を定義します。|

## <a name="text-value"></a>テキスト値
 テキスト値が必要です。

 有効なテキスト値は次のとおりです。

- `Enabled`をクリックすると、[**新しいプロジェクト**] ダイアログ ボックスの **[場所**] ボックスが有効になります。

- `Disabled`を指定すると、[**新しいプロジェクト**] ダイアログ ボックスの **[場所**] ボックスが無効になります。

- `Hidden`をクリックすると、[**新しいプロジェクト**] ダイアログ ボックスの **[場所**] ボックスが非表示になります。

## <a name="remarks"></a>Remarks
 既定値は `Enabled` です。

 [**新しいプロジェクト**] ダイアログ ボックスの **[場所**] テキスト ボックスでは、新しいプロジェクトを保存する既定のディレクトリを変更できます。

 要素で指定された`Location`値は、基になるプロジェクト システムがサポートする場合にのみダイアログ ボックスで受け入れられます。

## <a name="example"></a>例
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] テンプレートのメタデータの例を次に示します。

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LocationField>Disabled</LocationField>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>関連項目
- [Visual Studio テンプレート スキーマ リファレンス](../extensibility/visual-studio-template-schema-reference.md)
- [プロジェクトテンプレートと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)
