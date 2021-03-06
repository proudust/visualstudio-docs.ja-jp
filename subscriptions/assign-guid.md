---
title: 特定の GUID を Visual Studio サブスクライバーに割り当てる | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/20/2020
ms.topic: conceptual
description: 管理者が特定のサブスクリプション GUID をサブスクライバーに割り当てる方法について説明します
ms.openlocfilehash: e2e8cd4f5d07f218fc23c0b7b6f28ababc25263f
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072594"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Visual Studio サブスクリプション管理ポータルで特定のサブスクリプションを割り当てる

管理者は、Visual Studio サブスクリプション管理ポータルを使用して、特定のサブスクリプションを個々のサブスクライバーに割り当てることができるようになりました。  これは、サブスクリプションへのアクセスを短期間だけ必要とする臨時スタッフやベンダーが組織に存在する場合に役立ちます。  管理者は、既に部分的に使用されているサブスクリプションを割り当てて、新しいサブスクリプションはより長期の使用のために残しておくことができます。  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>特定のサブスクリプション GUID をユーザーに割り当てる

特定のサブスクリプションを個人に割り当てるプロセスでは、既存の 2 つの管理プロセスを活用して、特定のサブスクリプション グローバル一意識別子 (GUID) を個々のユーザーに割り当てる必要があります。  3 段階のプロセスでは、現在のサブスクリプションと割り当ての一覧をエクスポートし、その一覧を使用して割り当てたい特定の GUID を特定し、そして一括追加プロセスを使用して新しい割り当てをアップロードします。

### <a name="export-your-subscriptions-information"></a>サブスクリプション情報をエクスポートする

エクスポートを実行するには、次の手順に従います。
1. [管理ポータル](https://manage.visualstudio.com)にサインインします。
2. **[エクスポート]** タブを選択します。ファイルがローカル コンピューターにダウンロードされます。 このファイルには、ユーザー サブスクリプションを含む割り当ての名前と、エクスポートの日付が含まれます。
> [!div class="mx-imgBorder"]
> ![サブスクライバーのエクスポート](_img/exporting-subscriptions/exporting-subscriptions.png)

### <a name="identify-the-guids-you-want-to-assign"></a>割り当てる GUID を特定する

エクスポート ツールを以前に使用したことがある場合は、生成されたスプレッドシートに新しいフィールドが追加されていることがわかります。  これらは、各サブスクリプションの状態を特定し、ユーザーに割り当てるものを決定するのに役立ちます。  

- **サブスクリプションの状態**: このフィールドには、"割り当て済み" または "未割り当て" が示されます。  サブスクリプションの状態が "割り当て済み" の場合、それには名前や電子メールなどのユーザー情報が関連付けられています。 
- **使用状態**: 使用状態は、"新規" (ユーザーに割り当てられたことがないことを示す) か、"使用済み" (ある時点でユーザーに割り当てられたことを示す) のいずれかとなります。  

これらのフィールド内の値をスプレッドシート内の他の情報と共に使用することで、個々のユーザーに割り当てるサブスクリプションを決定することができます。 Excel でフィルターを適用すれば、状態、サブスクリプション レベル、有効期限などによって、一覧を容易に絞り込むことができます。 

### <a name="upload-your-new-assignments"></a>新しい割り当てをアップロードする

最後の手順は、**一括追加**テンプレートをダウンロードし、割り当てたいサブスクリプションに対して必要な情報を入力して、テンプレートをアップロードするというものです。  このプロセスの詳細については、[複数のユーザーへの割り当て](assign-license-bulk.md)に関する記事を参照してください。  

> [!IMPORTANT]
> アップロードを確実に行うには、次のことを確認してください。
> - **[一括追加]** を選択するとき、ダイアログ ボックスでリンクされているテンプレートを使用しています。  テンプレートのローカルに保存されているコピーは使用しないでください。必須フィールドの一部が含まれていない可能性があります。  古いテンプレートを使用すると、アップロードに失敗します。 
> - テンプレート内で**必須**として表示されているすべてのフィールドが完成している。
> - **エラー メッセージ**列にエラーがリストされていない。
> - テンプレート内で各 GUID が 1 回だけ使用されている。 
> - テンプレートのサブスクリプション レベルが、エクスポート リスト内の GUID のサブスクリプションと一致している。 
> - GUID が、エクスポート リスト内の別のユーザーにまだ割り当てられていない。 

## <a name="frequently-asked-questions"></a>よく寄せられる質問
### <a name="qhow-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>Q: 個々のユーザーへのサブスクリプションの現在の割り当てを変更するにはどうすればよいですか。
A: ユーザーへの GUID の割り当てを変更する場合は、まずそのユーザーのサブスクリプションを削除する必要があります。  詳細については、[サブスクリプションの削除](delete-license.md)に関するページを参照してください。  そのユーザーのサブスクリプションを削除したら、上記のプロセスを使用してリストをエクスポートし、新しいサブスクリプション情報をアップロードします。  

## <a name="see-also"></a>関連項目
- [Visual Studio ドキュメント](/visualstudio/)
- [Azure DevOps ドキュメント](/azure/devops/)
- [Azure ドキュメント](/azure/)
- [Microsoft 365 ドキュメント](/microsoft-365/)

## <a name="next-steps"></a>次の手順
ユーザーにサブスクリプションを割り当てたので、他の管理タスクを実行する方法について確認します。
- [個別のサブスクリプションの割り当て](assign-license.md)
- [複数のサブスクリプションを管理する](assign-license-bulk.md)
- [サブスクリプションの編集](edit-license.md)
- [サブスクリプションの削除](delete-license.md)
- [最大使用量の確認](maximum-usage.md)


