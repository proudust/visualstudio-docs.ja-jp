---
title: '方法: 予約済みの XML 文字をプロジェクト ファイルで使用する | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a041802af1c2fe8cfa195990e6eda3e9b49d773a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633773"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>方法: 予約済みの XML 文字をプロジェクト ファイルで使用する

プロジェクト ファイルを作成するときに、たとえばプロパティ値やタスク パラメーター値の中で、予約済み XML 文字を使用する必要が生じることがあります。 しかし、いくつかの予約文字は、プロジェクト ファイルを解析できるようにするために、名前付きエンティティに置き換える必要があります。

## <a name="use-reserved-characters"></a>予約文字を使用する

 次の表は、プロジェクト ファイルを解析できるようにするために、対応する名前付きエンティティに置き換える必要がある予約済み XML 文字を示しています。

|予約文字|名前付きエンティティ|
|------------------------|------------------|
|\<|&amp;lt;|
|>|&amp;gt;|
|&|&amp;amp;|
|"|&amp;quot;|
|' を返します。|&amp;apos;|

#### <a name="to-use-double-quotes-in-a-project-file"></a>プロジェクト ファイルで二重引用符を使用するには

- 二重引用符を対応する名前付きエンティティ &amp;quot; に置き換えます。 たとえば、`EXEFile` 項目リストを二重引用符で囲むには、次のように入力します。

    ```xml
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    ```

## <a name="example"></a>例

 次のコード例では、プロジェクト ファイルによって出力されるメッセージの中でファイル名を強調するために二重引用符が使用されています。

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>"HelloWorldCS"</appname>
    </PropertyGroup>
    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs" />
    </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input
        files of type CSFile -->
        <Csc Sources = "@(CSFile)">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile"/>
        </Csc>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    </Target>
</Project>
```

## <a name="see-also"></a>参照

- [MSBuild リファレンス](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
