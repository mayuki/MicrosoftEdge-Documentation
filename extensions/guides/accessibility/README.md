# アクセシビリティー


## Microsoft Edgeのためのアクセシブルな拡張のアイコンを作る

サードパーティーの拡張開発者はアイコンが明るいあるいはダークテーマのどちらでもはっきりと視認できるよう、Microsoftの厳格なアクセシビリティー要件を満たす画像アセットを使うことを推奨しています。全ての拡張のアイコンはアイコンの背景と優位な色が14:1の比率を持つことをお勧めします。


Microsoftによって開発されたファーストパーティー拡張は要件を満たすために“stickering” (ステッカー化) ビジュアル処理を適用しています。

### "ステッカー化" の例

“ステッカー化” の主なゴールはアイコンをどんな背景色の上でも目に見えてアクセシブルにすることです。ハイコントラスト要件をサポートするにはアイコンとその外側の白い縁との間の推奨される色の比率は 14:1 となるべきです。

#### よいアイコン
ステッカー化をした場合、ほとんどが黒いアイコンがどんな背景色の上でも視認できるままになります。


![image of icon being visible on any background color](../../media/accessibility-light-to-dark-good.png)
 
#### ダメなアイコン
ステッカー化をしていない場合、アイコンは背景と同化して見えなくなります。


![image of icon blending into black background](../../media/accessibility-light-to-dark-bad.png)

### 拡張のアイコンを"ステッカー化"

以下の5つのステップはMicrosoftのアクセシビリティー要件を満たす拡張のアイコンを作る方法の概略です。

Step 1 | Step 2 | Step 3 | Step 4 | Step 5
:---- | :----- | :------ | :------ | :------
指定したグリッドにアイコンを納めます	| アイコンサイズを2ピクセル縮めます | その場にアイコンをコピー、ペーストし、2ピクセルで角丸の縁取りをします | 縁取りをアウトライン化して、複合パスを解除し、残ったシェイプを結合します	| 外側の縁を白く、アイコンを好きなように色付けします 
![step1](../../media/accessibility-step1.png) |![step2](../../media/accessibility-step2.png) | ![step3](../../media/accessibility-step3.png) | ![step4](../../media/accessibility-step4.png) | ![step5](../../media/accessibility-step5.png)
