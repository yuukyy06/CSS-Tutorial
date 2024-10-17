角を丸めることでやさしい雰囲気にしたり、影を追加することで立体的に見えたりと、Webサイトの印象を変えることができます。

## 角を丸めてみよう
`border-radius`プロパティを使うことで、要素の角を丸めることができます。どのようにスタイルを宣言するのか見ていきましょう。

```html
<h3>Part8</h3>
```
```css
h3 {
  display: inline-block;
  background-color: #00008B;
  color: white;
  width: 160px;
  text-align: center;
  padding: 10px 0;
  margin-right: 20px;
}
```

![image](https://github.com/user-attachments/assets/62089f47-0076-4fb3-81fa-424c1a3e227d)

`border-radius`プロパティの値はpxで円の半径を指定したり、%で`width`や`height`に対する割合を指定するなどの方法があります。この`h3`要素は幅160px、高さは28pxですが上下に`padding`が適用されているため、背景色のエリアの高さは48pxになります。左右を完全に半円にした場合は、高さの半分の24pxで指定すればOKです。

```css
h3 {
  display: inline-block;
  background-color: #00008B;
  color: white;
  width: 160px;
  text-align: center;
  padding: 10px 0;
  margin-right: 20px;
  /* border-radiusプロパティの追加 */
  border-radius: 24px;
}
```

![image](https://github.com/user-attachments/assets/c8ec904d-bd43-42c2-a069-c21e0b390d53)

幅と高さが同じ場合、`border-radius`プロパティで50%を指定すると、きれいな円にすることができます。

```css
h3 {
  display: inline-block;
  background-color: #00008B;
  color: white;
  width: 160px;
  text-align: center;
  /* 高さが160pxになるようにpaddingプロパティを適用 */
  padding: 66px 0;
  margin-right: 20px;
  /* border-radiusプロパティを50%で宣言 */
  border-radius: 50%;
}
```

![image](https://github.com/user-attachments/assets/807a1487-970f-481d-9911-1e9fb1ec5f0f)

幅と高さが違う場合に50%で指定すると、それぞれのサイズの半分から丸め始めるため、真円ではなく楕円で丸める形になります。

```css
h3 {
  display: inline-block;
  background-color: #00008B;
  color: white;
  width: 160px;
  text-align: center;
  padding: 10px 0;
  margin-right: 20px;
  /* border-radiusプロパティの追加 */
  border-radius: 50px;
}
```

![image](https://github.com/user-attachments/assets/ad11a2ea-6fae-4e6c-8ed7-42f82490da63)

横方向と縦方向の半径の値を個別に指定することで、より細かく楕円のサイズを指定することもできます。書き方は`/`をはさんで左側が横方向の半径、右側が縦方向の半径になります。（`border-radius: 20px / 10px;`）

```css
h3 {
  display: inline-block;
  background-color: #00008B;
  color: white;
  width: 160px;
  text-align: center;
  padding: 10px 0;
  margin-right: 20px;
  border-radius: 20px / 10px;
}
```

![image](https://github.com/user-attachments/assets/8b9ce78a-99d5-46c5-bfbe-facf683d75a7)

また各角を指定することもでき、`padding`や`margin`プロパティと同様に値の数を1～4つで指定します。`/`の左側と右側にも同様に1～4つずつ指定することができます。

- 値が1つ：すべてに指定した値を適用（`border-radius: 10px;`）
- スペース区切りで値が2つ：前側の値が左上・右下に、後側の値が右上・左下に適用（`border-radius: 5px 1px;`）
- スペース区切りで値が3つ：前側の値が左上に、中央の値が右上・左下に、後側の値が右下に適用（`border-radius: 5px 1px 5px;`）
- スペース区切りで値が4つ：前の値から左上、右上、右下、左下に適用（`border-radius: 1px 5px 1px 5px;`）

また、それぞれを指定するためのプロパティも存在します。

- `border-top-left-radius`：左上
- `border-top-right-radius`：右上
- `border-bottom-right-radius`：右下
- `border-bottom-left-radius`：左下

## 影を追加してみよう
`box-shadow`プロパティを使うことで影を追加することができます。指定の方法が少し複雑なので詳しく説明していきます。

指定できる値は、横方向のずれ・縦方向のずれ・ぼかしの強度・影のサイズ・影の色・内側への影の6種類です。横と縦の値以外は任意で、指定してもしなくてもOKです。

### 横方向と縦方向のずれ（`offset-x`、`offset-y`）
正の値で指定した場合は横方向は右側、縦方向は下側に、負の値で指定した場合は横方向は左側、縦方向は上側に影はずれます。（`box-shadow: 5px 5px;`、`box-shadow: -5px -5px;`）

![image](https://github.com/user-attachments/assets/34d49cc6-bc79-470b-ab50-7a4c6dce7f66)

### ぼかしの強度（`blur-radius`）
ぼかしの強度を指定することで、影自体をぼかすことができます。数字が大きいほどぼかしは強くなります。（`box-shadow: 10px 10px 5px;`）

![image](https://github.com/user-attachments/assets/86ea4130-7ced-4f71-8713-bd9d163b2caa)

### 影のサイズ（`spread-radius`）
デフォルトでは影のサイズは要素のサイズとなりますが、要素のサイズ±影のサイズを指定することで影自体のサイズを変更することができます。ただし、影のサイズを指定する際はぼかしの強度の指定も必須になるため、ぼかしが不要な場合でも`0`を指定する必要があります。（`box-shadow: 10px 10px 0 10px;`）

![image](https://github.com/user-attachments/assets/43f7fc21-6393-4062-a854-4443ac4d2b09)

### 影の色
`color`プロパティなどと同様の値で指定することができます。（`box-shadow: 10px 10px red;`）

![image](https://github.com/user-attachments/assets/8c733196-5af7-413e-a213-444837a89eee)

### 内側への影
値に`inset`と宣言すると、影が内側に投影されます。この時、影が出来る位置に注意してください。内側へ投影する場合は、正の値で上と左、負の値で下と右になります。（`box-shadow: 10px 10px red inset;`）

![image](https://github.com/user-attachments/assets/2971d250-a835-4965-beb0-5bc0179a2f37)

### 複数の影を追加
上で紹介した最大6種類の値で1つの影とし、カンマ（`,`）で区切ることで1つの要素に複数の影を追加することができます。（`box-shadow: 10px 10px 5px red inset, 10px 10px 5px green;`）

![image](https://github.com/user-attachments/assets/097ab173-a569-4833-8290-2cbea63f9ed8)

## 要素のはみだしを調整しよう
表示したいサイズに対して要素の内容が大きすぎる時があります。その場合、はみでる部分をどうするか、CSSで指定することができます。次のようなHTMLとCSSがあるとします。`p`要素は指定したサイズで固定しなければなりません。

```html
<p>
  aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa<br />
  aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
</p>
```
```css
p {
  background-color: red;
  width: 100px;
  height: 30px;
}
```

![image](https://github.com/user-attachments/assets/7a89fbea-8769-421d-8ac8-0fa8d02625ad)

しかし`p`要素の文字数が多く、指定した範囲からはみだしてしまいます。このような時は、`overflow`プロパティを使用してはみだした部分に対してスタイルを適用できます。

- `visible`：はみだした部分をそのまま表示します。（デフォルト）
- `hidden`：はみ出した部分を非表示にします。
- `clip`：`hidden`同様はみ出した部分を非表示にします。
    
    他のスタイルとの兼ね合いで`hidden`とは異なる動作をしますが、複雑なためここでの説明は割愛します。
    
- `scroll`：スクロールバーを使用してはみ出た部分を表示することができます。
    
    はみ出ていなくても、スクロールバーが表示されます。また、指定した範囲内にスクロールバーも入ることに注意してください。
    
- `auto`：はみ出ている場合はスクロールバーを表示して、はみ出ていない場合はスクロールバーは表示されません。

![image](https://github.com/user-attachments/assets/7d27f1ff-5379-47d3-ae6b-4c163777e5c8)

上から`hidden`、`scroll`、`auto`を適用しています。`overflow`プロパティはそのままで`p`要素のサイズを変更してみましょう。現在は幅100px・高さ30pxなので、これを幅300px・高さ100pxにすると、`auto`を指定した場合ははみ出さなくなった縦方向のスクロールバーが消えました。

![image](https://github.com/user-attachments/assets/04e7623d-1260-436f-a5c8-380433081492)

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
  <header>
    <h1>CSSハンズオン</h1>
    <h3>Part8</h3>
  </header>
  <div>
    <nav>
      <ul>
        <li>001 RareTECHで学ぶ上での心構え</li>
        <li>002 Mattermostを使いこなそう</li>
        <li>003 試しに過去の講義を見てみよう</li>
        <li>004 RareTECHのコンテンツを使いこなそう</li>
        <li>005 ホームポジションを覚えよう</li>
      </ul>
    </nav>
    <main>
      <h3>001 RareTECHで学ぶ上での心構え</h3>
      <p>
        これより皆様は、RareTECH講師陣が用意した500ステップというカリキュラムを実施して頂きます。
        500ステップは、RareTECHの使い方から、技術的な内容まで様々な内容を網羅しています。<br />
        難易度は、簡単なものからエンジニア歴10年の人でも理解してないような高難易度なものまであります。
        毎日、少しずつカリキュラムをこなした上で、リアルタイム講義に参加することで総合的な知識を身につけます。
        <br />おすすめのペースは、1日1~3ステップです。
      </p>
    </main>
  </div>
</body>
</html>
```

1. すべての`li`要素に色`#192F60`、太さ1px、実線の境界線を追加し、半径8pxですべての角を丸めてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* li要素にスタイルを適用 */
    li {
      border: #192F60 1px solid;
      border-radius: 8px;
    }
    ```
    </details>

2. `header`要素の上部2ヶ所の角を半径20pxで丸めてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* header要素にスタイルを適用 */
    header {
      border-radius: 20px 20px 0 0;
    }
    ```
    </details>

3. `div`要素の下部2ヶ所の角を半径20pxで丸めてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* div要素にスタイルを適用 */
    div {
      border-radius: 0 0 20px 20px;
    }
    ```
    </details>

4. `main`要素にある`p`要素の中身がはみ出てしまっていますね。スクロールバーを追加して全文を読めるようにしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* main要素内にスタイルを適用 */
    main {
      overflow: auto;
    }
    ```
    </details>

すべて記述できるとブラウザでは以下のように表示されます。うまく表示されない場合は、コードを良く見返して修正しましょう。

![image](https://github.com/user-attachments/assets/1a6baa78-02ad-49b9-aba1-b86e32da3e7a)

## GitHubへプッシュしよう
編集した内容をステージング＆コミットし、自身のGitHubにあるリモートリポジトリにプッシュしましょう。以下のコマンドを実行します。

```bash
# すべてのファイルをステージング
git add .

# コミット（コミットメッセージは自由に記述してください）
git commit -m "Part8 角を丸めたり影を追加してみよう"

# リモートリポジトリへプッシュ
git push origin main
```