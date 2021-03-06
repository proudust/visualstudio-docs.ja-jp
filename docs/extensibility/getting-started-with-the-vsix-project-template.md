---
title: VSIX プロジェクト テンプレートの使用開始 |マイクロソフトドキュメント
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 773e9e6891599cd9672888d0521e94891e0d9f41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711240"
---
# <a name="get-started-with-the-vsix-project-template"></a>VSIX プロジェクト テンプレートの使用を開始する

VSIX プロジェクト テンプレートを使用して、拡張機能を作成したり、既存の拡張機能をパッケージ化して配置することができます。 VSIX プロジェクト テンプレートには、Visual Basic と Visual C# の両方のバージョンがあり、Visual Studio SDK の一部としてインストールされます。

 VSIX プロジェクト テンプレートは、単に、拡張とそれが出荷する資産に関する情報を含む*source.extension.vsixmanifest*ファイルで構成されています。

 VSIX プロジェクト テンプレートを検索するには、Visual Studio SDK をインストールする必要があります。 詳細については、「 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)」を参照してください。

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>VSIX プロジェクト テンプレートを使用してカスタム プロジェクト テンプレートを配置する

 次の手順では、VSIX プロジェクトを使用して、他の開発者と共有したり、Visual Studio ギャラリーにアップロードできるプロジェクト テンプレートをパッケージ化する方法を示します。

1. プロジェクト テンプレートを作成します。

    1. テンプレートの作成元となるプロジェクトを開きます。 このプロジェクトは、任意の種類のプロジェクトにできます。

    2. **[プロジェクト]** メニューの **[テンプレートのエクスポート]** をクリックします。 ウィザードの手順を完了します。

         *.zip*ファイルは *、%USERPROFILE%\マイ ドキュメント\Visual Studio {バージョン}\マイ\\エクスポート テンプレートに作成されます*。

2. 空の VSIX プロジェクトを作成します。

     [**ファイルの** > **新規作成** > **] をクリック**します。 検索ボックスに「vsix」と入力し **、C#** または**Visual Basic**バージョンの**VSIX プロジェクト**を選択します。

3. *.zip*ファイルをプロジェクトに追加します。 **[出力ディレクトリにコピー]** プロパティ`Copy Always`を に設定します。

4. **ソリューション エクスプローラー**で *、source.extension.vsixmanifest*ファイルをダブルクリックして**VSIX マニフェスト デザイナー**で開き、次の変更を行います。

    - [**製品名]** フィールドを **[マイ プロジェクト テンプレート]** に設定します。

    - **[製品 ID]** フィールドを **[MyProjectTemplate - 1]** に設定します。

    - **作成者**フィールドを **[Fabrikam]** に設定します。

    - [**説明]** フィールドを **[マイ プロジェクト テンプレート]** に設定します。

    - [**資産]** **セクションで、** 種類を追加し、そのパスを *.zip*ファイルの名前に設定します。

5. *ファイル*を保存して閉じます。

6. プロジェクトをビルドします。

7. 出力ディレクトリで *、.vsix*ファイルをダブルクリックします。

8. **VSIX インストーラー**のメッセージ ボックスが表示されます。 指示に従って拡張機能をインストールします。

9. Visual Studio をいったん閉じて開きなおします。

::: moniker range="vs-2017"

10. [**ツール]** メニューの **[拡張機能と更新プログラム**] を選択し、[**テンプレート**] カテゴリを選択します。 使用可能な拡張子の 1 つは、**マイ プロジェクト テンプレート である**必要があります。

::: moniker-end

::: moniker range=">=vs-2019"

10. **[拡張機能の管理**] **([拡張機能**] メニュー) を選択し、[**テンプレート]** カテゴリを選択します。 使用可能な拡張子の 1 つは、**マイ プロジェクト テンプレート である**必要があります。

::: moniker-end

11. 新しいプロジェクト テンプレートが[**新規プロジェクト**]ダイアログに、元のプロジェクト テンプレートと同じ場所に表示されます。 たとえば、Visual Basic コンソール アプリケーションから**VB コンソール**という名前のテンプレートを作成した場合 **、VB コンソール**は Visual Basic コンソール**アプリケーション**テンプレートと同じウィンドウに表示されます。

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>[新しいプロジェクト] ダイアログ ボックスでテンプレートの場所を指定するには

1. テンプレート フォルダーは *、{Visual Studio インストール パス}\Common7\IDE\プロジェクト テンプレート*および *{Visual Studio インストール パス}\Common7\IDE\ItemTemplates*ディレクトリにあります。 **[新しいプロジェクト**] ダイアログボックスの最上位セクションの名前が、テンプレートフォルダの名前と正確に一致しません。 異なる場合は、テンプレート フォルダの名前を使用します。

    *.vsix*ファイル拡張子を *.zip*に変更し、ファイルを開きます。

2. テンプレートを表示する[新規プロジェクト]ダイアログボックスのセクションと同じ名前の**新しい**フォルダを作成します。

3. テンプレートがサブセクションに表示される場合は、同じ名前のサブフォルダーを作成します。

4. テンプレートの *.zip*ファイルを新しいフォルダに移動します。

5. *.zip*拡張子を *.vsix*に変更します。

6. VSIX マニフェストを開きます。

7. VSIX マニフェストで、テンプレート ファイルが含まれるディレクトリ ツリーのルートを指す、テンプレートの**Asset**パスを更新します。 たとえば、テンプレートが*\CSharp\Windows*にある場合、参照は*\CSharp*を指す必要があります。
