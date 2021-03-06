---
title: テンプレート ディレクトリの説明 (.Vsdir) ファイル |マイクロソフトドキュメント
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16ba609d5b05d565a12b38bd19e9a777851ced5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704689"
---
# <a name="template-directory-description-vsdir-files"></a>テンプレート ディレクトリの説明 (.Vsdir) ファイル
テンプレート ディレクトリ記述ファイル (.vsdir) は、統合開発環境 (IDE) がダイアログ ボックスでプロジェクトに関連付けられているフォルダー、ウィザード .vsz ファイル、およびテンプレート ファイルを表示できるようにするテキスト ファイルです。 内容には、ファイルまたはフォルダごとに 1 つのレコードが含まれます。 参照先の場所にあるすべての .vsdir ファイルはマージされますが、複数のフォルダ、ウィザード、またはテンプレート ファイルを記述するために提供される .vsdir ファイルは 1 つだけです。

 フォルダ (サブディレクトリ)、.vsdir ファイルで参照されるファイル、および .vsdir ファイル自体はすべて同じディレクトリに格納されます。 ウィザードを実行するか、または **[新しいプロジェクト**] ダイアログ ボックスまたは [**新しい項目の追加**] ダイアログ ボックスにフォルダまたはファイルを表示すると、実行されたファイルが格納されているディレクトリが調べ、.vsdir ファイルが存在するかどうかを確認します。 .vsdir ファイルが見つかった場合、IDE は、実行または表示されるフォルダーまたはファイルのエントリが含まれているかどうかを判断するために、ファイルを読み取ります。 エントリが見つかった場合、IDE はウィザードの実行またはコンテンツの表示の情報を使用します。

 次のコード例は\<、EnvSDK>\BscPrj\BscPrj\BscPrjProjectItems\Source_Files レジストリ キーのファイルソース ファイル.vsdir から取得されています。

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 この場合、2 つのレコードが 1 つのファイルに入っています。 改行 (復帰文字) は、各レコードを区切ります。 各行は、異なるファイルの種類を表します。 パイプ (&#124;) 文字は、各レコードのフィールドを区切ります。 1 つのディレクトリに、異なるファイル名を持つ複数の .vsdir ファイルを含めることも、ファイルの種類ごとに 1 つの .vsdir ファイルを含めることもできます。

## <a name="fields"></a>フィールド
 次の表は、各レコードに指定されたフィールドの一覧です。

| フィールド | 説明 |
| - | - |
| 相対パス名 (相対パス名) | フォルダー、テンプレート、または .vsz ファイルの名前 (HeaderFile.h や MyWizard.vsz など)。 このフィールドには、フォルダーを表す名前を指定することもできます。 |
| {clsidPackage} | ローカライズされた文字列へのアクセスを有効にする VSPackage の GUID ( ローカライズされた名前、説明、アイコンリソース Id、および推奨されるベース名など ) は、VSPackage の衛星ダイナミック リンク ライブラリ (DLL) リソース内で使用されます。 DLL パスが指定されていない場合に適用されます。 **注:** 前のフィールドの 1 つ以上がリソース識別子でない限り、このフィールドはオプションです。 このフィールドは、テキストをローカライズしないサード パーティのウィザードに対応する .vsdir ファイルの場合は、通常は空白になります。 |
| LocalizedName | テンプレート ファイルまたはウィザードのローカライズされた名前。 このフィールドには、"#ResID" 形式の文字列またはリソース識別子を指定できます。 この名前は、[**新しい項目の追加**] ダイアログ ボックスに表示されます。 **注:** ローカライズ名がリソース識別子の場合は、{clsidPackage} が必要です。 |
| SortPriority | このテンプレート ファイルまたはウィザードの相対的な優先順位を表す整数。 たとえば、この項目の値が 1 の場合、このアイテムは、値が 1 の他のアイテムの横に表示され、並べ替え値が 2 以上のすべての項目の前に表示されます。<br /><br /> 並べ替えの優先順位は、同じディレクトリ内の項目に対する相対です。 同じディレクトリに複数の .vsdir ファイルが存在する可能性があります。 その場合<em>、すべての</em>.そのディレクトリ内の vsdir ファイルがマージされます。 同じ優先度の項目は、表示される名前の大文字小文字を区別しない辞書順でリストされます。 この`_wcsicmp`関数は、アイテムの順序付けに使用されます。<br /><br /> .vsdir ファイルに記載されていない項目には、.vsdir ファイルに記載されている優先度の最も高い番号よりも大きい優先度番号が含まれます。 結果として、これらの項目は、名前に関係なく、表示されるリストの末尾に表示されます。 |
| 説明 | テンプレート ファイルまたはウィザードのローカライズされた説明。 このフィールドには、"#ResID" 形式の文字列またはリソース識別子を指定できます。 この文字列は、項目が選択されている場合に **[新しいプロジェクト**]または **[新しい項目の追加**]ダイアログ ボックスに表示されます。 |
| DLLPath または {clsidPackage} | テンプレート ファイルまたはウィザードのアイコンを読み込むために使用します。 アイコンは、.dll ファイルまたは .exe ファイルからリソースとして読み込まれます。 この .dll ファイルまたは .exe ファイルは、完全パスを使用するか、VSPackage の GUID を使用して識別できます。 VSPackage の実装 DLL は、(サテライト DLL ではなく) アイコンを読み込むために使用されます。 |
| IconResourceId | 表示するアイコンを決定する DLL または VSPackage 実装 DLL 内のリソース識別子。 |
| フラグ<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>( ) | [**新しい項目の追加**] ダイアログ ボックスの **[名前**] フィールドと **[場所**] フィールドを無効または有効にします。 **Flags**フィールドの値は、必要なビット フラグの組み合わせに相当する 10 進数です。<br /><br /> ユーザーが **[新規**] タブで項目を選択すると、**プロジェクトは[新しい項目の追加**] ダイアログ ボックスが最初に表示されるときに [名前] フィールドと [場所] フィールドを表示するかどうかを決定します。 .vsdir ファイルを使用して、項目を選択したときにフィールドが有効か無効かを制御するアイテムだけです。 |
| SuggestedBaseName | ファイル、ウィザード、またはテンプレートの既定の名前を表します。 このフィールドは、"#ResID" 形式の文字列またはリソース識別子です。 IDE はこの値を使用して、項目のデフォルト名を指定します。 この基本値には、MyFile21.asp などの名前を一意にするために整数値が付加されます。<br /><br /> 前の一覧では、説明、DLLPath、アイコンリソース Id、フラグ、および推奨されるベース番号は、テンプレート ファイルとウィザード ファイルにのみ適用されます。 これらのフィールドは、フォルダーには適用されません。 この事実は、\<レジストリ キーの EnvSDK>\BscPrj\BscPrj\BscPrjProjectItems の BscPrj プロジェクト アイテム ファイルのコードに示されています。 このファイルには、各レコードに 4 つのフィールドを持つ 3 つのレコード (フォルダーごとに 1 つずつ) が含まれています。<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 ウィザード ファイルを作成する場合は、次の問題も考慮する必要があります。

- 意味のあるデータを持たない省略可能なフィールドには、プレースホルダーとして 0 (ゼロ) を格納する必要があります。

- ローカライズされた名前が指定されていない場合は、ウィザード ファイルで相対パス名が使用されます。

- DLLPath は、アイコンの場所の clsidPackage をオーバーライドします。

- アイコンが定義されていない場合、IDE はその拡張子を持つファイルの既定のアイコンに置き換えられます。

- 提案されたベース名が指定されていない場合は、'プロジェクト' が使用されます。

- .vsz ファイル、フォルダ、またはテンプレート ファイルを削除する場合は、.vsdir ファイルから関連付けられたレコードも削除する必要があります。

## <a name="see-also"></a>関連項目
- [ウィザード](../../extensibility/internals/wizards.md)
- [ウィザード (.Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)
