---
title: ジオメトリ シェイプのプロパティ
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c00fdf25b29c8a122347cf5261dfcbcb07d9415d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747453"
---
# <a name="properties-of-geometry-shapes"></a>ジオメトリ シェイプのプロパティ
Geometry 図形を使用して、ドメイン固有言語でドメインクラスのインスタンスをどのように表示するかを指定できます。 詳細については、「[ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)」を参照してください。 これらのプロパティの使用方法の詳細については、「[ドメイン固有言語のカスタマイズと拡張](../modeling/customizing-and-extending-a-domain-specific-language.md)」を参照してください。

 Geometry 図形には、次の表に示すプロパティがあります。

|property|説明|既定|
|-|-|-|
|[塗りつぶしの色]|この図形の塗りつぶしの色。|白|
|塗りつぶしのグラデーションモード|この図形の塗りつぶしのグラデーションモード (水平方向、垂直方向、左斜め、左上がり対角線、またはなし)。|[水平方向]|
|Geometry|この図形のジオメトリ (四角形、角丸四角形、楕円、または円)。|四角形|
|既定の接続ポイントがある|@No__t_0 した場合、図形は生成されたデザイナーで top、bottom、left、および right の各接続ポイントを使用します。|False|
|輪郭の色|この図形の輪郭の色。|黒|
|輪郭の破線のスタイル|この図形の輪郭の破線のスタイル (実線、ダッシュ、ドット、ダッシュドット、ダッシュ Dotドット、またはカスタム)。|[実線]|
|アウトラインの太さ|この図形の輪郭の太さ。|0.03125|
|テキストの色|この図形に関連付けられているテキストデコレーターに使用される色。|黒|
|アクセス修飾子|クラスのアクセス修飾子 (public または internal)。|Public|
|カスタム属性|この図形に対して生成されるソースコードクラスに属性を追加するために使用します。|\<none>|
|2つの派生を生成します|@No__t_0 場合、基本クラスと部分クラス (オーバーライドによるカスタマイズをサポートする) の両方が生成されます。 詳細については、「[生成されたクラスのオーバーライドと拡張](../modeling/overriding-and-extending-the-generated-classes.md)」を参照してください。|False|
|カスタムコンストラクターがある|@No__t_0 すると、カスタムコンストラクターがソースコードに提供されます。 詳細については、「[生成されたクラスのオーバーライドと拡張](../modeling/overriding-and-extending-the-generated-classes.md)」を参照してください。|False|
|継承修飾子|図形から生成されるソースコードクラスの継承の種類 (`none`、`abstract` または `sealed`) について説明します。|none|
|基本ジオメトリシェイプ|この図形の基本クラス。|(なし)|
|名|この図形の名前。|現在の名前|
|Namespace|この図形に関連付けられている名前空間。|現在の名前空間|
|ツールヒントの種類|ツールヒントがどのように定義されているか (fixed、variable、none)。 固定されている場合は、`Fixed Tooltip Text` プロパティの値がツールヒントとして使用されます。変数の場合、ツールヒントはカスタムコードで定義されます。|None|
|ノート|この要素に関連付けられている非公式のメモ。|\<none>|
|初期の高さ|この図形の初期の高さ (インチ単位)。|1|
|初期の幅|この図形の初期の幅 (インチ単位)。|1.5|
|プロパティとして塗りつぶされた塗りつぶしの色<br /><br /> 露出塗りつぶしのグラデーションモード<br /><br /> プロパティとして公開されたアウトラインの色<br /><br /> プロパティとしてアウトラインの破線のスタイルを公開<br /><br /> プロパティとしてアウトラインの太さを公開<br /><br /> テキストの色を公開します|@No__t_0 した場合、ユーザーは図形の指定されたプロパティを設定できます。 これを設定するには、図形定義を右クリックし、 **[公開の追加]** をクリックします。|False|
|説明|生成されたデザイナーを文書化するために使用される説明。|\<none>|
|[表示名]|この図形に対して生成されたデザイナーに表示される名前。|\<none>|
|固定ツールヒントのテキスト|固定のツールヒントに使用されるテキスト。|\<none>|
|ヘルプ キーワード|この図形の F1 ヘルプのインデックスを作成するために使用されるキーワード。|\<none>|

## <a name="see-also"></a>関連項目

- [ドメイン固有言語ツールの用語集](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)