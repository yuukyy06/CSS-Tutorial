要素の並びやサイズを調整するのもCSSの役割です。並べ方や表示するサイズによってWebサイトの見た目は大きく変わってくるので、ここもしっかり学んでいきましょう！

## displayプロパティ
displayプロパティは要素をブロックボックス、インラインボックスのどちらとして扱うか、また子要素のレイアウトなどを設定するために使用します。レイアウトに関しては後のステップで学習するので、ここではブロックボックスやインラインボックスについて学んでいきましょう。

## ブロックボックスとインラインボックス
HTMLで記述された各要素は、タグの種類によってブロックボックスとインラインボックスに分類されており、それぞれに以下のような特徴があります。

- ブロックボックス（ブロック要素）
    - 改行され、要素が縦方向に並んで表示されます。

        ![image](https://github.com/user-attachments/assets/f5dd5a88-f988-4739-b7c5-c41623d4ce6b)

    - 高さや幅が指定できます。
    - 多くのタグはデフォルトでブロックボックスです。
- インラインボックス（インライン要素）
    - 改行されず、要素が横方向に並んで表示されます。

        ![image](https://github.com/user-attachments/assets/1f68a1dd-69f3-43dc-8190-7e87896b5dc4)

    - 高さや幅の指定はできません。
    - `a`タグや`span`タグなどはデフォルトでインラインボックスです。

## displayプロパティの値
displayプロパティには設定できる値が多くありますが、ここでは3つを紹介します。

- `block`

    指定した要素をブロックボックスにします。デフォルトがインラインボックスの要素をブロックボックスにしたい時に使用します。

- `inline`

    指定した要素をインラインボックスにします。デフォルトがブロックボックスの要素をインラインボックスにしたい時に使用します。

- `inline-block`

    インラインボックスのように、改行はされずに横方向に並んで表示されますが、高さや幅を指定することができます。

## 幅や高さの設定
幅（横方向）は`width`プロパティ、高さ（縦方向）は`height`プロパティを使用します。値はpxやemなどで指定できます。

```html
<p class="hundred">幅100px、高さ100px</p>
<p class="two-hundreds">幅200px、高さ200px</p>
```

```css
p {
  color: white;
}

.hundred {
  width: 100px;
  height: 100px;
  background-color: green;
}

.two-hundreds {
  width: 200px;
  height: 200px;
  background-color: blue;
}
```

![image](https://github.com/user-attachments/assets/ff376c16-abc1-4c8c-a576-081bc6a2af23)

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
  <h3>Part5</h3>
  <p class="today">今日の天気</p>
  <p class="weather">晴れ</p>
  <p class="temperature">32℃</p>
  <p class="humidity">58%</p>
  <img src="images/weather.png" alt="sunny" />
</body>
</html>
```

1. class属性`today`の文字サイズを20pxにしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* todayクラスに適用するスタイル */
    .today {
      font-size: 20px;
    }
    ```
    </details>

2. class属性`today`の文章にある「天気」のみ背景色を`#FFC0CB`にしてください。
    <details>
    <summary>回答例</summary>

    ```html
    <p class="today">今日の<span>天気</span></p>
    ```
    
    ```css
    span {
      background-color: #FFC0CB;
    }
    ```
    </details>

3. class属性`today`の文章にある「天気」のみ高さを28pxにしてください。高さを変更するために`height`プロパティ以外にも指定すべきスタイルがあることに注意してください。
    <details>
    <summary>回答例</summary>

    ```css
    span {
      background-color: #FFC0CB;
      display: inline-block;
      height: 28px;
    }
    ```
    </details>

4. class属性`temperature`と`humidity`の背景色を以下の色にしてください。

    `temperature`：#FFD8B2
    
    `humidity`：#ADD8E6

    <details>
    <summary>回答例</summary>

    ```css
    /* temperatureクラスに適用するスタイル */
    .temperature {
      background-color: #FFD8B2;
    }
    
    /* humidityクラスに適用するスタイル */
    .humidity {
      background-color: #ADD8E6;
    }
    ```
    </details>

5. class属性`temperature`と`humidity`を`display`プロパティを使用して横に並ぶようにし、幅を40px、高さを20pxにしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* temperatureクラスに適用するスタイル */
    .temperature {
      background-color: #FFD8B2;
      display: inline-block;
      width: 40px;
      height: 20px;
    }
    
    /* humidityクラスに適用するスタイル */
    .humidity {
      background-color: #ADD8E6;
      display: inline-block;
      width: 40px;
      height: 20px;
    }
    ```
    </details>

6. `img`要素を`display`プロパティを使用して気温と湿度の下に表示されるようにしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* img要素に適用するスタイル */
    img {
      display: block;
    }
    ```
    </details>

すべて記述できるとブラウザでは以下のように表示されます。うまく表示されない場合は、コードを良く見返して修正しましょう。

![image](https://github.com/user-attachments/assets/161798ce-7d8a-40ee-8e86-48765ae029a3)

## GitHubへプッシュしよう
編集した内容をステージング＆コミットし、自身のGitHubにあるリモートリポジトリにプッシュしましょう。以下のコマンドを実行します。

```bash
# すべてのファイルをステージング
git add .

# コミット（コミットメッセージは自由に記述してください）
git commit -m "Part5 要素の並びやサイズを設定しよう"

# リモートリポジトリへプッシュ
git push origin main
```