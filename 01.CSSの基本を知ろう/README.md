## CSSとは

CSSはCascading Style Sheetsの略でHTMLがコンテンツの構造と意味を定義するのに対し、コンテンツにスタイルを与えたりレイアウトを決めるために使用されます。フォントや色、サイズ、余白など、Webサイトの「見た目」を装飾します。
HTMLだけでもWebサイトを作ることはできますが、同じフォントや色ばかりのサイトはつまらないですよね？CSSをうまく利用することで、表現力豊かなWebサイトにすることができます。

## CSSの書き方

### 基本構文
最初にスタイルをあてる対象のセレクターを宣言し、後ろに中括弧`{ }`を記述、その中に`プロパティ: 値;`という構文でスタイルを宣言します。

![image](https://github.com/user-attachments/assets/d40b5e7e-08fd-49fd-a8de-fe60cdc21480)

ここでは、`h1`タグで囲われた文字列に「`color`プロパティの値`black`」というスタイルを宣言しています。`color`プロパティは文字色を指定するために使用されます。CSSには非常に多くのプロパティがあるため、何が出来るのか？どれが何をするためのものか？を少しずつ理解していく必要があります。

### セレクターやプロパティをまとめて宣言
適用するスタイルやセレクターをまとめて宣言することも可能です。

```css
/* h1要素の文字色、文字サイズ、背景色をまとめて宣言 */
h1 {
  color: black;
  font-size: 32px;
  background-color: blue;
}

/* p要素とspan要素の文字色と背景色をまとめて宣言 */
p, span {
  color: red;
  background-color: yellow;
}

/* span要素の文字色と文字サイズをまとめて宣言 */
span {
  color: blue;
  font-size: 24px;
}
```

### 優先順位
CSSファイルでは後で書かれた宣言が優先されます。上記のように`span`要素の`color`プロパティが2回宣言されている場合、後で宣言されたものが先に宣言した内容を上書きするため、`color: blue;`が適用されます。

## HTMLにCSSを適用する
作成したHTMLファイルにCSSを適用するには、HTMLファイル内で適用するCSSファイルを指定する必要があります。`head`要素内に`link`タグを使用して宣言します。`rel`属性でCSSがあることを伝え、`href`属性で適用するCSSファイルのパスを指定します。HTMLファイルと同じディレクトリ内にある場合は、ファイル名のみでも大丈夫です。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <!-- styles.cssファイルをこのHTMLファイルに適用 -->
  <link rel="stylesheet" href="styles.css" />
  <title>CSS tutorial</title>
</head>
```

## CSSを書いてみよう
インプットした内容を基に、早速手を動かして試してみましょう。まずは自身で書いてみて、わからなければ回答例を見てもOKです。index.htmlをブラウザで表示して、ビフォーアフターも確認してみてください。

1. index.htmlで同じディレクトリにあるstyles.cssを適用するコードを書いてください。
    <details>
    <summary>回答例</summary>

    ```html
    <!DOCTYPE html>
    <html lang="ja">
    <head>
      <meta charset="UTF-8" />
      <!-- ここにstyles.cssを適用するコードを書いてください -->
      <link rel="stylesheet" href="styles.css" />
    
      <title>Document</title>
    </head>
    <body>
      <h1>CSSハンズオン</h1>
      <h3>Part1</h3>
      <p>ここの色を緑色にしてください。</p>
    </body>
    </html>
    ```
    </details>

2. 同じディレクトリにあるstyles.cssで、`h1`要素の文字色を青色で指定してください。
    <details>
    <summary>回答例</summary>

    ```css
    /* h1要素の文字色を青色で宣言 */
    h1 {
      color: blue;
    }
    ```
    </details>

3. 次に、`p`要素の文字色を緑色で指定してください。
    <details>
    <summary>回答例</summary>

    ```css
    /* p要素の文字色を緑色で宣言 */
    p {
      color: green;
    }
    ```
    </details>

すべて記述できるとブラウザでは以下のように表示されます。うまく表示されない場合は、コードを良く見返して修正しましょう。

![image (1)](https://github.com/user-attachments/assets/49fb2f09-a842-42c2-8c48-3f0168598c2d)

## GitHubへプッシュしよう
編集した内容をステージング＆コミットし、自身のGitHubにあるリモートリポジトリにプッシュしましょう。以下のコマンドを実行します。

```bash
# すべてのファイルをステージング
git add .

# コミット（コミットメッセージは自由に記述してください）
git commit -m "Part1 CSSの基本を知ろう"

# リモートリポジトリへプッシュ
git push origin main
```