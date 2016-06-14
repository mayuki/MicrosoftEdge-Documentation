## トラブルシューティング

[https://dev.windows.com](http://www.aka.ms/msedge-extensions)からダウンロードしたパッケージングされていない拡張を読み込ませようとし、問題に遭遇した際には次のトラブルシューティングのトピックが役立つかもしれません:

### 1. "We couldn't load this extension"と表示された

これは、読み込ませようとした際にMicrosoft Edgeが拡張のフォルダーにアクセスできなかったことを意味することが大体です。拡張のフォルダーを削除して、.EXEを再度実行して、**Downloads**に作成された拡張のフォルダーからの読み込みを試してみてください。


### 2. "Load extension"ボタンが見つからない
拡張がWindows Storeから利用できるようになるまでの間、このボタンはデフォルトで表示されている*はず*です。もし"More" (...)メニューを開いて、"Extensions"メニュー項目を選択し、ボタンが見つからない場合には次の手順をお試しください:
 
1. アドレスバーに**"about:flags"**を入力して、**"Enter"**キーを押します
2. **"Developer settings"**項目にある、**"Allow unpacked extensions to be loaded"**チェックボックスが選択されているか確認します

   ![about flags](../media/aboutflags.PNG)  

3. Microsoft Edgeを閉じて、再度開きなおし、**"Load extension"**ボタンが表示されることを確認します