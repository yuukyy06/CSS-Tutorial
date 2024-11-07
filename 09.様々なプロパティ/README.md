CSSには様々なプロパティがあります。ここでは、今までに紹介したもの以外にもよく使われるプロパティをいくつか紹介します。

## object-fit

様々なサイズの画像を並べて同じサイズで表示したい時に使用され、HTMLの`img`要素や`video`要素に対して使用されます。

【指定できる値】
- fill（デフォルト値）：縦横比を維持せず、要素のサイズに変形
- contain：縦横比を維持して、幅もしくは高さの大きい方のサイズに拡大・縮小
    - 要素の縦横比と画像の縦横比が異なる場合は、画像がすべて表示されます。
- cover：縦横比を維持して、幅もしくは高さの小さい方のサイズに拡大・縮小
    - 要素の縦横比と画像の縦横比が異なる場合は、画像のはみ出た部分が非表示となります。
- none：画像サイズのまま表示
- scale-down：noneとcontainのうち小さい方に合わせて表示
    - 要素のサイズよりも画像が大きい場合 ⇒ noneが適用
    - 要素のサイズよりも画像が小さい場合 ⇒ containが適用

それぞれどのように表示されるか見てみましょう。サイズが400px×300pxの画像を5つ配置し、それぞれに`object-fit`プロパティを適用させます。`img`要素自体のサイズはすべて200px×200pxにしています。

```html
<div>
  <img class="fill" src="img/lion-small.JPG" alt="fill">
  <p>object-fit: fill;</p>
</div>
<div>
  <img class="contain" src="img/lion-small.JPG" alt="contain">
  <p>object-fit: contain;</p>
</div>
<div>
  <img class="cover" src="img/lion-small.JPG" alt="cover">
  <p>object-fit: cover;</p>
</div>
<div>
  <img class="none" src="img/lion-small.JPG" alt="none">
  <p>object-fit: none;</p>
</div>
<div>
  <img class="scale-down" src="img/lion-small.JPG" alt="scale-down">
  <p>object-fit: scale-down;</p>
</div>
```
```css
div {
  margin-bottom: 20px;
  display: inline-block;
  width: 250px;
}

/* img要素のサイズを200px×200pxで統一 */
img {
  width: 200px;
  height: 200px;
}

.fill {
  object-fit: fill;
}

.contain {
  object-fit: contain;
}

.cover {
  object-fit: cover;
}

.none {
  object-fit: none;
}

.scale-down {
  object-fit: scale-down;
}
```

![image](https://github.com/user-attachments/assets/7bcc3f61-9d14-482a-b316-11629b21b38a)

fillでは幅方向に変形、containでは上下に空白が表れ、coverでは画像の両サイドがカットされ、noneでは画像の上下左右ががカットされ、scale-downではcontainが採用されていますね。

## position

要素の配置を設定するために使用されます。`position`プロパティを指定した後、位置を指定するためのプロパティ（`top`、`right`、`bottom`、`left`、`z-index`）で詳細な値を指定していきます。

【指定できる値】
- static（デフォルト値）：デフォルトの配置（位置指定のプロパティは効果無し）
- relative：デフォルトの配置を基準に相対的な位置を指定
- absolute：デフォルトの配置からは除外され、ページを基準に相対的な位置を指定
    - 親要素に`position`プロパティが適用されている場合はその親要素を基準に配置されます。
- fixed：デフォルトの配置からは除外され、画面の決まった位置を指定
- sticky：デフォルトの配置を基準に相対的な位置を指定
    - スクロール時に画面内に表示され続けます。

【位置を指定するためのプロパティ】
- `top`：上側の隙間を指定
- `right`：右側の隙間を指定
- `bottom`：下側の隙間を指定
- `left`：左側の隙間を指定
- `z-index`：重なりの順序を指定

`z-index`以外はいずれもpxやem、%などで指定できます。`z-index`は優先順位を数値で指定し、数値が大きい方が前面に表示されます。  
それぞれの使い方について以下のコードで見ていきましょう。

```html
<div class="container">
  <img class="img1" src="img/lion-small.JPG" alt="lion">
  <img class="img2" src="img/lion-small.JPG" alt="lion">
  <img class="img3" src="img/lion-small.JPG" alt="lion">
</div>
```
```css
.container {
  display: inline-block;
  margin: 50px
}

img {
  width: 200px;
  height: 200px;
  object-fit: cover;
}
```

![image](https://github.com/user-attachments/assets/faa7bf8a-bffe-4d07-ab77-70ca1c52b9ab)

### relative
img2クラスの要素に以下のスタイルを適用してみましょう。

```css
.container {
  display: inline-block;
  margin: 50px
}

img {
  width: 200px;
  height: 200px;
  object-fit: cover;
}

/* img2クラスにpositionプロパティとtop,leftプロパティを指定 */
.img2 {
  position: relative;
  top: 30px;
  left: 50px;
}
```

![image](https://github.com/user-attachments/assets/b0696973-1f85-4bec-a3cb-e133d421be26)

元の位置から上側に30px、左側に50pxの隙間ができました。（下に30px、右に50px移動）ここで`z-index`プロパティを指定して、img2クラスの要素を最背面にしてみましょう。
```css
.container {
  display: inline-block;
  margin: 50px
}

img {
  width: 200px;
  height: 200px;
  object-fit: cover;
}

.img2 {
  position: relative;
  top: 30px;
  left: 50px;
  /* z-indexプロパティを指定 */
  z-index: -1;
}
```

![image](https://github.com/user-attachments/assets/d0346139-8495-4cd2-aab2-7c9f51e3d200)

重なりの順序が変わって、img2クラスの要素が最背面になりましね。

### absolute
img2クラスの要素に以下のスタイルを適用してみましょう。

```css
.container {
  display: inline-block;
  margin: 50px
}

img {
  width: 200px;
  height: 200px;
  object-fit: cover;
}

/* img2クラスにpositionプロパティとtop,leftプロパティを指定 */
.img2 {
  position: absolute;
  top: 30px;
  left: 50px;
}
```

![image](https://github.com/user-attachments/assets/a5d75b9e-7932-4715-9f44-5be64babc4dc)

img2クラスの要素はデフォルトの位置から除外され、画面の左上（`body`要素）を基準にして上側に30px、左側に50pxの隙間ができました。（下に30px、右に50px移動）  
ここで、containerクラスの`div`要素に`position: relative;`を適用するとどうなるか見てみましょう。

```css
.container {
  display: inline-block;
  /* positionプロパティを指定 */
  position: relative;
  margin: 50px
}

img {
  width: 200px;
  height: 200px;
  object-fit: cover;
}

/* img2クラスにpositionプロパティとtop,leftプロパティを指定 */
.img2 {
  position: absolute;
  top: 30px;
  left: 50px;
}
```

![image](https://github.com/user-attachments/assets/e0661da9-4b72-42ca-8027-87b1448ea607)

img2クラスの要素の基準が`body`要素ではなく、containerクラスの`div`要素になりました。親要素を基準とすることで、階層が深くなっても指定すべき値が分かりやすくなりますね。

### fixed
img2クラスの要素に以下のスタイルを適用してみましょう。

```css
.container {
  display: inline-block;
  margin: 50px
}

img {
  width: 200px;
  height: 200px;
  object-fit: cover;
}

/* img2クラスにpositionプロパティとtop,leftプロパティを指定 */
.img2 {
  position: fixed;
  top: 30px;
  left: 50px;
}
```

![image](https://github.com/user-attachments/assets/14b515de-2d19-4ed2-83c3-71b17dffed16)

img2クラスの要素はデフォルトの位置から除外され、画面の左上を基準にして上側に30px、左側に50pxの隙間ができました。（下に30px、右に50px移動）  
親要素に`position`プロパティを設定していない時と同じですね？では、ここでもcontainerクラスの`div`要素に`position: relative;`を適用するとどうなるか見てみましょう。

```css
.container {
  display: inline-block;
  /* positionプロパティを指定 */
  position: relative;
  margin: 50px
}

img {
  width: 200px;
  height: 200px;
  object-fit: cover;
}

/* img2クラスにpositionプロパティとtop,leftプロパティを指定 */
.img2 {
  position: fixed;
  top: 30px;
  left: 50px;
}
```

![image](https://github.com/user-attachments/assets/60a61c97-d456-444d-89fd-1e3bfa37a2bd)

absoluteとは違い、こちらは全く変化がありません。これがabsoluteとfixedの違いです。

### sticky
こちらでは以下のコードで解説していきます。

```html
<body>
  <header>
    <h1>CSSハンズオン</h1>
    <h3>Part9</h3>
  </header>
  <main>
    <div>
      <img src="img/lion-small.jpg" alt="lion">
      <p>シンガポールのマーライオン</p>
    </div>
    <div>
      <img src="img/lion-small.jpg" alt="lion">
      <p>シンガポールのマーライオン</p>
    </div>
    <div>
      <img src="img/lion-small.jpg" alt="lion">
      <p>シンガポールのマーライオン</p>
    </div>
    <div>
      <img src="img/lion-small.jpg" alt="lion">
      <p>シンガポールのマーライオン</p>
    </div>
    <div>
      <img src="img/lion-small.jpg" alt="lion">
      <p>シンガポールのマーライオン</p>
    </div>
  </main>
</body>
```
```css
header {
  text-align: center;
  background-color: darkblue;
  color: white;
}

main {
  text-align: center;
}

div {
  margin-bottom: 32px;
}

img {
  width: 200px;
  height: 200px;
  object-fit: cover;
}

p {
  margin: 0;
}
```

![image](https://github.com/user-attachments/assets/d24030e1-4374-4fda-bea5-3e9abd8529ba)

現在のコードでは画面をスクロールすると`header`要素は表示されなくなります。この`header`要素にstickyを適用してみましょう。

```css
header {
  text-align: center;
  background-color: darkblue;
  color: white;
  /* positionプロパティでstickyを適用 */
  position: sticky;
  top: 12px;
}

main {
  text-align: center;
}

div {
  margin-bottom: 32px;
}

img {
  width: 200px;
  height: 200px;
  object-fit: cover;
}

p {
  margin: 0;
}
```

![image](https://github.com/user-attachments/assets/4c21d2c8-dd2d-432e-b451-e19a5969b804)

スクロールをしてもずっと`header`要素が表示されるようになりました。`top`プロパティでは、要素の位置を指定しており、スクロール時にどの位置に残すかもここで指定できます。  
今回、stickyを適用した`header`要素は「スティッキーアイテム」、その親要素である`body`要素は「スティッキーコンテナ」となり、スティッキーアイテムはスティッキーコンテナ内でのみ表示可能となります。では、`h1`要素にstickyを適用するとどうなるでしょう？挙動予想してみてください。

```css
header {
  text-align: center;
  background-color: darkblue;
  color: white;
}

/* h1要素にpositionプロパティでstickyを適用 */
h1 {
  position: sticky;
  top: 0;
}

main {
  text-align: center;
}

div {
  margin-bottom: 32px;
}

img {
  width: 200px;
  height: 200px;
  object-fit: cover;
}

p {
  margin: 0;
}
```

![image](https://github.com/user-attachments/assets/680ec3d8-0ab2-48d5-b170-97537207da5b)

スティッキーコンテナは`header`要素となり、その範囲内で`p`要素を維持した範囲でしか表示されませんね？stickyを使用する時は、「スティッキーアイテム」と「スティッキーコンテナ」の関係を念頭に入れてHTMLを作成することがポイントになります。

## opacity
要素の不透明度を設定するプロパティです。0～1もしくは0～100%で指定し、値が大きいほど不透明になります。以下のコードで見ていきましょう。

```html
<body>
  <header>
    <h1>CSSハンズオン</h1>
    <h3>Part9</h3>
  </header>
  <main>
    <img src="img/lion-small.jpg" alt="lion">
    <div></div>
  </main>
</body>
```
```css
header {
  text-align: center;
  background-color: darkblue;
  color: white;
}

main {
  text-align: center;
  position: relative;
}

img {
  margin: 50px;
  width: 200px;
  height: 200px;
  object-fit: cover;
}

div {
  width: 100%;
  height: 300px;
  background-color: cadetblue;
  position: absolute;
  top: 0;
}
```

![image](https://github.com/user-attachments/assets/9eec5c29-b4b3-4ada-b540-1ae60a44906e)

`img`要素の画像が`div`要素にかくれて見えないですね。そこで`div`要素に`opacity`プロパティを適用してみましょう。

```css
header {
  text-align: center;
  background-color: darkblue;
  color: white;
}

main {
  text-align: center;
  position: relative;
}

img {
  margin: 50px;
  width: 200px;
  height: 200px;
  object-fit: cover;
}

div {
  width: 100%;
  height: 300px;
  background-color: cadetblue;
  position: absolute;
  top: 0;
  /* opacityプロパティを適用 */
  opacity: 0.5;
}
```

![image](https://github.com/user-attachments/assets/754ccbdc-11f9-45f6-a864-f77ea976a4eb)

`div`要素の不透明度が半分になったため`img`要素の画像が見えるようになりました！

## CSSを書いてみよう
インプットした内容を基に、早速手を動かして試してみましょう。index.htmlを確認し、指示に従ってCSSを書いてください。まずは自身で書いてみて、わからなければ回答例を見てもOKです。index.htmlをブラウザで表示して、ビフォーアフターも確認してみてください。

index.html

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <link rel="stylesheet" href="styles.css">
  <title>Document</title>
</head>
<body>
  <header>
    <h1>CSSハンズオン</h1>
    <h3>Part9</h3>
  </header>
  <main>
    <div class="container">
      <div class="inner-container">
        <img src="img/lion-small.jpg" alt="lion">
        <p>シンガポールのマーライオン</p>
      </div>
      <div class="inner-container">
        <img src="img/lion-small.jpg" alt="lion">
        <p>シンガポールのマーライオン</p>
      </div>
      <div class="inner-container">
        <img src="img/lion-small.jpg" alt="lion">
        <p>シンガポールのマーライオン</p>
      </div>
    </div>
    <div class="container">
      <div class="inner-container">
        <img src="img/lion-small.jpg" alt="lion">
        <p>シンガポールのマーライオン</p>
      </div>
      <div class="inner-container">
        <img src="img/lion-small.jpg" alt="lion">
        <p>シンガポールのマーライオン</p>
      </div>
      <div class="inner-container">
        <img src="img/lion-small.jpg" alt="lion">
        <p>シンガポールのマーライオン</p>
      </div>
    </div>
    <div class="container">
      <div class="inner-container">
        <img src="img/lion-small.jpg" alt="lion">
        <p>シンガポールのマーライオン</p>
      </div>
      <div class="inner-container">
        <img src="img/lion-small.jpg" alt="lion">
        <p>シンガポールのマーライオン</p>
      </div>
      <div class="inner-container">
        <img src="img/lion-small.jpg" alt="lion">
        <p>シンガポールのマーライオン</p>
      </div>
    </div>
    <div class="container">
      <div class="inner-container">
        <img src="img/lion-small.jpg" alt="lion">
        <p>シンガポールのマーライオン</p>
      </div>
      <div class="inner-container">
        <img src="img/lion-small.jpg" alt="lion">
        <p>シンガポールのマーライオン</p>
      </div>
      <div class="inner-container">
        <img src="img/lion-small.jpg" alt="lion">
        <p>シンガポールのマーライオン</p>
      </div>
    </div>
  </main>
  <footer>RareTECH</footer>
</body>
</html>
```

1. すべての`img`要素の幅と高さを200pxにし、画像が縦横比は維持したまま高さ方向がすべて表示されるようにスタイルを適用してください。
    <details>
    <summary>回答例</summary>

    ```css
    /* img要素にスタイルを適用 */
    img {
      width: 200px;
      height: 200px;
      object-fit: cover;
    }
    ```
    </details>

2. `header`要素が上端に常に表示されるように`position`プロパティなどを適用してください。
    <details>
    <summary>回答例</summary>

    ```css
    /* header要素にスタイルを適用 */
    header {
      position: sticky;
      top: 0;
    }
    ```
    </details>

3. `main`要素が`header`要素を通過する時に少しだけ透けて見えるようにしたいです。必要な要素に`opacity`プロパティを0.9で指定してください。
    <details>
    <summary>回答例</summary>

    ```css
    header {
      position: sticky;
      top: 0;
      /* header要素にopacityプロパティを追加 */
      opacity: 0.9;
    }
    ```
    </details>

すべて記述できるとブラウザでは以下のように表示されます。スクロールすると、`header`要素は表示され続け、また`opacity`プロパティのため`main`要素が少し透けて見えていますね。うまく表示されない場合は、コードを良く見返して修正しましょう。

![image](https://github.com/user-attachments/assets/693626c8-f2f8-49ba-b13e-10dda399def6)

![image](https://github.com/user-attachments/assets/9de1663d-0dad-4592-a72c-cd97404c1604)

## GitHubへプッシュしよう
編集した内容をステージング＆コミットし、自身のGitHubにあるリモートリポジトリにプッシュしましょう。以下のコマンドを実行します。

```bash
# すべてのファイルをステージング
git add .

# コミット（コミットメッセージは自由に記述してください）
git commit -m "Part9 様々なプロパティ"

# リモートリポジトリへプッシュ
git push origin main
```