---
title: スキーマキャッシュ |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d590bf618693a5ced1aa17969b888c0fff130c4c
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476954"
---
# <a name="schema-cache"></a>スキーマ キャッシュ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML エディターはスキーマ キャッシュを提供します。このキャッシュは %InstallRoot%\Xml\Schemas ディレクトリに配置されています。 スキーマ キャッシュはコンピューター上のすべてのユーザーに対してグローバルで、IntelliSense と XML ドキュメントの検証に使用される標準的な XML スキーマを格納しています。

 XML エディターでは、ソリューションに配置されているスキーマ、ドキュメントの [**プロパティ**] ウィンドウの [**スキーマ**] フィールドで指定したスキーマ、および `xsi:schemaLocation` 属性と `xsi:noNamespaceSchemaLocation` 属性で識別されるスキーマも検索できます。

 次の表では XML エディターと共にインストールされるスキーマについて説明します。

|     ファイル名      |                                                      説明                                                      |
|-------------------|-----------------------------------------------------------------------------------------------------------------------|
|    catalog.xsd    |             XML エディターのスキーマ カタログ ファイル用のスキーマです。 スキーマ カタログの詳細については、下記を参照してください。             |
| DotNetConfig.xsd  |                 Web.config ファイルのスキーマ、`http://schemas.microsoft.com/.NETConfiguration/v2.0`。                 |
|    msbuild.xsd    |              MSBuild の make ファイルのスキーマ、`http://schemas.microsoft.com/developer/msbuild/2003`。              |
|    msdata.xsd     | <xref:System.Data.DataSet> クラスによって追加される XSD 注釈用のスキーマ (urn:schemas-microsoft-com:xml-msdata) です。 |
|     msxsl.xsd     |                  Microsoft XSLT スクリプト ブロック拡張用のスキーマ (urn:schemas-microsoft-com:xslt) です。                   |
| SnippetFormat.xsd |                 コード スニペットの XML ファイルのスキーマです。 例については、%InstallDir%\VC#\Expansions を参照してください。                 |
|    Soap1.1.xsd    |            Simple Object Access Protocol (SOAP) 1.1 のスキーマ、`http://schemas.xmlsoap.org/soap/envelope/`。            |
|    Soap1.2.xsd    |                                     簡易オブジェクト アクセス プロトコル 1.2 のスキーマです。                                     |
| SiteMapSchema.xsd |            ASP.NET sitemap XML ファイルのスキーマ、`http://schemas.microsoft.com/AspNet/SiteMap-File-1.0`。             |
|     wsdl.xsd      |                    Web サービス記述言語のスキーマ、`http://schemas.xmlsoap.org/wsdl/`。                     |
|     xenc.xsd      |                            XML 暗号化のスキーマ、`http://www.w3.org/2000/09/xmldsig#`。                             |
|     xhtml.xsd     |                                    XHTML `http://www.w3.org/1999/xhtml`のスキーマ。                                     |
|     xlink.xsd     |                                  XLink 1.0 のスキーマ、`http://www.w3.org/1999/xlink`。                                   |
|      xml.xsd      |              Xml: space および xml: lang 属性、`http://www.w3.org/XML/1998/namespace`を記述するスキーマ。               |
|    xmlsig.xsd     |                        XML デジタル署名のスキーマ、`http://www.w3.org/2000/09/xmldsig#`。                         |
|   xsdschema.xsd   |                            XSD 自体、`http://www.w3.org/2001/XMLSchema`を記述するスキーマ。                            |
|     xslt.xsd      |                           XML 変換のスキーマ、`http://www.w3.org/1999/XSL/Transform`。                            |

## <a name="updating-schemas-in-the-cache"></a>キャッシュ内のスキーマの更新
 エディターは、XML エディター パッケージが読み込まれるときにスキーマ キャッシュのディレクトリを読み込み、実行中にはすべての変更点を監視します。 スキーマが追加された場合は、そのスキーマがメモリ内にある既知のスキーマのインデックス内に自働的に読み込まれます。 スキーマが削除された場合は、そのスキーマがメモリ内のインデックスから自働的に削除されます。 スキーマが更新された場合は、メモリ内にあるそのスキーマのキャッシュが自動的に無効化されます。

> [!NOTE]
> スキーマ キャッシュのディレクトリはコンピューター上でグローバルなので、このキャッシュには、コンピューター上で作成されるすべての Visual Studio プロジェクトに対して標準的かつ有用なスキーマのみを追加する必要があります。

 XML エディターはまた、スキーマ キャッシュ ディレクトリ内で任意の数のスキーマ カタログ ファイルをサポートします。 スキーマ カタログでは、エディターで常に認識しておきたいスキーマが存在する他の場所を指し示すことができます。 catalog.xsd ファイルはカタログ ファイルの形式を定義し、スキーマ キャッシュ ディレクトリに格納されています。 catalog.xml ファイルは既定のカタログで、%InstallDir% に存在する他のスキーマへのリンクが含まれています。 catalog.xml ファイルの例を次に示します。

```
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%InstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%InstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%InstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

 `href` 属性は、任意のファイル パスか、またはスキーマを指す http URL のいずれかになります。 ファイル パスとして、カタログ ドキュメントを基準にした相対パスを使用できます。 %% によって区切られる次の変数はエディターによって認識され、パス内で展開されます。

- InstallDir

- System

- ProgramFiles

- ［プログラム］

- CommonProgramFiles

- ApplicationData

- CommonApplicationData

- LCID

  カタログ ドキュメントには、他のカタログを指す `Catalog` 要素を含めることができます。 `Catalog` 要素を使用して、チームや会社で共有する集中管理カタログや、ビジネス パートナーと共有するオンライン カタログを指し示すことができます。 `href` 属性は、ファイル パスか、他のカタログの http URL です。 `Catalog` 要素の例を次に示します。

```
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

 カタログでは、特別な `Association` 要素を使用して、スキーマを XML ドキュメントと関連付ける方法を制御することもできます。 この要素は、ターゲット名前空間を持たないスキーマを、特定のファイル拡張子と関連付けます。XML エディターでは、`targetNamespace` 属性を持たないスキーマを自動的に関連付けすることはしないため、この機能が便利な場合があります。 `Association` 要素によって、dotNetConfig スキーマを "config" というファイル拡張子を持つすべてのファイルと関連付ける例を次に示します。

```
<Association extension="config" schema="%InstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>ローカライズされたスキーマ
 多くの場合、catalog.xml ファイルには、ローカライズされたスキーマのエントリは含まれません。 ローカライズされたスキーマのディレクトリを指し示す追加のエントリを catalog.xml ファイルに追加できます。

 次の例では、%LCID% 変数を使用してローカライズされたスキーマを指し示す新しい `Schema` 要素を作成します。

```xml
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="changing-the-location-of-the-schema-cache"></a>スキーマ キャッシュの場所の変更
 [**その他**のオプション] ページを使用して、スキーマキャッシュの場所をカスタマイズできます。 よく使用するスキーマのディレクトリがある場合は、それらのスキーマを代わりに使用するようにエディターを構成できます。

> [!NOTE]
> この変更によって影響を受けるのは、現在の Visual Studio ユーザーのみです。

#### <a name="to-change-the-schema-cache-location"></a>スキーマ キャッシュの場所を変更するには

1. 
          **[ツール]** メニューの **[オプション]** を選択します。

2. [**テキストエディター**]、[ **XML**] の順に展開し、[**その他**] をクリックします。

3. [**スキーマ**] フィールドの [**参照**] ボタンをクリックします。

4. スキーマキャッシュのフォルダーを選択し、[ **OK]** をクリックします。

#### <a name="to-add-another-directory-of-common-schemas"></a>よく使用するスキーマが存在するディレクトリを追加するには

1. XML エディターのスキーマ キャッシュ ディレクトリにある catalog.xml ファイルを編集します。

2. 追加するスキーマのディレクトリを指し示す新しい `<Catalog href="…"/>` 要素を追加します。

3. 変更を [保存] します。

     カタログは自動的に再度読み込まれます。

## <a name="see-also"></a>参照
 [XML エディター](../xml-tools/xml-editor.md)
