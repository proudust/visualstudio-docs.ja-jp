---
title: 'チュートリアル: コンテンツコントロールを使用してテンプレートを作成する'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ffb7d7f9ad5453d38709802bf5e004c07bb09622
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255582"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>チュートリアル: コンテンツコントロールを使用してテンプレートを作成する
  このチュートリアルでは、コンテンツ コントロールを使用して、Microsoft Office Word テンプレートで構造化された再利用可能なコンテンツを作成するための、ドキュメント レベルのカスタマイズを作成する方法について説明します。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word では、*ビルドブロック*という名前の再利用可能なドキュメントパーツのコレクションを作成できます。 このチュートリアルでは、文書パーツとして 2 つの表を作成する方法を説明します。 各表には、プレーン テキストや日付などさまざまな種類のコンテンツを保持できる、複数のコンテンツ コントロールが含まれます。 表の 1 つには従業員に関する情報が含まれ、もう一方の表には顧客からのフィードバックが含まれています。

 テンプレートからドキュメントを作成した後に、複数の <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> オブジェクトを使用して、いずれかの表をドキュメントに追加できます。これらのオブジェクトには、テンプレート内で使用できる文書パーツが表示されます。

 このチュートリアルでは、次の作業について説明します。

- デザイン時に Word テンプレートで、コンテンツ コントロールが含まれる表を作成する。

- プログラムを使用して、コンボ ボックス コンテンツ コントロールおよびドロップダウン リスト コンテンツ コントロールのデータを読み込む。

- 特定の表を保護してユーザーが編集できないようにする。

- 表をテンプレートの文書パーツ コレクションに追加する。

- テンプレートで使用可能な文書パーツを表示するコンテンツ コントロールを作成する。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必須コンポーネント
 このチュートリアルを実行するには、次のコンポーネントが必要です。

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-a-new-word-template-project"></a>新しい Word テンプレートプロジェクトを作成する
 ユーザーが独自のコピーを簡単に作成できるように、Word テンプレートを作成します。

### <a name="to-create-a-new-word-template-project"></a>新しい Word テンプレート プロジェクトを作成するには

1. **MyBuildingBlockTemplate**という名前の Word テンプレートプロジェクトを作成します。 ウィザードで、ソリューション内に新しいドキュメントを作成します。 詳細については、「[方法 :Visual Studio で Office プロジェクトを作成する方法](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]デザイナーで新しい Word テンプレートを開き、**ソリューションエクスプローラー**に**MyBuildingBlockTemplate**プロジェクトを追加します。

## <a name="create-the-employee-table"></a>Employee テーブルを作成する
 ユーザーが従業員に関する情報を入力できる 4 種類のコンテンツ コントロールが含まれる表を作成します。

### <a name="to-create-the-employee-table"></a>従業員表を作成するには

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]デザイナーでホストされている Word テンプレートで、リボンの **[挿入]** タブをクリックします。

2. **[テーブル]** グループで、 **[テーブル]** をクリックし、2つの列と4つの行を含むテーブルを挿入します。

3. 最初の列に次のようにテキストを入力します。

   ||
   |-|
   |**従業員名**|
   |**入社日**|
   |**タイトル**|
   |**図**|

4. 2番目の列の最初のセル ( **[Employee Name]** の横) をクリックします。

5. リボンの **[開発]** タブをクリックします。

   > [!NOTE]
   > **[開発]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、「[方法 :リボン](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)に [開発者] タブを表示します。

6. **[コントロール]** グループの **[テキスト]** ボタン![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl")をクリックし<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>て、最初のセルにを追加します。

7. 2番目の列の2番目のセル ( **[入社日]** の横) をクリックします。

8. **[コントロール]** グループの **[日付の選択]** ボタン![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl")をクリック<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>して、2番目のセルにを追加します。

9. 2番目の列の3番目のセル ( **[タイトル]** の横) をクリックします。

10. **[コントロール]** グループで、**コンボボックス**ボタン![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl")をクリックして<xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> 、3番目のセルにを追加します。

11. 2番目の列の最後のセル ( **[画像]** の横) をクリックします。

12. **[コントロール]** グループで、 **[画像コンテンツコントロール]** ボタンをクリックして![[contentcontrol]](../vsto/media/pictcontentcontrol.gif "をクリック")し、最後のセルにを<xref:Microsoft.Office.Tools.Word.PictureContentControl>追加します。

## <a name="create-the-customer-feedback-table"></a>カスタマーフィードバックテーブルを作成する
 ユーザーが顧客のフィードバック情報を入力できる 3 種類のコンテンツ コントロールが含まれる表を作成します。

### <a name="to-create-the-customer-feedback-table"></a>顧客フィードバック表を作成するには

1. Word テンプレートで、前の手順で追加した employee テーブルの後の行をクリックし、 **enter**キーを押して新しい段落を追加します。

2. リボンの **[挿入]** タブをクリックします。

3. **[テーブル]** グループの **[テーブル]** をクリックし、2つの列と3つの行を含むテーブルを挿入します。

4. 最初の列に次のようにテキストを入力します。

   ||
   |-|
   |**顧客名**|
   |**満足度評価**|
   |**コメント**|

5. 2番目の列の最初のセル ( **[Customer Name]** の横) をクリックします。

6. リボンの **[開発]** タブをクリックします。

7. **[コントロール]** グループの **[テキスト]** ボタン![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl")をクリックし<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>て、最初のセルにを追加します。

8. 2番目の列の2番目のセル ( **[満足度評価]** の横) をクリックします。

9. **[コントロール]** グループの**ドロップダウンリスト**ボタン [ ![dropdownlistcontentcontrol](../vsto/media/dropdownlist.gif "dropdownlistcontentcontrol") ] をクリックして<xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 、2番目のセルにを追加します。

10. 2番目の列の最後のセル ( **[コメント]** の横) をクリックします。

11. **[コントロール]** グループの **[リッチテキスト]** ボタン![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl")をクリックし<xref:Microsoft.Office.Tools.Word.RichTextContentControl>て、最後のセルにを追加します。

## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>プログラムによるコンボボックスとドロップダウンリストの設定
 の [ [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**プロパティ**] ウィンドウを使用すると、デザイン時にコンテンツコントロールを初期化できます。 また、実行時に初期化することも可能で、これにより、コンテンツ コントロールを動的に初期の状態に設定できます。 このチュートリアルでは、コードを使用して、 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>および<xref:Microsoft.Office.Tools.Word.DropDownListContentControl>実行時にエントリを入力し、これらのオブジェクトの動作を確認できるようにします。

### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>コンテンツ コントロールの UI をプログラムで変更するには

1. **ソリューションエクスプローラー**で、 **ThisDocument.cs**または**ThisDocument**を右クリックし、[コードの**表示**] をクリックします。

2. `ThisDocument` クラスに次のコードを追加します。 このコードは、このチュートリアルの後半で使用するいくつかのオブジェクトを宣言します。

     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]

3. `ThisDocument_Startup` クラスの `ThisDocument` メソッドに次のコード行を追加します。 このコードは表の <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> と <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> にエントリを追加し、ユーザーがコンテンツ コントロールを編集する前に、各コントロールに表示されるプレースホルダー テキストを設定します。

     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]

## <a name="prevent-users-from-editing-the-employee-table"></a>ユーザーが employee テーブルを編集できないようにする
 先ほど宣言した <xref:Microsoft.Office.Tools.Word.GroupContentControl> オブジェクトを使用して、従業員表を保護します。 表を保護した後でも、ユーザーは表内のコンテンツ コントロールを編集できます。 ただし、最初の列のテキストを編集したり、他の方法で表を変更すること (行や列を追加/削除するなど) はできません。 を<xref:Microsoft.Office.Tools.Word.GroupContentControl>使用してドキュメントの一部を保護する方法の詳細については、「[コンテンツコントロール](../vsto/content-controls.md)」を参照してください。

### <a name="to-prevent-users-from-editing-the-employee-table"></a>従業員表を保護してユーザーが編集できないようにするには

1. `ThisDocument` クラスの `ThisDocument_Startup` メソッドに (前の手順で追加したコードの後ろに) 次のコードを追加します。 このコードにより、先ほど宣言した <xref:Microsoft.Office.Tools.Word.GroupContentControl> オブジェクト内に表を配置することで、ユーザーが従業員表を編集できないようにします。

     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]

## <a name="add-the-tables-to-the-building-block-collection"></a>文書パーツコレクションにテーブルを追加する
 作成した表をユーザーがドキュメントに挿入できるように、テンプレート内の文書パーツ コレクションに表を追加します。 ドキュメントの構成要素の詳細については、「[コンテンツコントロール](../vsto/content-controls.md)」を参照してください。

### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>テンプレートの文書パーツに表を追加するには

1. `ThisDocument` クラスの `ThisDocument_Startup` メソッドに (前の手順で追加したコードの後ろに) 次のコードを追加します。 このコードは、テーブルを含む新しいビルディングブロックを BuildingBlockEntries コレクションに追加します。このコレクションには、テンプレート内の再利用可能なすべての構成要素が含まれています。 新しい構成要素は、 **Employee および Customer Information**という名前の新しいカテゴリに定義され、文書パーツ`Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`の種類が割り当てられます。

     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]

2. `ThisDocument` クラスの `ThisDocument_Startup` メソッドに (前の手順で追加したコードの後ろに) 次のコードを追加します。 このコードは、テンプレートから、表を削除します。 表は、テンプレートの再利用可能な文書パーツのギャラリーに追加されたため、もう必要ありません。 コードは最初にドキュメントをデザイン モードにして、保護されている従業員表を削除できるようにします。

     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]

## <a name="create-a-content-control-that-displays-the-building-blocks"></a>構成要素を表示するコンテンツコントロールを作成する
 先ほど作成した文書パーツ (表) へのアクセスを提供するコンテンツ コントロールを作成します。 ユーザーはこのコントロールをクリックして、ドキュメントに表を追加できます。

### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>文書パーツを表示するコンテンツ コントロールを作成するには

1. `ThisDocument` クラスの `ThisDocument_Startup` メソッドに (前の手順で追加したコードの後ろに) 次のコードを追加します。 このコードは先ほど宣言した <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> オブジェクトを初期化します。 に<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>は、[**従業員] および [顧客情報**] というカテゴリに定義されているすべての`Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`構成要素と、文書パーツの種類が表示されます。

     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]

## <a name="test-the-project"></a>プロジェクトをテストする
 ユーザーはドキュメント内の文書パーツ ギャラリー コントロールをクリックして、従業員表や顧客フィードバック表を挿入できます。 ユーザーは、両方の表内のコンテンツ コントロールで、応答を入力または選択できます。 ユーザーは顧客フィードバック表の他の部分を変更できますが、従業員表の他の部分を変更できてはなりません。

### <a name="to-test-the-employee-table"></a>従業員表をテストするには

1. **F5** キーを押してプロジェクトを実行します。

2. [**最初のビルディングブロックを選択**する] をクリックして、最初の文書パーツギャラリーコンテンツコントロールを表示します。

3. コントロールの **[カスタムギャラリー 1]** 見出しの横にあるドロップダウン矢印をクリックし、 **[Employee Table]** を選択します。

4. **[Employee name]** セルの右側にあるセルをクリックし、名前を入力します。

     このセルにテキストのみを追加できることを確認します。 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> により、ユーザーはテキストのみを追加でき、アートや表など他の種類のコンテンツは追加できません。

5. **[入社日]** セルの右側にあるセルをクリックし、日付の選択で日付を選択します。

6. **タイトル**セルの右側にあるセルをクリックし、コンボボックスでいずれかのジョブタイトルを選択します。

     必要に応じて、リストに含まれていない役職名を入力します。 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> ではユーザーがエントリの一覧から選択することも、独自のエントリを入力することもできるため、このようなケースが生じることがあります。

7. **画像**セルの右側にあるセルのアイコンをクリックし、画像を参照して表示します。

8. 表に行や列を追加できるか、また、表から行や列を削除できるか、試してみます。 表を変更できないことを確認します。 <xref:Microsoft.Office.Tools.Word.GroupContentControl> により、表は変更できないようになっています。

### <a name="to-test-the-customer-feedback-table"></a>顧客フィードバック表をテストするには

1. [ **2 番目の文書パーツを選択**する] をクリックして、2つ目のビルドブロックギャラリーコンテンツコントロールを表示します。

2. コントロールの **[カスタムギャラリー 1]** 見出しの横にあるドロップダウン矢印をクリックし、 **[Customer Table]** を選択します。

3. **[Customer Name]** セルの右側にあるセルをクリックし、名前を入力します。

4. **満足度評価**セルの右側にあるセルをクリックし、使用可能なオプションの1つを選択します。

     独自のエントリを入力できないことを確認します。 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> では、ユーザーはエントリの一覧から選択することのみが可能です。

5. **[コメント]** セルの右側にあるセルをクリックし、コメントを入力します。

     必要に応じて、アートや、埋め込み表など、テキスト以外のコンテンツを追加します。 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ではユーザーがテキスト以外のコンテンツを追加できるため、このようなケースが生じることがあります。

6. 表に行や列を追加できること、また、表から行や列を削除できることを確認します。 表を <xref:Microsoft.Office.Tools.Word.GroupContentControl> に配置して保護していないため、表への変更が可能です。

7. テンプレートを閉じます。

## <a name="next-steps"></a>次の手順
 コンテンツ コントロールの使用方法の詳細については、次の各トピックを参照してください。

- コンテンツ コントロールを、文書に埋め込まれている XML の一部 (「カスタム XML 部分」とも呼ばれます) にバインドします。 詳細については、「[チュートリアル:コンテンツコントロールをカスタム XML 部分](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)にバインドします。

## <a name="see-also"></a>関連項目
- [拡張オブジェクトを使用した Word の自動化](../vsto/automating-word-by-using-extended-objects.md)
- [コンテンツコントロール](../vsto/content-controls.md)
- [方法: Word 文書にコンテンツコントロールを追加する](../vsto/how-to-add-content-controls-to-word-documents.md)
- [方法: コンテンツコントロールを使用してドキュメントの一部を保護する](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [ホスト項目とホストコントロールの概要](../vsto/host-items-and-host-controls-overview.md)
- [ホスト項目とホストコントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [実行時に Office ドキュメントにコントロールを追加する](../vsto/adding-controls-to-office-documents-at-run-time.md)
