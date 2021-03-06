---
title: コードにマニフェスト |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 17ecacea-397d-4a97-b003-01bd5d56e936
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 768561ef289f0f652f082d40ee9856843721f1ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707270"
---
# <a name="manifest-to-code"></a>Manifest to Code
マニフェストからコードへのツールは、Visual Studio イメージ サービスの .imagemanifest ファイルを受け取り、Visual Studio 拡張機能の C++ 、C#、VB、または .vsct ファイルでイメージ マニフェストの値を参照するためのラッパー ファイルを生成するコンソール アプリケーションです。 このツールは、Visual Studio イメージ サービスからイメージを直接要求したり、コードが独自の UI とレンダリングを処理しない場合に API を通じてマニフェスト値を渡すために使用できるラッパー ファイルを生成します。

## <a name="how-to-use-the-tool"></a>ツールの使用方法
 **構文**

 マニフェストコード /マニフェスト:\<イメージ マニフェスト ファイル>\</言語\<: コード言語>オプションの引数>

 **引数**

||||
|-|-|-|
|**スイッチ名**|**メモ**|**必須またはオプション**|
|/マニフェスト|コード ラッパーの作成または更新に使用するイメージ マニフェストへのパス。|必須|
|/言語|コード ラッパーを生成する言語。<br /><br /> 有効な値: CPP、C++、CS、CSharp、C#、VB、または VSCT 値は大文字と小文字を区別しません。<br /><br /> VSCT 言語オプションの場合、/モニカークラス、/クラスアクセス、および /名前空間の各オプションは無視されます。|必須|
|/イメージIdクラス|ツールによって作成された imageIdClass と関連ファイルの名前。 C++ 言語オプションの場合、.h ファイルのみが生成されます。<br /><br /> デフォルト:\<マニフェスト パス>\MyImageIds。\<ラング・エクス>|Optional|
|/モニカークラス|ツールによって作成された monikerClass と関連ファイルの名前。 C++ 言語オプションの場合、.h ファイルのみが生成されます。 VSCT 言語では無視されます。<br /><br /> デフォルト:\<マニフェストパス>\MyMonikers。\<ラング・エクス>|Optional|
|/クラスアクセス|イメージ Id クラスとモニカー クラスのアクセス修飾子。 アクセス修飾子が指定された言語に対して有効であることを確認します。 VSCT 言語オプションでは、このオプションは無視されます。<br /><br /> デフォルト: パブリック|Optional|
|/名前空間|コード ラッパーで定義されている名前空間。 VSCT 言語オプションでは、このオプションは無視されます。 '.' または ':' は、選択した言語オプションに関係なく、有効な名前空間の区切り文字です。<br /><br /> デフォルト: マイイメージ|Optional|
|/noLogo|このフラグを設定すると、製品および著作権情報の印刷が停止します。|Optional|
|/?|ヘルプ情報を印刷します。|Optional|
|/help|ヘルプ情報を印刷します。|Optional|

 **使用例**

- マニフェストコード /マニフェスト:D:\MyManifest.イメージマニフェスト /言語:CSharp

- マニフェストコード /マニフェスト:D:\MyManifest.imagemanifest /言語:C++ /名前空間:マイ:名前空間 /イメージIdクラス:マイイメージIds /モニカークラス:マイモニカー/クラスアクセス:フレンド

- マニフェストコード /マニフェスト:D:\MyManifest.イメージマニフェスト /言語:VSCT /イメージIdクラス:マイイメージIds

## <a name="notes"></a>Notes

- このツールは、リソースツールのマニフェストによって生成されたイメージ マニフェストで使用することをお勧めします。

- このツールは、コード ラッパーを生成するシンボル エントリのみを参照します。 イメージ マニフェストにシンボルが含まれている場合、生成されたコード ラッパーは空になります。 イメージ マニフェストにシンボルを使用しないイメージまたはイメージのセットがある場合、それらはコード ラッパーから除外されます。

## <a name="sample-output"></a>サンプル出力
 **C# ラッパー**

 C# の単純なイメージ ID とイメージ モニカークラスのペアは、次のコードのようになります。

```csharp
//-----------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by the ManifestToCode tool.
//     Tool Version: 14.0.15198
// </auto-generated>
//-----------------------------------------------------------------------------

using System;

namespace MyImages
{
    public static class MyImageIds
    {
        public static readonly Guid AssetsGuid = new Guid("{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}");

        public const int MyImage1 = 0;
        public const int MyImage2 = 1;
    }
}
//-----------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by the ManifestToCode tool.
//     Tool Version: 14.0.15198
// </auto-generated>
//-----------------------------------------------------------------------------

using Microsoft.VisualStudio.Imaging.Interop;

namespace MyImages
{
    public static class MyMonikers
    {
        public static ImageMoniker MyImage1 { get { return new ImageMoniker { Guid = MyImageIds.AssetsGuid, Id = MyImageIds.MyImage1 }; } }
        public static ImageMoniker MyImage2 { get { return new ImageMoniker { Guid = MyImageIds.AssetsGuid, Id = MyImageIds.MyImage2 }; } }
    }
}
```

 **C++ ラッパー**

 C++ の単純なイメージ ID とイメージ モニカークラスのペアは、次のコードのようになります。

```cpp
//-----------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by the ManifestToCode tool.
//     Tool Version: 14.0.15198
// </auto-generated>
//-----------------------------------------------------------------------------

#pragma once

#include <guiddef.h>

namespace MyImages {

class MyImageIds {
public:

    static const GUID AssetsGuid;

    static const int MyImage1 = 0;
    static const int MyImage2 = 1;

};

__declspec(selectany) const GUID MyImageIds::AssetsGuid = {0x442d8739,0xefde,0x46a4,{0x8f,0x29,0xe3,0xa1,0xe5,0xe7,0xf8,0xb4}};

}
//-----------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by the ManifestToCode tool.
//     Tool Version: 14.0.15198
// </auto-generated>
//-----------------------------------------------------------------------------

#pragma once

#include "ImageParameters140.h"
#include "MyImageIds.h"

namespace MyImages {

class MyMonikers {
public:

    static const ImageMoniker MyImage1;
    static const ImageMoniker MyImage2;

};

__declspec(selectany) const ImageMoniker MyMonikers::MyImage1 = { MyImageIds::AssetsGuid, MyImageIds::MyImage1 };
__declspec(selectany) const ImageMoniker MyMonikers::MyImage2 = { MyImageIds::AssetsGuid, MyImageIds::MyImage2 };

}
```

 **ビジュアルベーシックラッパー**

 Visual Basic の単純なイメージ ID とイメージ モニカークラスのペアは、次のコードのようになります。

```vb
' -----------------------------------------------------------------------------
'  <auto-generated>
'      This code was generated by the ManifestToCode tool.
'      Tool Version: 14.0.15198
'  </auto-generated>
' -----------------------------------------------------------------------------

Imports System

Namespace MyImages

    Public Module MyImageIds

        Public Shared ReadOnly AssetsGuid As Guid = New Guid("{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}")

        Public Const MyImage1 As Integer = 0
        Public Const MyImage2 As Integer = 1

    End Module

End Namespace
' -----------------------------------------------------------------------------
'  <auto-generated>
'      This code was generated by the ManifestToCode tool.
'      Tool Version: 14.0.15198
'  </auto-generated>
' -----------------------------------------------------------------------------

Imports Microsoft.VisualStudio.Imaging.Interop

Namespace MyImages

    Public Module MyMonikers

        Public Readonly Property MyImage1
            Get
                Return New ImageMoniker With {.Guid = MyImageIds.AssetsGuid, .Id = MyImageIds.MyImage1}
            End Get
        End Property

        Public Readonly Property MyImage2
            Get
                Return New ImageMoniker With {.Guid = MyImageIds.AssetsGuid, .Id = MyImageIds.MyImage2}
            End Get
        End Property

    End Module

End Namespace
```

 **VSCT ラッパー**

 vsct ファイルのイメージ ID のセットは、次のようになります。

```xml
<?xml version='1.0' encoding='utf-8'?>
<!--
- [auto-generated]
     This code was generated by the ManifestToCode tool.
     Tool Version: 14.0.15198
- [/auto-generated]
-->
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
  <Symbols>
    <GuidSymbol name="AssetsGuid" value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}">
      <IDSymbol name="MyImage1" value="0" />
      <IDSymbol name="MyImage2" value="1" />
    </GuidSymbol>
  </Symbols>
</CommandTable>
```
