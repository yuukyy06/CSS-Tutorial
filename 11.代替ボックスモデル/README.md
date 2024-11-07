## ボックスモデルとは？
ボックスモデルはブロックボックスに適用され、ボックスサイズをどのように設定するかを定義します。「07 余白を学ぼう」で、`width`や`height`プロパティで要素自身の幅や高さを変更しました。さらに`padding`や`border`プロパティを追加することで、ボックスサイズは「要素＋`padding`エリア＋`border`エリア」となりました。これは、標準ボックスモデル「**content-box**」での振舞いになります。

![image](https://github.com/user-attachments/assets/c5f7bf28-d96c-4ba2-bf97-852b8511f87f)

例えば、ボックスサイズ240px×36pxの範囲内で`border`を1pxとして「要素＋`padding`エリア＋`border`エリア」を収めたい場合は、要素のサイズを238px×34pxと算出して宣言する必要があります。毎回これをやるのは大変ですよね？  
そこで、代替ボックスモデルとして「**border-box**」があります。これは、`width`や`height`プロパティでボックスサイズ（`border`エリアまでのサイズ）を指定します。上記の例では、`width`と`height`プロパティで240px×36pxと指定し、必要なサイズの`border`プロパティを指定すれば、要素自身のサイズが自動算出されます。

```css
/* content-boxの場合 */
要素セレクター {
  width: 238px; /* 要素の幅 */
  height: 34px; /* 要素の高さ */
  border-width: 1px;
}

/* border-boxの場合 */
要素セレクター {
  width: 240px; /* ボックスサイズの幅 */
  height: 36px; /* ボックスサイズの高さ */
  border-width: 1px;
}
```

## box-sizing
ボックスモデルを指定するには`box-sizing`プロパティを使用します。デフォルトは標準ボックスモデルのcontent-boxなので、指定する場合は代替ボックスモデルのborder-boxを指定する時になります。以下のコードで確認してみましょう。

```html
<div class="content">content-box</div>
<div class="border">border-box</div>
```
```css
.border {
  box-sizing: border-box;
}

div {
  width: 300px;
  height: 200px;
  border: 5px solid green;
  padding: 50px;

  background-color: yellow;
  margin: 10px;
  text-align: center;
}
```

2つ`div`要素に対し、borderクラスには代替ボックスモデルを適用し、それ以外は全く同じスタイルを適用しています。

![image](https://github.com/user-attachments/assets/881fd532-801f-46e1-b1d2-65da00c66727)

標準ボックスモデルでは、要素自身（黄色）のエリアが300px×200px、`padding`エリアがすべて50px、`border`エリアがすべて5pxなので、ボックスサイズは410px×310pxとなります。  
代替ボックスモデルでは、ボックスサイズが300px×200pxとなり、その内側に`border`エリアと`padding`エリアがあります。要素自身のサイズは190px×90pxが自動算出されています。

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
    <h1>My Trips</h1>
    <ul>
      <li><a href="">Home</a></li>
      <li><a href="">Picture</a></li>
      <li><a href="">Blog</a></li>
    </ul>
  </header>
  <main>
    <div>
      <img src="img/eiffel.jpg" alt="エッフェル塔">
      <p>エッフェル塔</p>
    </div>
    <div>
      <img src="img/antelope.jpg" alt="アンテロープキャニオン">
      <p>アンテロープキャニオン</p>
    </div>
    <div>
      <img src="img/grand.jpg" alt="グランドキャニオン">
      <p>グランドキャニオン</p>
    </div>
  </main>
</body>
</html>
```

1. すべての`img`要素の幅と高さを300pxにしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* img要素にスタイルを適用 */
    img {
      width: 300px;
      height: 300px;
    }
    ```
    </details>

2. `div`要素のボックスサイズを幅320px・高さ360pxとし、borderを1px・実線・#800000で指定してください。また3つの`div`要素を横並びにしたいので、インラインボックスにしてください。
    <details>
    <summary>回答例</summary>
    
    ```css
    /* div要素にスタイルを適用 */
    div {
      box-sizing: border-box;
      width: 320px;
      height: 360px;
      border: 1px solid #800000;
      display: inline-block;
    }
    ```
    </details>


すべて記述できるとブラウザでは以下のように表示されます。うまく表示されない場合は、コードを良く見返して修正しましょう。

![image](https://github.com/user-attachments/assets/ec79df50-d718-495c-b8ff-7dc92a3ba96a)

## GitHubへプッシュしよう
編集した内容をステージング＆コミットし、自身のGitHubにあるリモートリポジトリにプッシュしましょう。以下のコマンドを実行します。

```bash
# すべてのファイルをステージング
git add .

# コミット（コミットメッセージは自由に記述してください）
git commit -m "Par11 代替ボックスモデル"

# リモートリポジトリへプッシュ
git push origin main
```