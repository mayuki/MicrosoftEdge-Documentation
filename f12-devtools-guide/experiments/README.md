<!-- # F12 Experiments -->
# F12 試験的機能

<!-- F12 experiments can be activated from the **Experiments** tab which is the last tab along the navigation bar along the top of F12. After enabling an experiment you’ll need to close F12 and Microsoft Edge for the change to take effect. --> 

F12 試験的機能はF12の上部にあるナビゲーションバーの最後のタブである**Experiments**タブで有効にできます。試験的機能を有効にした後、変更を反映するにはF12とMicrosoft Edgeを閉じる必要があります。

<!-- ## Experiment: Edit JavaScript -->
## 試験的機能: JavaScriptの編集

<!-- With this experiment enabled you can edit any JavaScript file in the debugger source viewer. Simply click on the viewer to place the cursor and type away. -->

この試験的機能を有効にするとデバッガーのソースビューアーでJavaScriptファイルを変更できるようになります。ビューアーをクリックしてカーソルを合わせて文字を打つだけです。

![Edge Experiment Tab](../media/Edge_Experiments_edit.gif)

<!-- As you make edits you will notice a dirty flag, an **asterisk (*)**, in the document’s tab which implies that the document has changed but has not yet been saved. -->

変更を加えるとダーティーフラグに気づくと思います。ドキュメントのタブの**アスタリスク (*)**はドキュメントが変更されているもののまだ保存されていないということを示しています。

![Edge Experiment Flag](../media/Edge_Experiment_flag.png)

<!-- Your edits can then be applied to the page by pressing the save icon or using the keyboard shortcut CTRL + S. -->

編集は保存アイコンまたはキーボードショートカットのCTRL + Sでページに反映できます。

![Edge Experiment Save](../media/Edge_Experiment_save.png)

<!-- Once saved, you will be able to compare the modified document to the original document using the **diff** command.  -->

保存すると、**diff**コマンドを使うことで編集後のドキュメントとオリジナルのドキュメントを比較することができます。

![Edge Experiment Diff](../media/Edge_Experiment_diff.png)

<!-- Clicking the **diff** command will open up a new **diff view** of the document, highlighting any changes. *Note that you will not be able to edit code in the **diff view**, but can do so by switching back to the original file on the tab bar.  -->

**diff**コマンドをクリックすると新しくドキュメントの**diffビュー**が開かれ、変更した点がハイライトされます。*なお、**diffビュー**ではコードの編集はできないことに注意してください。タブバーから元のファイルに戻すことは可能です。*

![Edge Experiment Diff View](../media/Edge_Experiment_diff_view.png)

<!-- All changes to the document will be lost when you navigate away or refresh from the current page. -->

ドキュメントに対するすべての変更は現在のページを離れるか再読み込みをすると失われます。

<!-- You will not be able to edit when paused in the **[Debugger](../debugger/)** or when a document has been pretty printed.  -->

**[デバッガー](../debugger/)**で一時停止中またはドキュメントがpretty printされている場合、編集することはできません。