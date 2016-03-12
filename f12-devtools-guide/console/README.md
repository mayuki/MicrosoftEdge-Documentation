<!-- # Console Tool -->
# コンソールツール

<!-- Use the **Console** tool to view errors and other messages, send debug output, inspect JavaScript objects and XML nodes, and to run JavaScript in the context of the selected window or frame. -->

**コンソール**ツールを利用することで、エラーとその他メッセージを表示、デバッグ出力の送信、JavaScriptオブジェクトとXMLノードの調査、そして選択中のウィンドウまたはフレームのコンテキストでJavaScriptを実行できます。

<!-- ## A window into your code -->
## コードへのウィンドウ

<!-- The primary use for the **Console** tool is to communicate into and out of running webpages. -->

**コンソール**ツールの主な利用目的は表示中のWebページの内と外のコミュニケーションです。

![Edge Console](../media/Edge_Console.gif)

<!-- *In the image above, as the JavaScript command to reload the page is entered in, the IntelliSense auto code completion pops up. Once the reload method is selected, the page reloads and the console sends JavaScript debugging messages out.* -->

*上の画像ではページの再読み込みのためのJavaScriptコマンドを入力し、IntelliSense自動コード補完が表示されています。reloadメソッドが選択されると、ページが再読み込みされコンソールにJavaScriptのデバッグメッセージを出力されます。*

<!-- 
   - **In:** Run JavaScript to view and change values in running webpages, add functions to running code, and run debug code on the fly, all while taking advantage of the Microsoft Edge [IntelliSense](https://msdn.microsoft.com/en-us/library/hcw1s69b.aspx) auto code completion.
   - **Out:** Microsoft Edge and JavaScript code deliver status, error, and debug messages to developers, including inspectable JavaScript objects and DOM Nodes. For more on how to send debug information and other messages to the console from your code, read up on [Using the Console API](./using-the-console-api/).
-->

   - **入力:** JavaScriptを実行することで表示中のWebページの値を表示や変更したり、実行中のコードに機能を追加したり、その場でデバッグコードを実行したりでき、その間ずっとMicrosoft Edge [IntelliSense](https://msdn.microsoft.com/en-us/library/hcw1s69b.aspx)自動コード補完の恩恵を受けることができます。

   - **出力:** Microsoft EdgeとJavaScriptコードはステータスやエラー、デバッグメッセージを調査可能なJavaScriptオブジェクトとDOMノードを含めて開発者へ届けます。

<!-- ### Messages Microsoft Edge sends to the console -->
### Microsoft Edgeがコンソールに送信するメッセージ

<!-- The Console has three categories: -->

コンソールは3つのカテゴリーを持ちます:

<!--
   - **Error:** Critical errors that cause code not to run. For more info, see a list of [error codes](./console-error-and-status-codes) used in the console.
   - **Warning:** Possible errors in your webpage that don't necessarily break it, but may cause unexpected behavior.
   - **Information:** Non-critical information you might want to know.
-->
   - **エラー:** コードの実行ができない致命的なエラーです。もっと詳しい情報はコンソールで使われている[エラーコード](./console-error-and-status-codes)の一覧を参照してください
   - **警告:** Webページのエラーだと考えられますが、必ずしも動作しないわけではないものの予期せぬ挙動が発生するかもしれません
   - **情報:** 致命的ではなく、知りたいことがあるかもしれない情報です

![Console System Messages](../media/Edge_Console_messages.gif)

<!-- These messages can be filtered out of the Console output. The icons for each message type at the top of the Console pane act as toggles. Click one to remove its associated message type, then again to return it. You can also right-click in the Console output and find check boxes for each type in the context menu. -->

これらのメッセージはコンソール出力の外側でフィルターできます。コンソールペインの上部にあるメッセージごとのアイコンはトグルとなっています。アイコンをクリックすると関連したメッセージの種類が削除され、もう一度クリックすると戻ります。また、コンソール出力を右クリックしするとコンテキストメニューにそれぞれの種類のチェックボックスを見つけることもできます。

<!-- When you click the file name that follows a message, you open the **[Debugger](../debugger/)** tool and load the file in the script pane. -->

メッセージの後にあるファイル名をクリックすると、**[デバッガー](../debugger/)**ツールを開いてスクリプトペインでファイルを読み込みます。

<!-- When the **Clear on navigate** icon is highlighted, the console clears every time the browser navigates to a new webpage. When it isn't highlighted, the browser preserves the contents of the **Console**, but messages from prior webpages are grayed out to better visually indicate they are not from the current page. -->

**Clear on navigate**アイコンが選択されていると、ブラウザーが新しいWebページに移動するたびにコンソールはクリアされます。選択されてない場合はブラウザーは**コンソール**の内容を維持します。しかし以前のページのメッセージは現在のページからのものではないことを明示するためにグレーアウトされます。

<!-- ### Selecting your execution target -->
### 実行ターゲットを選択する
<!-- The **Console** has a **Target** drop-down menu just above the **Console** output pane. If the webpage you're viewing has an [iframe element]() in it, select the iframe from the **Target** menu to run **Console** commands solely in the scope of the iframe. If your webpage has no iframes, the only selection will be "_top." -->

**コンソール**には**コンソール**出力ペインの真上に**ターゲット**ドロップダウンメニューがあります。もし表示中のWebページに[iframe要素]()を含んでいるのであれば、**ターゲット**メニューからiframeを選択することで、**コンソール**コマンドをiframeのスコープで実行できます。Webページにiframeがない場合には"_top"のみを選択できます。

![Console System Messages](../media/Edge_Console_toggles.gif)

<!-- *In the image above, the Target iframe is selected, then the page reloads to output only Error messages, the file name is clicked to follow the error to the script file where it is located in the Debugger. Returning to the Console, the Error Code itself is clicked, opening the documentation page for that error code.* -->

*上の画像ではターゲットiframeを選択し、エラーメッセージを表示するためにページを再読み込みし、ファイル名をクリックすることでデバッガーでスクリプトファイルのエラーを追いかけます。コンソールに戻り、エラーコード自体をクリックすると、エラーコードに関するドキュメントページが開きます。*

<!-- ### Sending JavaScript into the Console -->
### JavaScriptをコンソールに送る
<!-- The console not only displays output from code, but provides an interface to execute code as well. Just enter any valid JavaScript at the bottom of the Console, in the command line pane. -->

コンソールはコードからの出力を表示するだけではなく、コードをいい感じに実行するためのインターフェースも提供しています。任意の正しいJavaScriptをコンソールの一番下のコマンドラインペインに入力するだけです。

![F12 Console Command Line](../media/Edge_Console_command.gif)

<!-- Generally, all script entered in the command line executes in the [global scope](https://msdn.microsoft.com/en-us/library/bzt2dkta.aspx) of the currently selected window. However, if your script is currently paused (for instance, because you set a breakpoint), script executes in the [local scope](https://msdn.microsoft.com/en-us/library/bzt2dkta.aspx) of the current function within the call stack. -->

普段はコマンドラインに入力されたすべてのスクリプトは現在選択中のウィンドウの[グローバルスコープ](https://msdn.microsoft.com/en-us/library/bzt2dkta.aspx)です。
しかし、もしスクリプトが中断中(例えばブレークポイントをセットしていた場合)であれば、スクリプトはコールスタックの中の現在の関数の[ローカルスコープ](https://msdn.microsoft.com/en-us/library/bzt2dkta.aspx)で実行されます。

![F12 Console Command Line local scope](../media/Edge_Console_local_scope.png)

<!-- If your webpage is built with a **[frameset](https://msdn.microsoft.com/en-us/library/ms535251.aspx)** or **[iframes](https://msdn.microsoft.com/en-us/library/ms535258.aspx)**, those frames load their own documents in their own windows. -->

もしWebページが**[frameset](https://msdn.microsoft.com/en-us/library/ms535251.aspx)**または**[iframes](https://msdn.microsoft.com/en-us/library/ms535258.aspx)**で作られているならば、それぞれのフレームは各ウィンドウごとに各ドキュメントをロードします。

<!-- To target the window of a frameset frame or an iframe, use the `cd()` command, with the frame/iframe's name or ID attribute as the argument. For example, you have a frame with the name microsoftFrame and you're loading the Microsoft homepage in it. -->

framesetのフレームまたはiframeのウィンドウをターゲットとするには、frame/iframeの名前またはID属性を引数にして`cd()`コマンドを呼び出します。例えば、microsoftFrameという名前のフレームがあり、Microsoftのホームを表示しているとします。

   **JavaScript**
   ```js
   cd(microsoftFrame);
   ```
   ```
   Current window: www.microsoft.com/en-us/default.aspx
   ```

<!-- **Important**  Note that there were no quotes around the name of the frame. Only pass the unquoted name or ID value as the parameter.
To return to the top level window, use `cd()` with no argument. -->

**重要** フレームの名前の前後にはクォートがないことに注意してください。クォートなしの名前またはID値のみをパラメータとして渡します。
トップレベルのウィンドウに戻るには、引数なしで`cd()`を呼び出します。

<!-- ### Selecting elements in the Console -->
### コンソールで要素を選択する
<!-- Console selectors provide simple shorthands for quickly selecting elements in your DOM structure. They are: -->

コンソールセレクターはDOM構造から要素を素早く選択するための単純な短縮記述を提供します。

<!--
   - **$()** is a shorthand for [**`document.querySelector()`**](https://msdn.microsoft.com/en-us/library/cc288169.aspx).
   - **$$()** is a shorthand for [**`document.querySelectorAll()`**](https://msdn.microsoft.com/en-us/library/cc304115.85.aspx).
   - **$_()** is a shorthand for the last selected element or object.
   - **$0, $1, $2, $3, $4** return the last items selected in the [**DOM Explorer tool**](../dom-explorer/).
-->
   - **$()** は [**`document.querySelector()`**](https://msdn.microsoft.com/en-us/library/cc288169.aspx) の短縮記述
   - **$$()** は [**`document.querySelectorAll()`**](https://msdn.microsoft.com/en-us/library/cc304115.85.aspx) の短縮記述
   - **$_()** は最後に選択した要素またはオブジェクトの短縮記述
   - **$0, $1, $2, $3, $4** は[**DOM Explorer ツール**](../dom-explorer/)で最後に選択したアイテム

<!-- **Important**  If code in a webpage assigns a function to **$** or **$$**, that function overrides the console selector functions while the console is interacting with that page or its frames. -->

**重要** もしWebページのコードが**$**または**$$**に関数を割り当てている場合、そのページまたはフレームのコンソールと対話している間はその関数がコンソールセレクターを上書きします。

<!-- ### The multiline command line -->
### 複数行コマンドライン

<!-- Sending in single line commands is useful, but some tasks require executing longer scripts. Click the double up-arrow symbol to expand the command line. In multiline mode, enter as many lines as you need, then click the green arrow symbol to execute it in the console. -->

一行コマンドを送るのは便利ですが、中には作業では長いスクリプトを実行する必要となることもあります。
その場合には二つの上矢印マークをクリックすればコマンドラインを広げることができます。複数行モードではたくさんの行を必要なだけ入力でき、緑色の矢印マークをクリックすればコンソールで実行されます。

![F12 Console Multiline Command Line](../media/f12blueconsolecommandmultiple.png)

## Related topics
[Using the Console API](./using-the-console-api/)

