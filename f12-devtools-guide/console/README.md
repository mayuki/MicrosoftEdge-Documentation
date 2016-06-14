# コンソールツール

**コンソール**ツールを利用することで、エラーとその他メッセージを表示、デバッグ出力の送信、JavaScriptオブジェクトとXMLノードの調査、そして選択中のウィンドウまたはフレームのコンテキストでJavaScriptを実行できます。

## コードへのウィンドウ

**コンソール**ツールの主な利用目的は表示中のWebページの内と外のコミュニケーションです。

![Edge Console](../media/Edge_Console.gif)

*上の画像ではページの再読み込みのためのJavaScriptコマンドを入力し、IntelliSense自動コード補完が表示されています。reloadメソッドが選択されると、ページが再読み込みされコンソールにJavaScriptのデバッグメッセージを出力されます。*

   - **入力:** JavaScriptを実行することで表示中のWebページの値を表示や変更したり、実行中のコードに機能を追加したり、その場でデバッグコードを実行したりでき、その間ずっとMicrosoft Edge [IntelliSense](https://msdn.microsoft.com/en-us/library/hcw1s69b.aspx)自動コード補完の恩恵を受けることができます。

   - **出力:** Microsoft EdgeとJavaScriptコードはステータスやエラー、デバッグメッセージを調査可能なJavaScriptオブジェクトとDOMノードを含めて開発者へ届けます。

### Microsoft Edgeがコンソールに送信するメッセージ

コンソールは3つのカテゴリーを持ちます:
   - **エラー:** コードの実行ができない致命的なエラーです。もっと詳しい情報はコンソールで使われている[エラーコード](./console-error-and-status-codes)の一覧を参照してください
   - **警告:** Webページのエラーだと考えられますが、必ずしも動作しないわけではないものの予期せぬ挙動が発生するかもしれません
   - **情報:** 致命的ではなく、知りたいことがあるかもしれない情報です

![Console System Messages](../media/Edge_Console_messages.gif)

これらのメッセージはコンソール出力の外側でフィルターできます。コンソールペインの上部にあるメッセージごとのアイコンはトグルとなっています。アイコンをクリックすると関連したメッセージの種類が削除され、もう一度クリックすると戻ります。また、コンソール出力を右クリックしするとコンテキストメニューにそれぞれの種類のチェックボックスを見つけることもできます。

メッセージの後にあるファイル名をクリックすると、**[デバッガー](../debugger/)**ツールを開いてスクリプトペインでファイルを読み込みます。

**Clear on navigate**アイコンが選択されていると、ブラウザーが新しいWebページに移動するたびにコンソールはクリアされます。選択されてない場合はブラウザーは**コンソール**の内容を維持します。しかし以前のページのメッセージは現在のページからのものではないことを明示するためにグレーアウトされます。

### 実行ターゲットを選択する
**コンソール**には**コンソール**出力ペインの真上に**ターゲット**ドロップダウンメニューがあります。もし表示中のWebページに[iframe要素]()を含んでいるのであれば、**ターゲット**メニューからiframeを選択することで、**コンソール**コマンドをiframeのスコープで実行できます。Webページにiframeがない場合には"_top"のみを選択できます。

![Console System Messages](../media/Edge_Console_toggles.gif)

*上の画像ではターゲットiframeを選択し、エラーメッセージを表示するためにページを再読み込みし、ファイル名をクリックすることでデバッガーでスクリプトファイルのエラーを追いかけます。コンソールに戻り、エラーコード自体をクリックすると、エラーコードに関するドキュメントページが開きます。*

### JavaScriptをコンソールに送る

コンソールはコードからの出力を表示するだけではなく、コードをいい感じに実行するためのインターフェースも提供しています。任意の正しいJavaScriptをコンソールの一番下のコマンドラインペインに入力するだけです。

![F12 Console Command Line](../media/Edge_Console_command.gif)

普段はコマンドラインに入力されたすべてのスクリプトは現在選択中のウィンドウの[グローバルスコープ](https://msdn.microsoft.com/en-us/library/bzt2dkta.aspx)です。
しかし、もしスクリプトが中断中(例えばブレークポイントをセットしていた場合)であれば、スクリプトはコールスタックの中の現在の関数の[ローカルスコープ](https://msdn.microsoft.com/en-us/library/bzt2dkta.aspx)で実行されます。

![F12 Console Command Line local scope](../media/Edge_Console_local_scope.png)

もしWebページが**[frameset](https://msdn.microsoft.com/en-us/library/ms535251.aspx)**または**[iframes](https://msdn.microsoft.com/en-us/library/ms535258.aspx)**で作られているならば、それぞれのフレームは各ウィンドウごとに各ドキュメントをロードします。

framesetのフレームまたはiframeのウィンドウをターゲットとするには、frame/iframeの名前またはID属性を引数にして`cd()`コマンドを呼び出します。例えば、microsoftFrameという名前のフレームがあり、Microsoftのホームを表示しているとします。

   **JavaScript**
   ```js
   cd(microsoftFrame);
   ```
   ```
   Current window: www.microsoft.com/en-us/default.aspx
   ```

**重要** フレームの名前の前後にはクォートがないことに注意してください。クォートなしの名前またはID値のみをパラメータとして渡します。
トップレベルのウィンドウに戻るには、引数なしで`cd()`を呼び出します。

### コンソールで要素を選択する
コンソールセレクターはDOM構造から要素を素早く選択するための単純な短縮記述を提供します。

   - **$()** は [**`document.querySelector()`**](https://msdn.microsoft.com/en-us/library/cc288169.aspx) の短縮記述
   - **$$()** は [**`document.querySelectorAll()`**](https://msdn.microsoft.com/en-us/library/cc304115.85.aspx) の短縮記述
   - **$_()** は最後に選択した要素またはオブジェクトの短縮記述
   - **$0, $1, $2, $3, $4** は[**DOM Explorer ツール**](../dom-explorer/)で最後に選択したアイテム

**重要** もしWebページのコードが**$**または**$$**に関数を割り当てている場合、そのページまたはフレームのコンソールと対話している間はその関数がコンソールセレクターを上書きします。

### 複数行コマンドライン

一行コマンドを送るのは便利ですが、中には作業では長いスクリプトを実行する必要となることもあります。
その場合には二つの上矢印マークをクリックすればコマンドラインを広げることができます。複数行モードではたくさんの行を必要なだけ入力でき、緑色の矢印マークをクリックすればコンソールで実行されます。

![F12 Console Multiline Command Line](../media/f12blueconsolecommandmultiple.png)

## Related topics
[Using the Console API](./using-the-console-api/)

