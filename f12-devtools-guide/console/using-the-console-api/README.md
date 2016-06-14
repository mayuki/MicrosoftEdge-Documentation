# コンソールAPIを使う

コンソールAPIは意味ある情報をアプリケーションからコンソールに送ったり、コンソールツールの中から診断情報を得るために開発者のためのメソッドを提供します。

## コードからレポートする
[コンソールデバッグAPI](https://msdn.microsoft.com/library/hh772173.aspx)はコードからコンソールへ情報を送信する方法を提供します。情報は次の種類に分類されます:

  - [カスタムメッセージ](#カスタムメッセージ)
  - [調査可能なオブジェクトとノード](#調査可能なオブジェクトとノード)
  - [カウンター](#カウンター)
  - [タイマー](#タイマー)
  - [アサーション](#アサーション)
  - [トレース](#トレースとプロファイル)

### カスタムメッセージ
カスタムメッセージには4つの選択肢があります。3つはシステムメッセージの書式に使います: [`console.info()`](https://msdn.microsoft.com/library/hh772178.aspx)は情報メッセージ、[`console.warn()`](https://msdn.microsoft.com/library/hh772181.aspx)は警告メッセージ、 [`console.error()`](https://msdn.microsoft.com/library/hh772176.aspx)はエラーです。4つ目、[`console.log()`](https://msdn.microsoft.com/library/hh772179.aspx)はアラートアイコンを表示しないプレーンなテキストです。4つともすべてメッセージには同様の引数をとります。

**テキストだけの場合:**

```JavaScript
console.log('This is some text');
```
>`This is some text`


**変数だけの場合:**

```javascript
var mytext = 'This is some text';
console.log(mytext);
```
>`This is some text`

**テキストと変数の混在:**

```javascript
var mytext = 'pieces';
var myval = 0;
console.log("The number of " + mytext + "is " + myval);
```
>`The number of pieces is 0`

**変数置換:**

```javascript
var mytext = 'pieces';
var myval = 5;
console.log("The number of %s is %d", mytext, myval);
```
>`The number of pieces is 5`

変数置換は5つの変数型を持ちます:
  - %**s** - 文字列
  - %**d** - 整数
  - %**i** - 整数
  - %**f** - 浮動小数
  - %**o** - オブジェクト
  - %**b** - バイナリ
  - %**x** - 16進数
  - %**e** - 指数

変数型は変数をどう表現したらよいのかをコントロールします。例えば、float値を整数変数型で表現すると整数として表示されます。

### 調査可能なオブジェクトとノード
調査可能なオブジェクトは広げることのできるノードとして折りたたまれたツリー形式でコンソールに表示されます。コンソールは送られてきたものがdivのようなDOMノードであるのか、イベントのようなJavaScriptのオブジェクトであるのかといった種類を自動的に判別します。

調査可能なJavaScriptオブジェクトを表示するには、[`console.dir()`](https://msdn.microsoft.com/library/jj152132.aspx)を利用してコンソールに送ります。

調査可能なDOMノードを表示するには、[`console.dirxml()`](https://msdn.microsoft.com/library/dn265067.aspx)を利用してコンソールに送ります。

codepenのサンプルをF12ツールと共に開いて、"show it"ボタンをクリックするとオブジェクトとノードがコンソールに表示されます。

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/PNEKQX?editors=1010)(325)

下のコンソールのスクリーンショットでは左の矢印を使い、オブジェクトとノードを開いているところです。

![Edge Console Inspectable objects and nodes](../../media/Edge_Console2.png)

DOMノードを右クリックすると表示されるコンテキストメニューに**Evaluate as Object**という選択肢があります。この選択肢を選ぶと、ノードをコンソールにオブジェクトして送ることができます。同様に、DOMノードのJavaScriptのオブジェクト表現のコンテキストメニューには**Evaluate as HTML**が用意されています。

### カウンター
コードでカウンターをセットするのは比較的簡単な半面、何度も繰り返されるタスクでもあります。開発者のワークフローをスピードアップするため、コンソールデバッグAPIは単純な短縮記述を提供します。

<<<<<<< HEAD
[`console.count()`](https://msdn.microsoft.com/library/dn265064.aspx)をカウンターのラベルを持つ文字列を引数として呼び出します。初回の呼び出しで指定したラベルでカウンターがコンソールに出力されます。続いて`console.count()`を同じラベルで呼び出すとカウンターが加算されます。カウンターをリセットして0にするにはラベルを指定して`console.countReset()`を呼び出します。
=======
Use [`console.count()`](https://msdn.microsoft.com/library/dn265064.aspx) with a string containing a counter label as its argument. The first use with a specific label establishes a counter in the Console output. Subsequent uses of `console.count()` with the same label increment the counter. To reset the counter to zero, use `console.countReset()` with the label.
>>>>>>> f558c17fdf417c5b524d0bec25daa820ebd5db3d

```javascript
console.count('mylabel');
for(var i = 0; i < 10; i++){
  console.count('mylabel');
}
```
>`mylabel:         11`

### タイマー
カウンターを作るのと同じように、コード中にタイマーを作るのも比較的簡単です。しかし[コンソールデバッグAPI](https://msdn.microsoft.com/library/hh772173.aspx)はそれをさらに簡単するべく単純で短縮記述法を提供しています。

[`console.time()`](https://msdn.microsoft.com/library/dn265071.aspx)をコードのどこかで呼び出すことでタイマーを開始し、[`console.timeEnd()`](https://msdn.microsoft.com/library/dn265072.aspx)でタイマーを止めて結果をコンソールに送ります。もしタイマーにラベルを付けたい、または2つ以上のタイマーを使いたいのであれば、`console.time()`と`console.timeEnd()`メソッドの両方の引数にユニークなラベルとなる文字列を渡してください。引数を渡していない場合にはメソッドは"default"をラベルとして使います。

`console.timeStamp()`は言わばページの年齢です。メソッドはタイムスタンプをコンソールに出力し、現在のWebページが読み込まれてからのミリ秒を表示します。もしメソッドの引数に数値または文字列を渡した場合、それはラベルとして扱われ、デフォルトのラベルである"timestamp"を上書きします。**UI Responsiveness**プロファイルセッション中に呼び出した場合、コンソール出力に加えて、セッションタイムラインにユーザーマークがセッションが開始された時からの時間と共に追加されます。

### アサーション
アサーションは開発者のワークフローをスピードアップするための異なる短縮記法です。[`console.assert()`](https://msdn.microsoft.com/library/hh772171.aspx)を呼び出す際に第一引数の評価結果がfalseとなる場合、[`console.error()`](https://msdn.microsoft.com/library/hh772176.aspx)を実行し、アサーションの追加の引数をエラーメッセージとして使います。

コードの使用している行:

`console.assert(f < 25, 'f is not less than %d, but is instead %o', 25, f);`

これは下記のように書くのと同様:

```javascript
if(!(f < 25)){
  console.error('f is not less than %d, but is instead %o', 25, f)
}
```

サンプルコード中で、変数を出力するために`%o`を利用しています。これは変数の値が数値ではない場合に上の評価は失敗するため、`%o`を使うことで特定の型にキャストする代わりに変数の値を見れる形にします。

### トレースとプロファイル
コードがどこから呼ばれているのか、どのコードが実行されているのか、実行するのにどのぐらいの時間がかかっているのかを知るということは、遅さあるいは予期していない挙動の解析に役立ちます。

スタックトレースはコードがトレース要求にたどり着くまでの上方の実行パスを表示します。
[`console.trace()`](https://msdn.microsoft.com/library/hh772176.aspx)をコードから呼び出すことでスタックトレースを表示できます。

このコードが...

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

### メッセージの読みやすさを管理する
**メッセージをグループに分ける**

メッセージの種類と内容がコンソールに送られてはいるものの、それらを追い続けることは難しいかもしれません。

  - [`console.group()`](https://msdn.microsoft.com/library/dn265068.aspx) は展開状態で折りたたみ可能なグループを開始します。このコマンド以降に送信されたメッセージはグループに入り、`console.groupEnd()`メソッドが呼び出されるまで続きます。メソッドの第一引数に文字列を渡した場合、文字列はグループのラベルとして使用されます
  - [`console.groupCollapsed()`](https://msdn.microsoft.com/library/dn265069.aspx)は折りたたまれた状態で折りたたみ可能なグループを開始します。ほかの点は`console.group()`と同様に振る舞います
  - [`console.groupEnd()`](https://msdn.microsoft.com/library/dn265068.aspx)は一番最近開かれたグループを閉じます
  - [`console.clear()`](https://msdn.microsoft.com/library/jj152131.aspx)は現在コンソールに表示されているすべてのメッセージを削除します

グループはグルーピングをさらに詳細なものにするため他のグループをネストできます。

異なるメッセージの種類をオン/オフするにはフィルタリングを使用します。

**コンソール**の上部にはエラー、警告、情報のメッセージのアイコンが件数と共に並んでいます。アイコンをクリックすることでその種類のメッセージの表示をオン、オフが切り替わります。オフに切り替わったときはその種類のメッセージは非表示となりますが、削除はされていないため、もう一度メッセージの種類を切り替えることで元に戻せます。

コンソールの出力での右クリックで表示されるコンテキストメニューには3つのメッセージの種類に加えて`console.log()`で送られるメッセージのチェックボックスによる切り替えがあります。

時々ではあるものの、きれいさっぱりクリアしたいということがあります。**CTRL + L**はコンソールのすべてのメッセージと出力をクリアする素早いキーボードショートカットです。