## 文字色を変更する
文字色を指定するには`color`プロパティを使用します。様々な指定方法があるので、学んでいきましょう。

1. 色の名前を英語で指定

    `blue`や`yellow`など英語で指定することができます。

    ```css
    /* h1要素の文字色を青色に指定 */
    h1 {
      color: blue;
    }
    
    /* p要素の文字色を黄色に指定 */
    p {
      color: yellow;
    }
    ```
    
2. RGBで指定

    `rgb(0, 0, 225)`（青色）や`rgb(255, 255, 0)`（黄色）などで指定することができます。同じ色でも数値を細かく指定することで、英語で指定するよりも細やかに指定することができます。
    
    ```css
    /* h1要素の文字色を青色に指定 */
    h1 {
      color: rgb(255, 0, 0);
    }
    
    /* p要素の文字色を黄色に指定 */
    p {
      color: rgb(255, 255, 0);
    }
    ```
    
3. 16進数で指定

    `#0000FF`（青色）や`#FFFF00`（黄色）などで指定することができます。RGBと同様にこちらも英語で指定するよりも細やかに色を指定することができます。
    
    ```css
    /* h1要素の文字色を青色に指定 */
    h1 {
      color: #0000FF;
    }
    
    /* p要素の文字色を黄色に指定 */
    p {
      color: #FFFF00;
    }
    ```

## 背景色をを変更する
背景色を指定するには`background-color`プロパティを使用します。色の指定方法は`color`プロパティと同じです。

```css
/* p要素の背景色を黒色に指定 */
/* 英語での指定 */
p {
  color: black;
}

/* RGBでの指定 */
p {
  color: rgb(0, 0, 0);
}

/* 16進数での指定 */
p {
  color: #000000;
}
```

## 文字のサイズを変更する
文字のサイズを指定するには`font-size`プロパティを使用します。こちらも様々な指定方法があるので、学んでいきましょう。

1. px（ピクセル）で指定

    ピクセル（画素数）で指定することができます。画面のサイズが変わっても文字のサイズは固定されますが、高解像度のディスプレイでは小さく表示される場合があるので、注意してください。

    ```css
    /* h1要素の文字サイズを24pxに指定 */
    h1 {
      font-size: 24px;
    }
    
    /* p要素の文字サイズを16pxに指定 */
    p {
      font-size: 16px;
    }
    ```

2. em（エム）で指定

    emで指定すると、HTMLの親要素の`font-size`を基準に算出されます。以下のようなHTMLファイルがあるとします。

    ```html
    <!DOCTYPE html>
    <html lang="ja">
    <head>
      <meta charset="UTF-8" />
      <link rel="stylesheets" href="styles.css" />
      <title>Document</title>
    </head>
    <body>
      <h1>CSSハンズオン</h1>
      <p>ここの色を<span>緑色</span>にしてください。</p>
    </body>
    </html>
    ```

    CSSファイルで以下のように宣言すると、まず`p`要素の親要素は`html`なので`16px × 2em = 32px`となります。次に`span`要素の親要素が`p`なので`span`要素の文字サイズは`32px × 0.5em = 16px`となります。

    ```css
    html {
      font-size: 16px;
    }
    
    p {
      font-size: 2em;
    }
    
    span {
      font-size: 0.5em;
    }
    ```

3. rem（レム）で指定

    remで指定すると、`html`要素の`font-size`を基準に算出されます。以下のようなHTMLファイルがあるとします。

    ```html
    <!DOCTYPE html>
    <html lang="ja">
    <head>
      <meta charset="UTF-8" />
      <link rel="stylesheets" href="styles.css" />
      <title>Document</title>
    </head>
    <body>
      <h1>CSSハンズオン</h1>
      <p>ここの色を<span>緑色</span>にしてください。</p>
    </body>
    </html>
    ```

    CSSファイルで以下のように宣言すると、`p`要素は`16px × 2rem = 32px`となり、`span`要素は`16px × 0.5rem = 8px`となります。

    ```css
    html {
      font-size: 16px;
    }
    
    p {
      font-size: 2rem;
    }
    
    span {
      font-size: 0.5rem;
    }
    ```

4. 紹介した以外にも%（パーセンテージ）で指定する方法などもあるので、是非調べてみてください。指定方法によってどのような値になるのかを理解することが大切です。

## 文章の途中で文字のスタイルを変更する
文章の途中で文字のスタイルを変更する場合は、`span`タグを使用します。`span`タグは特に意味を持たないインライン要素なので、文章内で部分的にスタイルを適用させたい場合に使用されます。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8" />
  <link rel="stylesheets" href="styles.css" />
  <title>Document</title>
</head>
<body>
  <h1>CSSハンズオン</h1>
  <!-- 「緑色」の文字だけ個別にスタイルを適用させることができる -->
  <p>ここの色を<span>緑色</span>にしてください。</p>
</body>
</html>
```
```css
/* p要素の文字色を青色で表示 */
p {
  color: blue;
}

/* p要素内の「緑色」の文字だけ緑色で表示 */
span {
  color: green;
}
```

![image](https://github.com/user-attachments/assets/aab1ee8b-7831-46d7-aff5-257774df4511)

## CSSを書いてみよう
インプットした内容を基に、手を動かして試してみましょう。同じディレクトリにあるindex.htmlとstyles.cssに指示に従ってコードを書いてください。わからなければ回答例を見てもOKです。index.htmlをブラウザで表示して、ビフォーアフターも確認してみてください。

1. 前回の復習も兼ねて、まずはindex.htmlにstyles.cssを適用するコードを書いてください。
    <details>
    <summary>回答例</summary>

    ```html
    <!DOCTYPE html>
    <html lang="ja">
    <head>
      <meta charset="UTF-8" />
      <!-- ここにstyles.cssを適用するコードを記述 -->
      <link rel="stylesheet" href="styles.css" />
    
      <title>Document</title>
    </head>
    <body>
      <h1>CSSハンズオン</h1>
      <h3>Part2</h3>
      <!-- 「色」にのみCSSを適用するために編集 -->
      <p>ここの色を緑色にしてください。</p>
    </body>
    </html>
    ```
    </details>

2. `html`要素の文字サイズを24pxで宣言してください。
    <details>
    <summary>回答例</summary>

    ```css
    /* html要素の文字サイズを宣言 */
    html {
      font-size: 24px;
    }
    ```
    </details>

3. `h1`要素の文字色を白色、背景色を青色、文字サイズを24pxになるように「rem」を使用して宣言してください。
    <details>
    <summary>回答例</summary>

    ```css
    /* h1要素の文字色、背景色、文字サイズを宣言 */
    h1 {
      color: white;
      background-color: blue;
      font-size: 1rem;
    }
    ```
    </details>

4. `h3`要素の背景色を深緑（`rgb(0, 100, 0)`）、文字サイズを18pxになるように「rem」を使用して宣言してください。
    <details>
    <summary>回答例</summary>

    ```css
    /* h3要素の背景色、文字サイズを宣言 */
    h3 {
      background-color: rgb(0, 100, 0);
      font-size: 0.75rem;
    }
    ```
    </details>

5. `p`要素の文字色を群青（#000080）、文字サイズを12pxになるように「rem」を使用して宣言してください。
    <details>
    <summary>回答例</summary>

    ```css
    /* p要素の文字色、文字色、文字サイズを宣言 */
    p {
      color: #000080;
      font-size: 0.5rem;
    }
    ```
    </details>

6. `p`要素内の文章の「色」の文字のみ文字色を赤色にしてください。
    <details>
    <summary>回答例</summary>

    ```html
    <!DOCTYPE html>
    <html lang="ja">
    <head>
      <meta charset="UTF-8" />
      <!-- ここにstyles.cssを適用するコードを記述 -->
      <link rel="stylesheet" href="styles.css" />
    
      <title>Document</title>
    </head>
    <body>
      <h1>CSSハンズオン</h1>
      <h3>Part2</h3>
      <!-- 「色」にのみCSSを適用するために編集 -->
      <p>ここの<span>色</span>を緑色にしてください。</p>
    </body>
    </html>
    ```
    ```css
    /* 「色」の文字色を宣言 */
    span {
      color: red;
    }
    ```
    </details>

すべて記述できるとブラウザでは以下のように表示されます。うまく表示されない場合は、コードを良く見返して修正しましょう。

![image](https://github.com/user-attachments/assets/70dd3170-66b4-4f8f-ac6d-00d9e4ee0e3b)

## GitHubへプッシュしよう
編集した内容をステージング＆コミットし、自身のGitHubにあるリモートリポジトリにプッシュしましょう。以下のコマンドを実行します。

```bash
# すべてのファイルをステージング
git add .

# コミット（コミットメッセージは自由に記述してください）
git commit -m "Part2 色やサイズを変更してみよう"

# リモートリポジトリへプッシュ
git push origin main
```