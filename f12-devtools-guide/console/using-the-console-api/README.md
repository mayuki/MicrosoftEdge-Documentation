<!-- # Using the Console API -->
# コンソールAPIを使う

<!-- The Console API provides methods for developers to send meaningful information to the Console from within their applications and to obtain diagnostic information from within the Console tool. -->

コンソールAPIは意味ある情報をアプリケーションからコンソールに送ったり、コンソールツールの中から診断情報を得るために開発者のためのメソッドを提供します。

<!-- ## Reporting out from your code -->
## コードからレポートする
<!-- The [Console Debugging API](https://msdn.microsoft.com/en-us/library/hh772173.aspx) gives you methods for sending info out from your code to the console. The info breaks down into these types: -->

[コンソールデバッグAPI](https://msdn.microsoft.com/en-us/library/hh772173.aspx)はコードからコンソールへ情報を送信する方法を提供します。情報は次の種類に分類されます:

<!-- 
  - [Custom messages](#custom-messages)
  - [Inspectable objects and nodes](#inspectable-objects-and-nodes)
  - [Counters](#counters)
  - [Timers](#timers)
  - [Assertions](#assertions)
  - [Traces](#traces-and-profiles)
-->
  - [カスタムメッセージ](#カスタムメッセージ)
  - [調査可能なオブジェクトとノード](#調査可能なオブジェクトとノード)
  - [カウンター](#カウンター)
  - [タイマー](#タイマー)
  - [アサーション](#アサーション)
  - [トレース](#トレースとプロファイル)

<!-- ### Custom messages -->
### カスタムメッセージ
<!-- You have four options for custom messages. Three use the format of system messages: [`console.info()`](https://msdn.microsoft.com/en-us/library/hh772178.aspx) for information messages, [`console.warn()`](https://msdn.microsoft.com/en-us/library/hh772181.aspx) for warnings, and [`console.error()`](https://msdn.microsoft.com/en-us/library/hh772176.aspx) for errors. The fourth, [`console.log()`](https://msdn.microsoft.com/en-us/library/hh772179.aspx) presents plain text with no alert icon. All four take the same forms of argument for the message. -->

カスタムメッセージには4つの選択肢があります。3つはシステムメッセージの書式に使います: [`console.info()`](https://msdn.microsoft.com/en-us/library/hh772178.aspx)は情報メッセージ、[`console.warn()`](https://msdn.microsoft.com/en-us/library/hh772181.aspx)は警告メッセージ、 [`console.error()`](https://msdn.microsoft.com/en-us/library/hh772176.aspx)はエラーです。4つ目、[`console.log()`](https://msdn.microsoft.com/en-us/library/hh772179.aspx)はアラートアイコンを表示しないプレーンなテキストです。4つともすべてメッセージには同様の引数をとります。

<!-- **Just text:** -->

**テキストだけの場合:**

###### *JavaScript*

`console.log('This is some text');`
>
`This is some text`



<!-- **Just a variable:** -->

**変数だけの場合:**

###### *JavaScript*
```javascript
var mytext = 'This is some text';
console.log(mytext);
```
>
`This is some text`

<!-- **Mixed text and variables:** -->

**テキストと変数の混在:**
###### *JavaScript*
```javascript
var mytext = 'pieces';
var myval = 0;
console.log("The number of " + mytext + "is " + myval);
```
>
`The number of pieces is 0`

<!-- **Variable Substitution:** -->

**変数置換:**

###### *JavaScript*
```javascript
var mytext = 'pieces';
var myval = 5;
console.log("The number of %s is %d", mytext, myval);
```
>
`The number of pieces is 5`

<!-- Variable substitution has five variable types: -->

変数置換は5つの変数型を持ちます:

<!-- 
  - %**s** - string
  - %**d** - integer
  - %**i** - integer
  - %**f** - float
  - %**o** - object
  - %**b** - binary
  - %**x** - hexadecimal
  - %**e** - exponent
 -->
  - %**s** - 文字列
  - %**d** - 整数
  - %**i** - 整数
  - %**f** - 浮動小数
  - %**o** - オブジェクト
  - %**b** - バイナリ
  - %**x** - 16進数
  - %**e** - 指数

<!-- The variable types control how the variable is presented. For example, a float value represented by an integer variable type is displayed as an integer. -->

変数型は変数をどう表現したらよいのかをコントロールします。例えば、float値を整数変数型で表現すると整数として表示されます。

<!-- ### Inspectable objects and nodes -->
### 調査可能なオブジェクトとノード
<!-- Inspectable objects appear in the console in a collapsed tree format with expandable nodes. The console detects whether you are sending a DOM node like a div or a JavaScript object like an event and displays them as the detected type automatically. You can, however, force the mode using specific methods. -->

調査可能なオブジェクトは広げることのできるノードとして折りたたまれたツリー形式でコンソールに表示されます。コンソールは送られてきたものがdivのようなDOMノードであるのか、イベントのようなJavaScriptのオブジェクトであるのかといった種類を自動的に判別します。

<!-- To display an inspectable JavaScript object, send it to the console using [`console.dir()`](https://msdn.microsoft.com/en-us/library/jj152132.aspx) -->

調査可能なJavaScriptオブジェクトを表示するには、[`console.dir()`](https://msdn.microsoft.com/en-us/library/jj152132.aspx)を利用してコンソールに送ります。

<!-- To display an inspectable DOM node, send it to the console using [`console.dirxml()`](https://msdn.microsoft.com/en-us/library/dn265067.aspx) -->

調査可能なDOMノードを表示するには、[`console.dirxml()`](https://msdn.microsoft.com/en-us/library/dn265067.aspx)を利用してコンソールに送ります。

###### *HTML*
```html
<div id="thediv">
   <p>Click the button to show this div as a JavaScript object and a
   <em>DOM</em> node.</p>
   <button id="thebutton">show it</button>
</div>
<script>
  document.getElementById('thebutton').addEventListener('click', function(e){
    var divid = document.getElementById('thediv');
    console.log('Showing the div element as a DOM node.');
    console.dirxml(divid);
    console.log('Showing the div element as a JavaScript object.');
    console.dir(divid);
    console.log('Showing the div element via a plain console.log.');
    console.log(divid);
    console.log('Showing the click event via a plain console.log.');
    console.log(e);
    console.log('Argument logging for %s', thediv.id, thediv)
  });
</script>
```
![Edge Console Inspectable objects and nodes](../../media/Edge_Console2.png)

<!-- Use the arrows to the left to expand objects and nodes. -->

左の矢印を使ってオブジェクトとノードを開くことができます。

<!-- Right-clicking DOM nodes provide an **Evaluate as Object** option in the context menu. If you select that option, you send the node to the console as an object. Similarly, JavaScript objects that represent DOM nodes offer an **Evaluate as HTML** option in their context menus. -->

DOMノードを右クリックすると表示されるコンテキストメニューに**Evaluate as Object**という選択肢があります。この選択肢を選ぶと、ノードをコンソールにオブジェクトして送ることができます。同様に、DOMノードのJavaScriptのオブジェクト表現のコンテキストメニューには**Evaluate as HTML**が用意されています。

<!-- ### Counters -->
### カウンター
<!-- While setting up a counter in code is relatively easy, it's also a repetitive task. To speed up developer workflow, the Console Debugging API provides a simple shorthand. -->

コードでカウンターをセットするのは比較的簡単な半面、何度も繰り返されるタスクでもあります。開発者のワークフローをスピードアップするため、コンソールデバッグAPIは単純な短縮記述を提供します。

<!-- Use [`console.count()`](https://msdn.microsoft.com/en-us/library/dn265064.aspx) with a string containing a counter label as its argument. The first use with a specific label establishes a counter in the Console output. Subsequent uses of `console.count()` with the same label increment the counter. To reset the counter to zero, use `console.countReset()` with the label. -->

[`console.count()`](https://msdn.microsoft.com/en-us/library/dn265064.aspx)をカウンターのラベルを持つ文字列を引数として呼び出します。初回の呼び出しで指定したラベルでカウンターがコンソールに出力されます。続いて`console.count()`を同じラベルで呼び出すとカウンターが加算されます。カウンターをリセットして0にするにはラベルを指定して`console.countReset()`を呼び出します。

###### *JavaScript*
```javascript
console.count('mylabel');
for(var i = 0; i < 10; i++){
  console.count('mylabel');
}
```
>
`mylabel:         11`

<!-- ### Timers
### タイマー
<!-- Like creating counters, creating a timer within code is relatively easy, but the [Console Debugging API](https://msdn.microsoft.com/en-us/library/hh772173.aspx) provides a simple shorthand that makes it even easier. -->

カウンターを作るのと同じように、コード中にタイマーを作るのも比較的簡単です。しかし[コンソールデバッグAPI](https://msdn.microsoft.com/en-us/library/hh772173.aspx)はそれをさらに簡単するべく単純で短縮記述法を提供しています。

<!-- Use [`console.time()`](https://msdn.microsoft.com/en-us/library/dn265071.aspx) anywhere in your code to begin a timer and [`console.timeEnd()`](https://msdn.microsoft.com/en-us/library/dn265072.aspx) to end the timer and send the result to the console. If you want to label your timer or need more than one timer, pass a string with a unique label as the argument for both the `console.time()` and `console.timeEnd()` methods. If you don't pass an argument, the methods use "default" as the label. -->

[`console.time()`](https://msdn.microsoft.com/en-us/library/dn265071.aspx)をコードのどこかで呼び出すことでタイマーを開始し、[`console.timeEnd()`](https://msdn.microsoft.com/en-us/library/dn265072.aspx)でタイマーを止めて結果をコンソールに送ります。もしタイマーにラベルを付けたい、または2つ以上のタイマーを使いたいのであれば、`console.time()`と`console.timeEnd()`メソッドの両方の引数にユニークなラベルとなる文字列を渡してください。引数を渡していない場合にはメソッドは"default"をラベルとして使います。

<!-- The `console.timeStamp()` shows you the age of a page, so to speak. It will output a timestamp to the console, showing the number of milliseconds since the current webpage loaded. If you put a number or string as the method's parameter, it will be used as a label, overriding the default label of "timestamp." When you use it during a **UI Responsiveness** profiling session, in addition to its console output, it will add a user mark to the session timeline with the time since the session was initiated. -->

`console.timeStamp()`は言わばページの年齢です。メソッドはタイムスタンプをコンソールに出力し、現在のWebページが読み込まれてからのミリ秒を表示します。もしメソッドの引数に数値または文字列を渡した場合、それはラベルとして扱われ、デフォルトのラベルである"timestamp"を上書きします。**UI Responsiveness**プロファイルセッション中に呼び出した場合、コンソール出力に加えて、セッションタイムラインにユーザーマークがセッションが開始された時からの時間と共に追加されます。

<!-- ### Assertions -->
### アサーション

<!-- Assertions are another shorthand for speeding up developer workflow. If the first argument used with [`console.assert()`](https://msdn.microsoft.com/en-us/library/hh772171.aspx) evaluates to false, it runs [`console.error()`](https://msdn.microsoft.com/en-us/library/hh772176.aspx), using the assertion's additional arguments for the error message. -->

アサーションは開発者のワークフローをスピードアップするための異なる短縮記法です。[`console.assert()`](https://msdn.microsoft.com/en-us/library/hh772171.aspx)を呼び出す際に第一引数の評価結果がfalseとなる場合、[`console.error()`](https://msdn.microsoft.com/en-us/library/hh772176.aspx)を実行し、アサーションの追加の引数をエラーメッセージとして使います。

<!-- Use this one line of code: -->

コードの使用している行:

###### *JavaScript*
`console.assert(f < 25, 'f is not less than %d, but is instead %o', 25, f);`

<!-- And it's equivalent to writing: -->

これは下記のように書くのと同様:

###### *JavaScript*
```javascript
if(!(f < 25)){
  console.error('f is not less than %d, but is instead %o', 25, f)
}
```

<!-- In the example code, we used `%o` to output the variable. Because the evaluation above will fail if the variable's value isn't a number, using `%o` makes it possible to see the variable as it is instead of cast into a specific type. -->

サンプルコード中で、変数を出力するために`%o`を利用しています。これは変数の値が数値ではない場合に上の評価は失敗するため、`%o`を使うことで特定の型にキャストする代わりに変数の値を見れる形にします。

<!-- ### Traces and profiles -->
### トレースとプロファイル
<!-- Understanding where your code is being called from, what code is running, and how long that execution takes can be useful in analyzing slowness or unexpected behavior. -->

コードがどこから呼ばれているのか、どのコードが実行されているのか、実行するのにどのぐらいの時間がかかっているのかを知るということは、遅さあるいは予期していない挙動の解析に役立ちます。

<!-- A stack trace shows you the execution path your code took to reach it, from the trace request upward through the path. Use [`console.trace()`](https://msdn.microsoft.com/en-us/library/hh772176.aspx) in your code to show a stack trace. -->

スタックトレースはコードがトレース要求にたどり着くまでの上方の実行パスを表示します。
[`console.trace()`](https://msdn.microsoft.com/en-us/library/hh772176.aspx)をコードから呼び出すことでスタックトレースを表示できます。

<!-- This code... -->

このコードが...

###### *JavaScript*
```javascript
function a(){
  c();
}
function b(){
  c();
}
function c(){
  console.trace()
}
function d(){
  b();
}

a();
d();
```

<!-- ...displays this output in the console. -->

...コンソールにこの出力を表示します。

```javascript
console.trace()
at c (http://www.contoso.com/trace.html:24:3)
at a (http://www.contoso.com/trace.html:18:3)
at Global code (http://www.contoso.com/trace.html:30:1)
console.trace()
at c (http://www.contoso.com/trace.html:24:3)
at b (http://www.contoso.com/trace.html:21:3)
at d (http://www.contoso.com/trace.html:27:3)
at Global code (http://www.contoso.com/trace.html:31:1)
```

<!-- ### Managing messages for readability -->
### メッセージの読みやすさを管理する
<!-- **Organizing messages into groups.** -->

**メッセージをグループに分ける**

<!-- With all the types of messages and content that get sent to the console, keeping track of them can be difficult. Use the following commands to keep things more orderly: -->

メッセージの種類と内容がコンソールに送られてはいるものの、それらを追い続けることは難しいかもしれません。

<!-- 
  - [`console.group()`](https://msdn.microsoft.com/en-us/library/dn265068.aspx) begins a collapsible group in an expanded state. Every message sent to the console after this command is placed in the group until the `console.groupEnd()` method is used. If a string is provided as the first argument for the method, the string is used as a label for the group.
  - [`console.groupCollapsed()`](https://msdn.microsoft.com/en-us/library/dn265069.aspx) begins a collapsible group in a collapsed state. In all other respects, it behaves like `console.group()`.
  - [`console.groupEnd()`](https://msdn.microsoft.com/en-us/library/dn265068.aspx) closes the most recently opened group.
  - [`console.clear()`](https://msdn.microsoft.com/en-us/library/jj152131.aspx) deletes all messages currently displayed in the console.
 -->
  - [`console.group()`](https://msdn.microsoft.com/en-us/library/dn265068.aspx) は展開状態で折りたたみ可能なグループを開始します。このコマンド以降に送信されたメッセージはグループに入り、`console.groupEnd()`メソッドが呼び出されるまで続きます。メソッドの第一引数に文字列を渡した場合、文字列はグループのラベルとして使用されます
  - [`console.groupCollapsed()`](https://msdn.microsoft.com/en-us/library/dn265069.aspx)は折りたたまれた状態で折りたたみ可能なグループを開始します。ほかの点は`console.group()`と同様に振る舞います
  - [`console.groupEnd()`](https://msdn.microsoft.com/en-us/library/dn265068.aspx)は一番最近開かれたグループを閉じます
  - [`console.clear()`](https://msdn.microsoft.com/en-us/library/jj152131.aspx)は現在コンソールに表示されているすべてのメッセージを削除します

<!-- Groups can be nested within one another for more detailed levels of grouping. -->

グループはグルーピングをさらに詳細なものにするため他のグループをネストできます。

<!-- To turn different types of messages on and off, use filtering. -->

異なるメッセージの種類をオン/オフするにはフィルタリングを使用します。

<!-- At the top of the **Console tool** are icons for error, warning, and informational messages with a count of each type next to them. Click an icon to toggle the display of that message type on or off. When toggled off, that type of message is hidden, but not deleted, and can be restored by toggling that message type on again. -->

**コンソール**の上部にはエラー、警告、情報のメッセージのアイコンが件数と共に並んでいます。アイコンをクリックすることでその種類のメッセージの表示をオン、オフが切り替わります。オフに切り替わったときはその種類のメッセージは非表示となりますが、削除はされていないため、もう一度メッセージの種類を切り替えることで元に戻せます。

<!-- Right-clicking within the console output displays a context menu with check box toggles for the three main message types plus messages sent using `console.log()`. -->

コンソールの出力での右クリックで表示されるコンテキストメニューには3つのメッセージの種類に加えて`console.log()`で送られるメッセージのチェックボックスによる切り替えがあります。

<!-- Sometimes, though, you just need to manage it by wiping it clear. **CTRL + L** is a quick keyboard shortcut to clear all the messages and output in the **Console tool**. -->

時々ではあるものの、きれいさっぱりクリアしたいということがあります。**CTRL + L**はコンソールのすべてのメッセージと出力をクリアする素早いキーボードショートカットです。