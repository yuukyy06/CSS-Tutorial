Webサイトのボタンにある文字がすべて左寄りだと、ちょっといまいちですよね？上下左右に対し、中央に配置したくなると思います。今回はテキストの配置と太さのスタイルについて学んでいきます。

## テキストの配置
### 左右方向の配置

左右方向のテキストの配置を変更するには、`text-align`プロパティを使用します。デフォルトは左寄り（`left`）になっており、主に`left`、`center`、`right`で指定します。

以下のようなHTMLとCSSで試してみましょう。

```html
<div>
  <p>押してね!</p>
</div>
```
```css
p {
  background-color: brown;
  width: 120px;
  height: 40px;
}
```

![image](https://github.com/user-attachments/assets/35906695-91f7-4b61-98dd-64c4ac253687)

`text-align`プロパティで`center`を指定すると、中央に配置されます。

```css
p {
  background-color: brown;
  width: 120px;
  height: 40px;
  /* text-alignプロパティを追加 */
  text-align: center;
}
```

![image](https://github.com/user-attachments/assets/059dc80d-d7a0-4435-a690-d056a2b77881)

`right`を指定すると、右寄りに配置されます。

```css
p {
  background-color: brown;
  width: 120px;
  height: 40px;
  /* text-alignプロパティを追加 */
  text-align: right;
}
```

![image](https://github.com/user-attachments/assets/ffb2a1da-32a0-4b7c-8fbc-db25969fd8ce)

### 上下方向の配置
上下方向のテキストの配置を変更するのは、少し複雑かつ様々な方法があります。ここでは、テキストが1行で高さが決まっている場合に適用できる方法を紹介します。

上のHTMLとCSSで試してみましょう。親要素に`height`プロパティを指定し、子要素に`line-height`プロパティを指定します。

```css
div {
  height: 40px;
}

p {
  background-color: brown;
  width: 120px;
  text-align: center;
  /* line-heightプロパティを使用（heightプロパティの代わり） */
  line-height: 40px;
}
```

![image](https://github.com/user-attachments/assets/8c44e943-41b2-4a9e-83cb-e6e3027ab8e4)

`line-height`プロパティは行間を含む文字の高さを設定します。親要素で指定した`height`プロパティの値と同じ値で`line-height`プロパティを指定することで、`上下の行間＋文字の高さ＝親要素の高さ`になるため中央に配置することができます。行間を含んだ高さの指定のため、複数行の文章での使用には適しません。

## テキストの太さ
テキストの太さは`font-weight`プロパティを使用します。数字（100～900で100刻み）や英文字でも指定でき、`normal`は数字の400、`bold`は数字の700に相当します。

```css
div {
  height: 40px;
}

p {
  background-color: brown;
  width: 120px;
  text-align: center;
  line-height: 40px;
  /* font-weightを追加 */
  font-weight: 700;
}
```

![image](https://github.com/user-attachments/assets/67ab6325-1d92-48e6-a4d6-1245fe16b939)

100～900まで適用してみると、ある程度大きな文字でないと`normal`と`bold`の差しか認識できなさそうですね。

![image](https://github.com/user-attachments/assets/ffcac8c9-4fe6-415c-819a-039cbacb1a3c)

## CSSを書いてみよう
インプットした内容を基に、早速手を動かして試してみましょう。index.htmlを確認し、指示に従ってCSSを書いてください。まずは自身で書いてみて、わからなければ回答例を見てもOKです。index.htmlをブラウザで表示して、ビフォーアフターも確認してみてください。

index.html

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8" />
  <link rel="stylesheet" href="styles.css" />
  <title>Document</title>
</head>
<body>
  <h1>CSSハンズオン</h1>
  <h3>Part6</h3>
  <p>Python</p>
</body>
</html>
```

1. `h1`要素を文字サイズ32px、文字色を白色、背景色をmidnightblueにし、文字の横方向の配置を中央にしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* h1要素に適用するスタイル */
    h1 {
      font-size: 32px;
      color: white;
      background-color: midnightblue;
      text-align: center;
    }
    ```
    </details>

2. `h3`要素を文字色を白色、背景色をdeepskyblueにしてください。また高さを50pxで、文字が上下左右共に中央に配置されるようにスタイルを適用してください。ここでは、HTMLファイルの編集も必要になります。
    <details>
    <summary>回答例</summary>

    ```html
    <div>
      <h3>Part6</h3>
    </div>
    ```
    ```css
    /* h3要素に適用するスタイル */
    div {
      height: 50px;
    }
    
    h3 {
      color: white;
      background-color: deepskyblue;
      line-height: 50px;
      text-align: center;
    }
    ```
    </details>

3. `p`要素を文字色を白色、背景色を#3776AB、文字の横方向の配置を中央にしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* p要素に適用するスタイル */
    p {
      color: white;
      background-color: #3776AB;
      text-align: center;
    }
    ```
    </details>

すべて記述できるとブラウザでは以下のように表示されます。うまく表示されない場合は、コードを良く見返して修正しましょう。

![image](https://github.com/user-attachments/assets/8942ed04-bccc-4f6a-8d0a-96eb61b39b3d)

## GitHubへプッシュしよう
編集した内容をステージング＆コミットし、自身のGitHubにあるリモートリポジトリにプッシュしましょう。以下のコマンドを実行します。

```bash
# すべてのファイルをステージング
git add .

# コミット（コミットメッセージは自由に記述してください）
git commit -m "Part6 テキストの配置と太さを学ぼう"

# リモートリポジトリへプッシュ
git push origin main
```