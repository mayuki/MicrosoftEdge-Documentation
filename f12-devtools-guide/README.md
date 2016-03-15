<!-- # Meet the Microsoft Edge Developer Tools -->
# Microsoft Edge開発者ツールに触れる

<!-- Microsoft Edge introduces great new improvements to F12 developer tools, including some of the most requested features from [UserVoice](https://wpdev.uservoice.com/forums/257854-microsoft-edge-developer).  The new tools are built in TypeScript, and are always running, so no reloads are required. In addition, F12 developer tools documentation is now fully available on [GitHub](https://github.com/MicrosoftEdge/MicrosoftEdge-Documentation). From this point on, the docs will not only be influenced by your feedback, but you're invited to contribute and help shape our documentation. -->

Microsoft EdgeではF12開発者ツールに[UserVoice](https://wpdev.uservoice.com/forums/257854-microsoft-edge-developer)に寄せられた最もリクエストの多かった機能のいくつかを含む、素晴らしい新改良が導入されました。

![channel9](https://channel9.msdn.com/Blogs/One-Dev-Minute/Microsoft-Edge-F12-tools)

<!-- ## The F12 tools at work -->
## 作業でのF12ツール

<!-- There are seven distinct tools, each with their own tab in the F12 tools interface. Here you'll find an image of each tool and a quick summary of what it does, followed by lists of its main features and typical tasks. -->

F12ツールのインターフェースには独自のタブを持つ、それぞれ7つの異なった機能があります。ここではそれぞれのイメージとそれが何をするのかについての概要、続いて主な機能と典型的なタスクのリストを見ることができます。

<!-- ## The DOM Explorer tool (CTRL+1) -->
## DOM Explorerツール (CTRL+1)

<!-- [The DOM Explorer tool](./dom-explorer/) shows the structure of your webpage as it's being rendered in the browser and makes it possible to edit your HTML and styles in a live page. You can do this without having to edit and reload your sources, so you can quickly solve display issues or experiment with new ideas.
 -->

[DOM Explorerツール](./dom-explorer/)はブラウザでレンダリングされているWebページの構造を表示し、現在のページのHTMLとスタイルを編集可能にします。そのために編集と再読み込みが不要となるので、素早く表示上の問題を解決したり、新しいアイデアを試すことができます。

![Edge DOM Explorer](./media/Edge_DOMExplorer.png)

<!-- **Features** in the DOM Explorer tool include: -->

DOM Explorerツールに含まれている**特徴**:

<!-- 
 - IntelliSense autocompletion suggestions when editing HTML attributes and CSS properties.		+|IntelliSense autocompletion suggestions when editing HTML attributes and CSS properties.|
 - Drag DOM nodes to rearrange them.		+|Drag DOM nodes to rearrange them.|
 - Support for compiled CSS sourcemaps		+|Support for compiled CSS sourcemaps|
 -->

- HTMLの属性とCSSのプロパティを編集時にIntelliSenseよる自動補完候補
- DOMノードをドラッグして並び替え
- コンパイルされたCSSのソースマップサポート

<!-- **Development and debugging tasks it makes easier:** -->

**開発とデバッグタスクをもっと簡単に:**

<!-- 		
  - Determining why an element is not displaying at the right place or right size.
 - Figuring out which CSS styles and media queries are being applied to an element.
 - Testing a series of different colors for an element to see which looks best.
 -->

- なぜ要素が正しい場所または正しいサイズで表示されていないのかを突き止める
- 要素に適用されているCSSのスタイルとメディアクエリーを把握する
- どれが最もよく見えるのか把握するために、要素に対する一連の様々な色のテストをする

<!-- [Learn more about the DOM Explorer tool.](./dom-explorer/) -->

[DOM Explorerツールについてもっと詳しく](./dom-explorer/)

<!-- ## The Console tool (CTRL+2) -->
## コンソールツール (CTRL+2)

![Edge Console Tool](./media/Edge_Console.png)

<!-- The [Console tool](./console/) provides a way to interact with your running code: -->

[コンソールツール](./console/)は実行中のコードと対話する手段を提供します:

<!-- 
  - change variable values or inject code into a live site with the Console's command line.
  - use the [Console Debugging API](./console/using-the-console-api/) to send out debug information.
  - see browser error messages and status codes.
 -->

  - 変数の値を変更する、あるいはコンソールのコマンドラインから現在のサイトにコードを差し込む
  - [コンソールデバッグAPI](./console/using-the-console-api/)を使うことでデバッグ情報を出力する
  - ブラウザーのエラーメッセージとステータスコードを見る

<!-- **Features** in the [Console tool](./console/) include: -->

[コンソールツール](./console/)が含む**特徴**:

<!-- 
  - Open the Console at the bottom of any other tool with the Console button or CTRL + `.
  - [Console Debugging API](./console/using-the-console-api/) methods for timing, counting, grouping, and more.
  - IntelliSense autocompletion suggestions on the command line speed up input, reduce typos, and help you discover aspects of JavaScript APIs.
 -->
  - コンソールボタンまたはCTRL + `で他のツールの下にコンソールを開く
  - タイミング、カウンター、グルーピング、その他のための[コンソールデバッグAPI](./console/using-the-console-api/)メソッド
  - コマンドラインでのIntelliSenseによる自動補完候補で、入力をスピードアップし、打ち間違いを減らし、JavaScript APIを探る手助け

<!-- **Development and debugging tasks it makes easier:** -->

**開発とデバッグタスクをもっと簡単に:**

<!-- 
  - targeting specific iFrames.
  - timing code execution down to the statement with new timing methods.
  - changing the value of a variable in running code without reloading.
 -->
  - 特定のiframeをターゲットにする
  - 新しいタイミングメソッドで文までのコードの実行の時間計測する
  - コード実行中に再読み込みなしで変数の値を変更をする

<!-- [Learn more about the Console tool.](./console/) -->

[コンソールツールについてもっと詳しく](./console/)

<!-- ## The Debugger tool (CTRL+3) -->
## デバッガーツール (CTRL+3)
![Edge Debugger Tool](./media/Edge_Debugger.png)

<!-- You use the [Debugger tool](./debugger/) to examine what your code is doing, when it's doing it, and how it's doing it. Pause code in mid-execution, step through it line-by-line, and watch the state of variables and objects at each step. -->

コードが何をして、どういうときに動き、どう動いているのかを調査するのに[デバッガーツール](./debugger/)を使うことができます。実行中にコードの一時停止をして、一行ごとにステップ実行し、ステップごとに変数とオブジェクトの状態を監視できます。

<!-- **Features** in the [Debugger tool](./debugger/) include: -->

[デバッガーツール](./debugger/)が含む**特徴**:

<!-- 
  - No-refresh debugging. Set your breakpoints and go without reloading and losing state.
  - Tabbed document interface for easier management of multiple scripts.
  - Breakpoints on standard code, XHR responses, and events.
 -->

  - リフレッシュのないデバッグ。ブレークポイントを設定し、再読み込みなしで実行し状態を失いません
  - 複数のスクリプトを簡単に管理するためのタブドキュメントインターフェース
  - 標準的なコード、XHRレスポンス、イベントに対するブレークポイント

<!-- **Development and debugging tasks it makes easier:** -->

**開発とデバッグタスクをもっと簡単に:**

<!-- 
  - Seeing what led to a function call using the Call stack.
  - Making compressed or minified code more readable using source maps.
  - Monitoring web worker creation and execution.
  - 
[Learn more about the Debugger tool.](./debugger/)
 -->

  - コールスタックを使って、関数の呼び出しの流れを見る
  - ソースマップで圧縮またはminfyされたコードをもっと読みやすくする
  - Web Workerの生成と実行をモニタリングする

[デバッガーツールについてもっと詳しく](./debugger/) 

## The Network tool (CTRL+4)
![Edge Network Tool](./media/Edge_Network_details.png)

The [Network tool](./network/) gives you the fine details of any network requests involved in the loading and operation of your webpages.

**Development and debugging tasks it makes easier:**
  - Viewing the amount of bandwidth your page consumes across resources.
  - Debugging AJAX requests by viewing request and response headers and bodies.
  - Identifying network requests that slow the loading of your webpages.

[Learn more about the Network tool.](./network/)

## The Performance Tool (CTRL+5)
![Edge Performance Tool](./media/Edge_Performance.png)

The [Performance tool](./performance/) helps you dig into what is happening when your page slows down. Using it to profile specific points of slowness shows the operations that are causing them. In Microsoft Edge, the Performance tool combines the previous **UI Responsiveness** and **Profiler** tools to create an end-to-end view of your scripting and painting performance.

Some interesting features are:

  - Identifying the different sources of CPU activity causing UI slowness.
  - Insight into your webpage's frame rate and how much repaints and reflows cost.
  - Setting labels on the timeline to isolate user scenarios.

**Development and debugging tasks it makes easier:**

  - Testing code optimizations.
  - Speeding up your webpages.

[Learn more about the Performance tool.](./performance/) 

## The Memory tool (CTRL+6)
![Edge Memory Tool](./media/Edge_Memory.png)

When a webpage starts out fast and slows down after you use it for a while, the culprit is usually a memory leak. The [Memory tool](./memory/) tracks the memory use of your webpage, helping you identify where memory use is growing, why it's growing, and how to fix it.

Some interesting features are:

  - A timeline to see progressive changes in memory use.
  - Snapshots to examine the details of memory use at specific points.
  - Snapshot comparisons to identify specific points of growth.

**Development and debugging tasks it makes easier:**

  - Identifying detached DOM nodes.
  - Identifying points of memory growth.
  - Measuring the memory use of objects.

[Learn more about the Memory tool.](./memory/)

## The Emulation tool (CTRL+7)
![Edge Emulation Tool](./media/Edge_Emulation.png)

The [Emulation](./emulation/) helps you test how your webpages run on different screen sizes and hardware features, and how they respond to different user agent strings.

Some interesting features are:

  - You can emulate different screen sizes and resolutions.
  - GPS simulation.

**Development and debugging tasks it makes easier:**

  - Testing responsive designs on multiple screen types.
  - Testing location-aware features for a mobile site.

[Learn more about the Emulation tool.](./emulation/)
