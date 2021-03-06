# パフォーマンス

**Performance**ツールを使うことでWebページのフレームレートのタイムライン、JavaScriptのコールスタックを含む実行時間をプロファイルできます。CPU使用率とJavaScriptのプロファイリングの様々なレポートはUIパフォーマンスの問題を解析するのを手助けとなります。

## 速度の問題

アニメーションがガクガクしたり、ユーザーインターフェース要素の反応が遅かったりといったことで、UIがスムーズでもなく反応もよくないといった場合にユーザーの体験は損なわれてしまいます。新しい**Performance**プロファイラはページがスローダウンしている裏側で何が起きているのかを確認する手助けをします。この情報はスピードを改善するための手がかりとなります。

![Edge F12 Tools Performance](../media/Edge_Performance.png)

### プロファイルセッションを記録する

**Performance**を最初に読み込んだ時、**start profiling to begin a performance session**という案内がメインペインに見つかります。この案内のリンクまたはツールの上部にある矢印アイコンをクリックすることでプロファイリングがスタートします。

プロファイリング中には遅さをキャプチャーして解析するための最小限の操作をしてください。余計な操作をするとページから余計なデータが生まれ、結果がぐちゃぐちゃになってしまいます。

もしレポート中で正確なページのロード時間を知りたい場合は、[**Network tool**](../network/)を開いて**clear browser cache**オプションをプロファイリングの前に実行してください。

**Performance**ツールは[**DOMContentLoaded**](https://msdn.microsoft.com/library/hh869434.aspx)のような**アプリ ライフサイクル イベント**を自動的にマークします。コードからは[`performance.mark()`](https://msdn.microsoft.com/library/jj585593.aspx)メソッドを使うことでカスタムの**ユーザー マーク**をセットできます。

プロファイルしたい挙動をキャプチャーできたら、**stop profiling to generate a report**またはツールの上部の四角アイコンをクリックしてください。

もしかしたら情報を今すぐ解析する時間がなかったり、以前のプロファイルセッションの結果を見直したりするかもしれません。インポート(フォルダーアイコンまたはCTRL + O)とエクスポート(ディスクアイコンまたはCTRL + S)の機能でブラウザーとF12開発者ツールをずっと開きっぱなしにしておかなくても後日調査できます。

## パフォーマンスセッションレポート

### ルーラー

![Edge F12 Tools Ruler](../media/F12BlueResponsivenessRuler.png)

ルーラーには**アプリ ライフサイクル イベント**と**ユーザー マーク**はもちろんセッションの実行時間が表示されます。イベントとマークにカーソルを合わせることでラベルとセッション中の位置を表示します。

ユーザー マークには`performance.mark()`メソッドの引数の文字列をラベルとして付けることができます。

**ユーザー マーク**は[`performance.measure()`](https://msdn.microsoft.com/library/jj585594.aspx) APIでもっと便利になります。**ユーザー マーク**をセットしたのち、2つのマークの間で発生したイベントをグループ化するために**user measure**をセットできます。例えば、もし"Begin Rotation"と"End Rotation"という二つの**ユーザー マーク**がある場合、次のコードでそれらを"box cycler"というラベルでグループ化できます。

```javascript
performance.measure("box cycler","Begin Rotation","End Rotation");
```

![Edge F12 Tools Performance Measure](../media/Edge_Performance_measure.png)

### タイムライン

![Edge F12 Tools Performance Measure](../media/gdr_f12_ResponsivenessTimeline.png)

**タイムライン*は二つの尺度を表示します:


  - **CPU 使用率** は利用率と色でカテゴリを分類された発生したアクティビティの種類を表示します。分類されたカテゴリについての詳しい情報は[イベント カテゴリー](#イベント-カテゴリー)を参照してください
  - **ビジュアル スループット**は表示の一秒当たりのフレーム数(fps)の大よその値を表示します。フレームレートの落ち込みはどこでスローダウンが発生したかを示し、フレームレートがゼロであればフレームがドロップされていることを意味します

**タイムライン**上のエリアをクリックして水平方向にまたぐようにドラッグするとハイライトできます。この**タイムライン 詳細**フィルターでハイライトされたエリアの詳細だけを表示できます。さらに詳細を見るにはズームしてください。**Performance**ツールの上部のズームコントロールの右にはハイライトを削除する**Clear selection**アイコンがあります。

### The timeline details

![Edge F12 Tools Performance Timeline Details](../media/gdr_f12_ResponsivenessTimelineDetails.png)

The **Timeline details** look deeper into the recorded events, breaking down the categories into their component events. This info provides details about the DOM elements they impact or the code they cause to run.

In the previous image, The `DOMContentLoaded` event has a very short *exclusive duration* time, which is the time it took for the event itself to fire. The longer *inclusive duration* includes not only the event, but several processes launched as a result of the event.

The **event type filter** offers filters for **background activity**, **network traffic**, **UI activity** and **user measures**. When one of those options is selected, that kind of event is filtered out of the **Timeline details**. For example, while a page is loading, the details can be overwhelmed by **HTTP request** events. Click the **event type filter** and uncheck **network traffic** to make them disappear from view. 

In the image below, at the bottom of the dialog, a time filter is shown as set to filter out all events taking less than 1 millisecond, and a text box at the top is set to filter by text in the event's name.

![Edge F12 Tools Performance Timeline Filter](../media/Edge_Performance_filters.png)

To the left of the updated filters button is the **Group top level events by frames** button, or **frame grouping**. This creates a set of pseudo-events based on the measured frame rate and groups events under them. When you're trying to determine why you're dropping frames in an animation, this helps break units of work by frame and identify where frames are taking longer to execute than others.

![Edge F12 Tools Performance Timeline Grouping](../media/Edge_Performance_grouping.png)

For a quick overview of events that contributed to the inclusive duration, the event details pane shows a circular chart using the same color coding as the timeline. Because the colors represent categories of events, the chart might contain multiple segments in the same color. Placing your mouse over a segment shows a tooltip with its event label.

### Filtering to an event

Right-click events to see a context menu with three options:

  - **Filter to event** sets the zoom level to the event's inclusive time, so just the event and any events that happened at the same time are displayed.

  - **Clear selection** zooms out again.

  - **View Source** is only enabled for **Scripting** events. It switches to the [**Debugger**](../debugger/), opens the file containing the code that generated the event, and moves the cursor to the point in the code where the event was generated.

### The details of the details

Each element in the **Timeline details** shows different info, depending on its type.

![Edge F12 Tools Performance Timer Details](../media/F12BlueResponsivenessTimerDetails.png)

This timer was invoked by a [`setTimeout()`](https://msdn.microsoft.com/library/ms536753.aspx) which called the **autoNextSlide** function in **script.jsx**. When you click the file name, it opens in the [**Debugger tool**](../debugger/) and navigates to the function for inspection.

The circular chart at the bottom shows that while **Scripting** made up a large part of the event's time, **Styling** took up a fair portion. Expanding the timer's event in the **Timeline details** shows more about the different **Styling** operations that contributed to the time it required.

When you select a portion of the timeline, that selection's summary information is presented in the event details pane like a timeline event until you select an event from the **Timeline details**.

![Edge F12 Tools Performance Selection Summary](../media/Edge_Performance_selectionSummary.png)

## Event categories and definitions
The Responsiveness tool uses 7 main event categories on the timeline. These break down into a selection of events in **Timeline details**.

  - **Loading** contains events related to bootstrapping and loading a webpage's resources. This is recorded for the primary window and any frames within it. The events gathered within **Loading** are:
    - **CSS parsing**: New CSS content was found and needs to be analyzed. The details include the URL of the content or inline in parentheses after the event if the CSS is hardcoded into the webpage.
    - **HTML parsing**: New HTML content was found that needs to be divided into nodes and added to the DOM.
    - **HTTP request:** Makes an HTTP request to a server and receives the response. More than one response can appear at the same time and not consume significant resources. However, rendering might be delayed by waiting for a large or slow HTTP request to complete. The URL of the request and the response code are the type of details shown here.
    - **Speculative downloading**: The webpage's HTML content is searched for required resources so HTTP requests can be scheduled as quickly as possible.

  - **Scripting** contains events related to processing and executing JavaScript. These events are gathered within **Scripting**:
    - **Animation frame callback**: A new frame was being prepared and a registered callback was triggered so that it could contribute any visual changes. Details include the location of the callback within the webpage or external scripts.
    - **DOM event**: A [**DOM event**](https://msdn.microsoft.com/library/hh771866.aspx) was fired. Event listeners attached to it are shown as children of the event.
    - **Script evaluation**: Processing content within `<script>` elements. Details include the URL of the script or **inline** if it's part of the webpage.
    - **Timer**: An [interval](https://msdn.microsoft.com/library/ms536749.aspx) or [timeout](https://msdn.microsoft.com/library/ms536753.aspx) completed and triggered execution of its callback. The details include the location of the timer within the webpage or external scripts, the time it took, and the name of its callback function (if any). Actions triggered by the callback are shown as children of the event.
    - [**Media query listener**](https://msdn.microsoft.com/library/hh772369.aspx): When script that responds to a media query event runs, this is broken out as its own category.
    - [**Mutation observer**](https://msdn.microsoft.com/library/dn265034.aspx): Script responding to events fired by mutation observers is broken out as a category.

When a change is explicitly made to a style object via JavaScript (i.e. `element.style.height="20px"`), requiring the DOM to be updated, the individual changes and their exclusive times are shown as descendants of the Scripting event that caused them.

  - **GC**, garbage collection, is the identification and removal of items from memory when they are no longer needed. It's referred to by its full name in **Timeline details**.

  - **Styling** contains events related to CSS styles and element positioning. The events gathered within **Styling** are:

    - **Layout**: Changes were made to the DOM that required the size and/or position of all affected elements to be computed.
    - **Style calculation**: Changes were made to the DOM or new CSS content was added, requiring the style properties of all affected elements to be recalculated.

  - **Rendering** contains events related to putting elements on the screen. The events gathered within **Rendering** are:
    - **Paint**: Visual changes were made to the DOM that required all affected portions of the page to be redrawn. **Render layer** events may appear as child events and indicate a specific fragment of the DOM was redrawn. The coordinates (x,y) and dimensions of the layer impacted by a **Render layer** event are included in the details.

  - **Image Decoding** is the activity of turning compressed image file formats into the sequences of colored pixels that are painted to the screen. It's referred to by its name in **Timeline details**.

  - **Other**: Miscellaneous browser-related computing. Computing categorized as **Other** doesn't get displayed in **Timeline details**. In Windows 8.1 Update, **Other** is removed from the categories.

For a more specific demonstration of using the Performance tool, check out our demo and code sample: [Improving animation performance with the Performance tool](http://samples.msdn.microsoft.com/workshop/samples/UIPerformance/default.html).

## JavaScript Call Stacks
If you remember the F12 tools in Internet Explorer 11, you'll remember the **JavaScript profiler** tool. In Microsoft Edge, it's combined with the prior **UI responsiveness** tool to make the **Performance** tool. We found that the information for both tools was often needed together, so now whenever a **Performance** report is generated, the JavaScript call stack is timed and that profiling information is presented in the **JavaScript call stacks** tab.

![Edge F12 Tools Performance Timeline Grouping](../media/Edge_Performance_callstacks.png)

The image above shows the initial load of the Microsoft homepage, a little navigation around it, and the JavaScript functions that were invoked. 

  - The **Inclusive CPU** (both % and ms) represent the amount of CPU resources and time to execute required both by that function and the other functions called as a result of running it.

  - The **Exclusive CPU** (both % and ms) represent the amount of CPU resources and time to execute required speficically by that function alone.

  - The **URL** provides the URL of the script where that function exists. Because of functions in your code calling libraries that reside in different files, you may see multiple URLs owning the child functions in a call stack.


## Performance profiling tips
**Test more than once**: The results you'll see in a profiling report are not just based on your code. They're influenced by other processes on your system competing for your processor and memory. A moment of slowness or a bad overall test might be due to a virus scan running in the background or too many tabs being open on your browser. Alternatively, if you test on a new machine under laboratory conditions, it might be so fast, your code just runs great. It's important to make sure you can reproduce slowness reliably, just like reproducing a bug. Then you can diagnose the cause.

**Consistency feels faster**: The **Performance** profiler's visual map of your frame rate over time can be very useful. Uneven frame rates or skipped frames can make your site feel slow. If it reduces skips and helps keep the frame rate consistent, slowing down your animation could make it feel faster. ["The secret to silky smooth JavaScript animations"](http://creativejs.com/resources/requestanimationframe/) provides a couple of suggestions for reducing frame rate while getting the power-saving and anti-skipping benefits of using [`window.requestAnimationFrame()`](https://msdn.microsoft.com/library/hh773174.aspx).

**How much of this CSS is necessary?** Many sites use a site-wide style sheet to make pages load faster. It can reduce the number of network requests and take advantage of caching on subsequent loads. However, every style in a style sheet must be parsed and adds to the complexity of **Styling** calculations whether the style is used in the page or not.

For most sites, this never becomes a problem. In very large sites with complex styling, lots of pages, lots of UI animations, and gigantic site-wide style sheets, you'll often see **Styling** operations become a primary cause of performance lags because of the overhead created by unused styles.

At this point, the question to ask is: is the cost of the unused styles bigger than the benefit of the single style sheet? Try a few different solutions and profile them. You'll have your answer soon enough.

## Related topics

[Improving animation performance with the Performance tool](http://samples.msdn.microsoft.com/workshop/samples/UIPerformance/default.html)

[The Performance tool in Visual Studio](https://msdn.microsoft.com/library/dn194502.aspx)

[Microsoft Edge Developer Tools on Twitter: Find helpful F12 hints and news updates](https://twitter.com/EdgeDevTools)
