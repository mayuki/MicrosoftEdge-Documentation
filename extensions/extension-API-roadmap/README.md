<!-- # Microsoft Edge extension API roadmap -->
# Microsoft Edge 拡張 API ロードマップ

<!-- In addition to web APIs, the extension API allows extensions to achieve deeper integration with the browser host. This API gives developers access to Microsoft Edge’s browser features such as tab and window manipulation.  Check out the table below for descriptions on how these classes can empower your extensions. -->

Web APIだけでなく拡張APIで、拡張がブラウザーホストとの密な統合を成し遂げられるようにします。拡張APIはMicrosoft Edgeのタブやウィンドウ操作といったブラウザー機能へのアクセスを提供します。これらAPIのクラスが拡張にどのような力を与えてくれるのかといった説明は下のテーブルでご確認ください。

<!-- This table also details our current progress towards completing the Microsoft Edge extension API. Status updates will be made here as classes move through development towards completion.-->

このテーブルはMicrosoft Edge 拡張 APIの完成に向けた現在の進捗の詳細でもあります。クラスの開発が動き出し、完成に向かうと、ステータスのアップデートはここに記されます。


| クラス         | 説明 | ステータス
|---------------|--------------|---------------------|
|bookmarks     | ブックマークを作成、管理、操作するために使用されます | Under consideration |
|browserAction | 拡張からMicrosoft Edgeの永続的なボタンを追加できるようにします | In development
|contextMenus  | 特定のURL、特定のWebページのコンテキストでのコンテキストメニューの項目を追加します | In development
|cookies       | Cookieのクエリーと変更、それらの変更の通知に使用されます | In development |
|downloads     | ダウンロードの開始、監視、操作、検索をプログラムから行うために使用されます | Under consideration |
|extension     | あらゆる拡張のページで利用できるユーティリティを含みます | In development      |
|history       | ブラウザーの訪問済みページの記録とやり取りします | Under consideration |
|i18n          | 拡張全体で利用できる国際化機能を実装します | In development      |
|idle          | コンピューターがアイドル状態になったことを検知するために使用されます | In development |
|notifications | ユーザーのシステムトレイに表示する、テンプレートを利用した通知を作成できるようにします | Under consideration |
|pageAction    | 拡張がアドレスバーの中にボタンを追加できるようにします | In development      |
|permissions   | ユーザーがオプションのパーミッションを選択して、拡張のアクセスを許可したいといったことをできるようにします | Under consideration
|runtime       | バックグラウンドページの取得や、マニフェストについての詳細を返したり、拡張のライフサイクルイベントに応答するためにリッスンします | In development
|storage       | データーの読み書きとデーターの同期を拡張が行うために使用されます | In development
|tabs          | ブラウザーのタブの作成、変更、並び替えといったMicrosoft Edgeのタブシステムとやり取りします | In development
|webNavigation | 発行されたナビゲーションリクエストの状態についての通知を受け取るために使用されます | In development
|webRequest    | webRequest APIを利用することでトラフィックを監視、解析し、発行されたリクエストをインターセプト、ブロック、変更を行えるようにします | In development
|windows       | ウィンドウの作成、変更、並び替えをブラウザーとやり取りします | In development

<!--
| Class         | Description | Status
|---------------|--------------|---------------------|
bookmarks     | Used to create, organize, and manipulate bookmarks. | Under consideration |
browserAction | Enables extensions to add a persistent button within Microsoft Edge. | In development
contextMenus  | Adds a context menu item on a specific URL, in a specified context of a webpage. | In development
cookies       | Used to query and modify cookies, as well as notify when they change. | In development |
downloads     | Used to programmatically initiate, monitor, manipulate, and search for downloads. | Under consideration |
extension     | Contains utilities that can be used by any extension page. | In development      |
history       | Interacts with the browser's record of visited pages. | Under consideration |
i18n          | Implements internationalization across an extension. | In development      |
idle          | Used to detect when the machine's idle state is changed. | In development |
notifications | Allows creation of notifications using templates to be displayed in the user's system tray. | Under consideration |
pageAction    | Enables extensions to add a button inside the address bar. | In development      |
permissions   | Allows users to select what optional permissions they would like to grant an extension access to. | Under consideration
runtime       | Retrieves the background page, returns details about the manifest, and listens for and responds to events in the extension lifecycle. | In development
storage       | Used by the extension to read/write data and to sync data. | In development
tabs          | Interacts with Microsoft Edge's tab system by creating, modifying, and rearranging tabs in the browser. | In development
webNavigation | Used to receive notifications about the status of navigation requests in-flight. | In development
webRequest    | Enables use of the webRequest API to observe and analyze traffic and to intercept, block, or modify requests in-flight. | In development
windows       | Interacts with the browser by creating, modifying, and rearranging windows. | In development
-->