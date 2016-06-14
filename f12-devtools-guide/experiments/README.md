# F12 試験的機能

F12 試験的機能はF12の上部にあるナビゲーションバーの最後のタブである**Experiments**タブで有効にできます。試験的機能を有効にした後、変更を反映するにはF12とMicrosoft Edgeを閉じる必要があります。

## 試験的機能: JavaScriptの編集

この試験的機能を有効にするとデバッガーのソースビューアーでJavaScriptファイルを変更できます。ビューアーをクリックしてカーソルを合わせて文字を打つだけです。

![Edge Experiment Tab](../media/Edge_Experiments_edit.gif)

変更を加えるとダーティーフラグに気づくと思います。ドキュメントのタブの**アスタリスク (*)**はドキュメントが変更されているもののまだ保存されていないということを示しています。

![Edge Experiment Flag](../media/Edge_Experiment_flag.png)

編集は保存アイコンまたはキーボードショートカットのCTRL + Sでページに反映できます。

![Edge Experiment Save](../media/Edge_Experiment_save.png)

保存すると、**diff**コマンドを使うことで編集後のドキュメントとオリジナルのドキュメントを比較できます。

![Edge Experiment Diff](../media/Edge_Experiment_diff.png)

**diff**コマンドをクリックすると新しくドキュメントの**diffビュー**が開かれ、変更した点がハイライトされます。*なお、**diffビュー**ではコードの編集はできないことに注意してください。タブバーから元のファイルに戻すことは可能です。*

![Edge Experiment Diff View](../media/Edge_Experiment_diff_view.png)

ドキュメントに対するすべての変更は現在のページを離れるか再読み込みをすると失われます。

**[デバッガー](../debugger/)**で一時停止中またはドキュメントがpretty printされている場合は編集できません。

## Related topics

[Microsoft Edge Developer Tools on Twitter: Find helpful F12 hints and news updates](https://twitter.com/EdgeDevTools)
