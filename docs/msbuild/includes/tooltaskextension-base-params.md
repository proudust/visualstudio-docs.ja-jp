---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: 40108f56ee9d64688fc665fdef0e0ab731bddfff
ms.sourcegitcommit: 596f92fcc84e6f4494178863a66aed85afe0bb08
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2020
ms.locfileid: "82204596"
---
### <a name="tooltaskextension-parameters"></a>ToolTaskExtension パラメーター

このタスクが <xref:Microsoft.Build.Tasks.ToolTaskExtension> クラスを継承します。このクラスは <xref:Microsoft.Build.Utilities.ToolTask> クラスから継承され、さらに、このクラス自体は <xref:Microsoft.Build.Utilities.Task> から継承されます。 この継承チェーンにより、これらのクラスから派生したタスクにいくつかのパラメーターが追加されます。

基本クラスのパラメーターの説明を次の表に示します。

| パラメーター | 説明 |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | 省略可能な `bool` 型のパラメーターです。<br /><br /> `true` に設定すると、このタスクは **/Q** を *cmd.exe* コマンド ラインに渡して、コマンド ラインが stdout にコピーされないようにします。 |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | 省略可能な `String` 型の配列パラメーターです。<br /><br /> 等号で区切られた環境変数のペアの配列です。 これらの変数は、標準の環境ブロックに加え (または標準の環境ブロックを選択的にオーバーライドして)、子の実行可能ファイルに渡されます。 |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | 省略可能な `Int32` 型の読み取り専用出力パラメーターです。<br /><br /> 実行したコマンドの終了コードを示します。 タスクがエラーを記録した一方で、プロセスの終了コードが 0 (成功) だった場合、これは -1 に設定されます。 |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | 省略可能な `bool` 型のパラメーターです。<br /><br /> `true` の場合、標準エラー ストリームで受け取ったすべてのメッセージがエラーとして記録されます。 |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | 省略可能な `bool` 型のパラメーターです。<br /><br /> `true` の場合、標準エラー ストリームで受け取ったすべてのメッセージがエラーとして記録されます。 |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | 省略可能な `String` 型のパラメーターです。<br /><br /> 標準出力ストリームのテキストを記録するときに使用する重要度です。 |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | 省略可能な `String` 型のパラメーターです。<br /><br /> 標準出力ストリームのテキストを記録するときに使用する重要度です。 |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | 省略可能な `Int32` 型のパラメーターです。<br /><br /> タスク実行を終了するまでの時間をミリ秒単位で指定します。 既定値は `Int.MaxValue` であり、タイムアウト期限がないことを示します。 タイムアウトはミリ秒単位です。 |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | 省略可能な `string` 型のパラメーターです。<br /><br /> プロジェクトで実装すると、ToolName をオーバーライドできます。 タスクでオーバーライドすると、ToolName を保持できます。 |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | 省略可能な `string` 型のパラメーターです。<br /><br /> タスクで基になる実行可能ファイルを読み込む場所を指定します。 このパラメーターを指定しない場合、タスクでは、MSBuild を実行しているフレームワークのバージョンに対応する SDK インストール パスが使用されます。 |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | 省略可能な `bool` 型のパラメーターです。<br /><br /> `true` に設定した場合、このタスクで直接コマンドを実行する代わりに、コマンド ラインのバッチ ファイルを作成し、そのファイルをコマンド プロセッサで実行します。 |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | 省略可能な `bool` 型のパラメーターです。<br /><br /> `true` に設定した場合、このタスクは、その実行時にノードを生成します。 |
