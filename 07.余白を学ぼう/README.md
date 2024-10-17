余白を学ぶことで要素同士の間隔や、要素の境界を設定できるようになります。余白や境界を設定するプロパティは主に`margin`、`border`、`padding`の3つがあり、それぞれが指すエリアは以下の通りです。

![image](https://github.com/user-attachments/assets/8424b152-fc05-45aa-a46c-c0c298f6307a)

## border
`border`プロパティは要素の境界を設定します。要素を四角で囲うとイメージがしやすくなるので以下の例を見てみましょう。

```html
<p>Python</p>
<p>JavaScript</p>
```

```css
p {
  display: inline-block;
  width: 100px;
  background-color: #3776AB;
  color: white;
  text-align: center;
}
```

![image](https://github.com/user-attachments/assets/f1fdd6ea-b3e3-4439-927e-7f39a01c42b1)

2つの`p`要素に`border`プロパティを追加してみます。

```css
p {
  display: inline-block;
  width: 100px;
  background-color: #3776AB;
  color: white;
  text-align: center;
  /* borderプロパティを追加 */
  border: red 2px solid;
}
```

![image](https://github.com/user-attachments/assets/75f144dd-a536-4b8c-9957-32603693990f)

今は`padding`プロパティを指定していないため、要素エリアのすぐ外側に2pxの`border`エリアが表示されました。

値には、色、線の太さ、線の種類を指定しますが、値の順番には決まりが無いため、`border: solid red 2px;`でも同じスタイルになります。線の種類は、今回は実線（`solid`）としていますが、他にも点線（`dotted`）や破線（`dashed`）などがあります。

![image](https://github.com/user-attachments/assets/802c5c05-ff20-41aa-88f8-4604cf422457)

![image](https://github.com/user-attachments/assets/7f2593c4-7b43-48fc-a2de-97feee97057d)

## padding
`padding`プロパティは要素と`border`エリアの間になります。先ほどの例に`padding`プロパティを追加してみましょう。

```css
p {
  display: inline-block;
  width: 100px;
  background-color: #3776AB;
  color: white;
  text-align: center;
  border: red 2px solid;
  /* paddingプロパティを追加 */
  padding: 10px;
}
```

![image](https://github.com/user-attachments/assets/fa384885-ad82-4e9c-b312-df3f7aa607cf)

要素のエリアが大きくなったようにも見えますが、要素自体のサイズはそのままで`padding`エリアが10px広がりました。上下方向も中央配置になっており、前回学んだ方法よりもシンプルに配置できましたね。これは、`height`プロパティを指定しない場合、基本的にはデフォルトで文字のサイズに合った高さが設定されるため、上下方向の`padding`プロパティを同じ値で設定するだけで上下方向の配置を中央にすることができるためです。

## margin
`margin`プロパティは`border`エリアの外側のエリアになります。先ほどの例に`margin`プロパティを追加してみましょう。

```css
p {
  display: inline-block;
  width: 100px;
  background-color: #3776AB;
  color: white;
  text-align: center;
  border: red 2px solid;
  padding: 10px;
  /* marginプロパティを追加 */
  margin: 50px;
}
```

![image](https://github.com/user-attachments/assets/a9fba72f-b013-4da7-96db-d2175843a6a7)

要素間の間隔や画面内での位置が変わりましたね。これは各`p`要素に`margin`プロパティが設定されたためです。

## 上下左右のそれぞれへの指定
紹介した3つのうち`padding`と`margin`プロパティでは、上下左右それぞれに個別に値を設定することができます。設定方法は以下の通りです。

- 値が1つ：上下左右すべてに指定した値を適用（`padding: 10px;`）
- スペース区切りで値が2つ：前側の値が上下に、後側の値が左右に適用（`padding: 5px 1px;`）
- スペース区切りで値が3つ：前側の値が上に、中央の値が左右に、後側の値が下に適用（`padding: 5px 1px 5px;`）
- スペース区切りで値が4つ：前の値から上、右、下、左に適用（`padding: 1px 5px 1px 5px;`）

また、それぞれを指定するためのプロパティも存在します。

- `padding-top`、`margin-top`：上
- `padding-right`、`margin-right`：右
- `padding-bottom`、`margin-bottom`：下
- `padding-left`、`margin-left`：左

`border`プロパティは3種類の値が存在するため、それぞれ個別に指定するためのプロパティを使用することで、`padding`プロパティや`margin`プロパティと同様に上下左右を個別に指定することができます。

- 色：`border-color`
- 線の太さ：`border-width`
- 線の種類：`border-style`

そして、こちらにも各プロパティに`-top`や`-right`を追加したプロパティ（`border-top-color`や`border-right-style`）が存在するため、それぞれを単体で指定することが可能です。

## outline
`outline`プロパティも`border`プロパティのような「枠線」を追加することができます。値の指定方法は同じですが、`border`プロパティのように上下左右のそれぞれに別のスタイルを適用することはできません。また、`border`プロパティは指定した線の太さに合わせて`border`エリアが広がるため、「要素＋padding＋border＋margin」のサイズが変わりますが、`outline`プロパティは枠線を表示するだけなので、指定した線の太さが変わっても「要素＋padding＋border＋margin」のサイズは変わりません。

```html
<div class="box">
  <div class="border"></div>
  <p>Python</p>
</div>
<div class="box">
  <div class="outline"></div>
  <p>JavaScript</p>
</div>
```
```css
p {
	margin: 0 0 20px 0;
	text-align: center;
}

.box {
	display: inline-block;
	margin: 20px;
	background-color: aqua;
}

.border, .outline {
	display: inline-block;
	width: 100px;
	padding: 20px 0;
	background-color: #3776AB;
}

/* borderクラスにborderプロパティで枠線を追加 */
.border {
  border: red 5px solid;
}

/* outlineクラスにoutlineプロパティで枠線を追加 */
.outline {
  outline: red 5px solid;
}
```

![image](https://github.com/user-attachments/assets/a4575630-f2a0-4848-8fb3-34b626b3cc76)

この例では、枠線のスタイル以外は全く同じですが、`border`プロパティで指定したPython側は水色のエリア内に枠線が入っています。これは`border`クラスのエリアが広がったため`box`クラスのエリアもそれに伴って広がっているためです。しかし、`outline`プロパティで指定したJavaScript側は、枠線が水色のエリアの外に配置されています。`outline`プロパティでは、どのエリアにも影響を及ぼさずに枠線を表示できるため、後に出てくるホバーやフォーカスなどの疑似クラスを使用する時に、スタイルを崩さずに枠線を表示することができます。

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
  <h3>Part7</h3>
  <p>ダッシュボード</p>
  <p>講義動画</p>
  <p>講義日程</p>
  <p>ステップ一覧</p>
  <p>ハッカソン</p>
</body>
</html>
```

1. すべての`p`要素をサイズを変更できるインラインブロックにしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* p要素に適用するスタイル */
    p {
      display: inline-block;
    }
    ```
    </details>

2. すべての`p`要素の背景色を`#00008B`、文字色を白色にしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* p要素に適用するスタイル */
    p {
      display: inline-block;
      background-color: #00008B;
      color: white;
    }
    ```
    </details>

3. すべての`p`要素の幅を160pxにし、各要素の文字が左右方向で中央になるようにしてください。

    ![image](https://github.com/user-attachments/assets/f66648be-c067-4eff-97f3-28c43af62e1e)

    <details>
    <summary>回答例</summary>

    ```css
    /* p要素に適用するスタイル */
    p {
      display: inline-block;
      background-color: #00008B;
      color: white;
      width: 160px;
      text-align: center;
    }
    ```
    </details>

4. すべての`p`要素に`padding`を上下にのみ10pxずつ追加してください。
    <details>
    <summary>回答例</summary>

    ```css
    /* p要素に適用するスタイル */
    p {
      display: inline-block;
      background-color: #00008B;
      color: white;
      width: 160px;
      text-align: center;
      padding: 10px 0;
    }
    ```
    </details>

5. すべての`p`要素に`margin`を右にだけ20px追加してください。
    <details>
    <summary>回答例</summary>

    ```css
    /* p要素に適用するスタイル */
    p {
      display: inline-block;
      background-color: #00008B;
      color: white;
      width: 160px;
      text-align: center;
      padding: 10px 0;
      margin-right: 20px;
    }
    ```
    </details>

6. すべての`p`要素に以下の内容で`border`を適用してください。
    
    |  | 色 | 線の太さ | 線の種類 |
    | --- | --- | --- | --- |
    | 上 | 黄色 | 5px | 点線 |
    | 右 | 黄色 | 10px | `ridge` |
    | 下 | 赤色 | 10px | `ridge` |
    | 左 | 黄色 | 5px | 実線 |

    <details>
    <summary>回答例</summary>

    ```css
    /* p要素に適用するスタイル */
    p {
      display: inline-block;
      background-color: #00008B;
      color: white;
      width: 160px;
      text-align: center;
      padding: 10px 0;
      margin-right: 20px;
      border-style: dotted ridge solid;
      border-color: yellow yellow red;
      border-width: 5px 10px;
    }
    ```
    </details>

すべて記述できるとブラウザでは以下のように表示されます。うまく表示されない場合は、コードを良く見返して修正しましょう。

![image](https://github.com/user-attachments/assets/4b34b86c-f56c-4b0c-b44e-ea666cde425d)

## GitHubへプッシュしよう
編集した内容をステージング＆コミットし、自身のGitHubにあるリモートリポジトリにプッシュしましょう。以下のコマンドを実行します。

```bash
# すべてのファイルをステージング
git add .

# コミット（コミットメッセージは自由に記述してください）
git commit -m "Part7 余白を学ぼう"

# リモートリポジトリへプッシュ
git push origin main
```