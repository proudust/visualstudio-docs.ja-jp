---
title: プロジェクトテンプレートリンク要素マイクロソフトドキュメント
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6d402b6605f2e01a20d400c2c33573c686a1cdd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701817"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink 要素 (Visual Studio テンプレート)
複数プロジェクトのテンプレート内の 1 つのプロジェクトの *.vstemplate*ファイルへのパスを指定します。

 \<プロジェクト\<テンプレート>\<プロジェクト コレクション\<>プロジェクト テンプレート>> \<-または\<VSTemplate \<> テンプレート\<> プロジェクト\<> コレクション>ソリューション フォルダ>プロジェクト テンプレート リンク>

## <a name="syntax"></a>構文

```xml
<ProjectTemplateLink ProjectName="Name">
    PathToTemplateFile
</ProjectTemplateLink>
```

## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|`ProjectName`|省略可能な属性です。<br /><br /> 複数プロジェクトのテンプレートにある各プロジェクトに個別の名前を指定します。 [**新しいプロジェクト**] ダイアログ ボックスでは、個々のプロジェクトに名前を割り当てることはできません。|
|`CopyParameters`|メインのグループ テンプレート内のすべての変数を、リンクされたテンプレートそれぞれにコピーできるようにします。<br /><br /> リンクされたテンプレート内のパラメーターには、プレフィックス `"$ext_*$"` が付きます。 たとえば、親グループ テンプレートに値**ExampleProject1**が設定`$projectname$`されている場合、リンクされたテンプレートが実行される順番を取得すると、親グループ テンプレートから`$ext_projectname$``$projectname$`パラメーターのコピーであるパラメーター が取得されます。<br /><br /> これにより、リンクされたテンプレートは、親のグループ テンプレートでのみ簡単に作成できる一部の共通パラメーターを共有できるようになります。<br /><br /> この属性は省略可能であり、省略した場合は自動的に `false` に設定されます。<br /><br /> Visual Studio 2013 更新プログラム 2 で導入されました。 正しい製品バージョンを参照するには[、「Visual Studio 2013 SDK 更新 2 で提供される参照アセンブリ](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb)」を参照してください。|

### <a name="child-elements"></a>子要素
 [なし] :

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|複数プロジェクトのテンプレートの構成と内容を指定します。|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|複数プロジェクトのテンプレートをグループ化します。|

## <a name="text-value"></a>テキスト値
 テキスト値が必要です。

 このテキストは、テンプレートの *.vstemplate*ファイルへのパスを指定します。

## <a name="remarks"></a>Remarks
 複数プロジェクトのテンプレートは、2 つ以上のプロジェクトのコンテナーとして機能します。 要素`ProjectTemplateLink`は、テンプレート内のプロジェクトの 1 つに対する *.vstemplate*ファイルの場所を指定するために使用されます。 複数プロジェクトのテンプレートの *.vstemplate*ファイルには、`ProjectTemplateLink`テンプレート内のプロジェクトごとに 1 つの要素が含まれています。 複数プロジェクトのテンプレートの詳細については、「[方法 : 複数プロジェクト テンプレートを作成する](../ide/how-to-create-multi-project-templates.md)」を参照してください。

## <a name="example"></a>例
 この例では、単純な複数プロジェクトのルート *.vstemplate*ファイルを示します。 この例では、テンプレートには `My Windows Application` と `My Class Library` の 2 つのプロジェクトが含まれています。 `ProjectName` 要素の `ProjectTemplateLink` 属性は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がこのプロジェクトに割り当てる名前を設定します。 属性が`ProjectName`存在しない場合は *、.vstemplate*ファイルの名前がプロジェクト名として使用されます。

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>関連項目
- [Visual Studio テンプレート スキーマ リファレンス](../extensibility/visual-studio-template-schema-reference.md)
- [プロジェクト テンプレートと項目テンプレートを作成する](../ide/creating-project-and-item-templates.md)
- [方法: 複数プロジェクトテンプレートを作成する](../ide/how-to-create-multi-project-templates.md)
