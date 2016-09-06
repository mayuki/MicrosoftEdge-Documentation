# Microsoft Edge 拡張 API ロードマップ

Web APIだけでなく拡張APIで、拡張がブラウザーホストとの密な統合を成し遂げられるようにします。拡張APIはMicrosoft Edgeのタブやウィンドウ操作といったブラウザー機能へのアクセスを提供します。これらAPIのクラスが拡張にどのような力を与えてくれるのかといった説明は下のテーブルでご確認ください。

このテーブルはMicrosoft Edge 拡張 APIの完成に向けた現在の進捗の詳細でもあります。クラスの開発が動き出し、完成に向かうと、ステータスのアップデートはここに記されます。

| クラス         | 説明 | ステータス
|---------------|--------------|---------------------|
bookmarks     | ブックマークを作成、管理、操作するために使用されます | In development |
browserAction | 拡張からMicrosoft Edgeの永続的なボタンを追加できるようにします | Supported — Microsoft Edge (38) / Windows 10 (14393)
contextMenus  | 特定のURL、特定のWebページのコンテキストでのコンテキストメニューの項目を追加します | Supported — Microsoft Edge (38) / Windows 10 (14393)
cookies       | Cookieのクエリーと変更、それらの変更の通知に使用されます | Supported — Microsoft Edge (38) / Windows 10 (14393) |
downloads     | ダウンロードの開始、監視、操作、検索をプログラムから行うために使用されます | Under consideration |
extension     | あらゆる拡張のページで利用できるユーティリティを含みます | Supported — Microsoft Edge (38) / Windows 10 (14393)      |
history       | ブラウザーの訪問済みページの記録とやり取りします | Under consideration |
i18n          | 拡張全体で利用できる国際化機能を実装します | Supported — Microsoft Edge (38) / Windows 10 (14393)      |
idle          | コンピューターがアイドル状態になったことを検知するために使用されます | Supported — Microsoft Edge (38) / Windows 10 (14393) |
notifications | ユーザーのシステムトレイに表示する、テンプレートを利用した通知を作成できるようにします | Under consideration |
pageAction    | 拡張がアドレスバーの中にボタンを追加できるようにします | Supported — Microsoft Edge (38) / Windows 10 (14393)      |
permissions   | ユーザーがオプションのパーミッションを選択して、拡張のアクセスを許可したいといったことをできるようにします | Under consideration
runtime       | バックグラウンドページの取得や、マニフェストについての詳細を返したり、拡張のライフサイクルイベントに応答するためにリッスンします | Supported — Microsoft Edge (38) / Windows 10 (14393)
storage       | データーの読み書きとデーターの同期を拡張が行うために使用されます | Supported — Microsoft Edge (38) / Windows 10 (14393)
tabs          | ブラウザーのタブの作成、変更、並び替えといったMicrosoft Edgeのタブシステムとやり取りします | Supported — Microsoft Edge (38) / Windows 10 (14393)
webNavigation | 発行されたナビゲーションリクエストの状態についての通知を受け取るために使用されます | Supported — Microsoft Edge (38) / Windows 10 (14393)
webRequest    | webRequest APIを利用することでトラフィックを監視、解析し、発行されたリクエストをインターセプト、ブロック、変更を行えるようにします | Supported — Microsoft Edge (38) / Windows 10 (14393)
windows       | ウィンドウの作成、変更、並び替えをブラウザーとやり取りします | Supported — Microsoft Edge (38) / Windows 10 (14393)
