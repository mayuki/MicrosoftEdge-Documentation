# フォルダーアップロード

Microsoft Edgeはファイルやフォルダー、ファイルとフォルダーの組み合わせのアップロードをChromeと互換性のあるAPIを使うことでサポートしています。

| API | Description |
| --- | ----------- |
| DataTransferItem.[webkitGetAsEntry](https://msdn.microsoft.com/library/mt709130) メソッド | `DataTransferItem` に対する `WebKitEntry` オブジェクト (ファイルまたはディレクトリー) を返します。 |
| [WebKitEntry](https://msdn.microsoft.com/library/mt732557) インターフェース | ファイルまたはディレクトリを表します。(`isDirectory` と `isFile` プロパティを使うことで判別できます) |
| [WebKitDirectoryReader](https://msdn.microsoft.com/library/mt732554) インターフェース | 指定されたディレクトリーに含まれているファイルを走査する `readEntries` メソッドを提供します。 |
| [WebKitFileSystem](https://msdn.microsoft.com/library/mt732564) インターフェース | アップロードのために(サンドボックス化済み)ファイルシステムへのインターフェースを提供します。`WebKitEntry` オブジェクトの `filesystem` プロパティを使うことでドラッグアンドドロップ(または ファイル/フォルダー選択)操作で利用するグローバルにユニークな名前とファイルシステムのルートフォルダーを取得できます。 |

## 例

that's been selected for upload.
このコードの断片はアップロードのために選択したファイルとフォルダーのアイテムの区別の付け方のサンプルです。

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/wWwBqa?editors=1010)

![spec](FileSystemAPI)

## API Reference

[FileSystem API](https://msdn.microsoft.com/library/mt732552)

## Specification

[FileSystem API](https://wiki.whatwg.org/wiki/DragAndDropEntries)
