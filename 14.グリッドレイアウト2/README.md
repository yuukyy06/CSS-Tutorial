前回は、コンテナにプロパティを宣言してトラックのサイズや配置、アイテムをコンテナやトラックに対してどこに配置するかなどを学びました。今回は、トラックに対してアイテムを配置する方法を学びます。

## グリッド線
トラックを仕切る線を「グリッド線」と呼びます。このグリッド線には番号がふられており、縦線は左から1・2・3・・・、横線は上から1・2・3・・・となっています。また、それぞれ負の値でも表すことができ、この場合は縦線は右から-1・-2・-3・・・、横線は下から-1・-2・-3・・・となっています。

![image](https://github.com/user-attachments/assets/af87b55d-4749-4067-a23f-187da1069e5b)

## アイテムの配置
アイテムに以下のプロパティを宣言することで、1つもしくは複数のトラックにアイテムを配置することができます。

【使用する主なプロパティ】
- `grid-row`：横線の番号を指定してアイテムを配置
- `grid-column`：縦線を指定してアイテムを配置

各プロパティについて、以下のコードを使って解説していきます。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <link rel="stylesheet" href="styles.css">
  <title>Document</title>
</head>
<body>
  <div class="container">
    <div class="item1">div1</div>
    <div class="item2">div2</div>
    <div class="item3">div3</div>
    <div class="item4">div4</div>
    <div class="item5">div5</div>
    <div class="item6">div6</div>
  </div>
</body>
</html>
```
```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px 100px;
  grid-template-rows: 100px 100px 100px;
}

div > div {
  outline: 1px black solid;
}
```

コンテナとなる`div`要素に100px×100pxの9つのトラックを定義し、わかりやすいように、item〇クラスの`div`要素に枠線を指定しています。9つのトラックを定義していますが、アイテムは6つなので、下段3つのトラックにはアイテムが配置されていない状態です。ブラウザで開くと以下のように表示されます。

![image](https://github.com/user-attachments/assets/c8840de7-fe60-426a-a16a-7902836c2301)

## grid-row
横線の番号を指定してアイテムを配置します。

### 1つの数値だけを指定

指定した番号の横線の下にあるトラックに配置されます。

```css
.item1 {
  grid-row: 2;
}
```

![image](https://github.com/user-attachments/assets/bac2351a-ba68-41dc-8ef3-ddeb63a47af2)

item1クラスの`div`要素が、横線2の下に配置されました。item1クラスがいなくなった場所を埋めるように、他の`div`要素が順に詰まっているのがわかります。

### 2つの数値を指定
2つの数値を指定した場合は、開始する横線と終了する横線の指定となります。ここでは、2つの数値は /（スラッシュ）で区切ることに注意が必要です。

```css
.item1 {
  grid-row: 1 / 4;
}
```

![image](https://github.com/user-attachments/assets/d8155a83-5bbd-44a8-9667-0d234c3a38d4)

item1クラスの`div`要素が、横線1の下から始まり横線4までの位置に配置されました。

### spanを使って指定
spanと数値をスペース区切りで指定することで、現在の位置からいくつトラックを使用するかを指定できます。

```css
.item1 {
  grid-row: 1 / 4;
}

.item2 {
  grid-row: span 2;
}
```

![image](https://github.com/user-attachments/assets/d840dda2-89c0-4a4d-a4da-c5867e99b514)

item2クラスの`div`要素が、縦方向に2つのトラックを使用して配置されました。  
また、開始位置の指定とspanを使ってトラック使用数をまとめて指定することもできます。

```css
.item1 {
  grid-row: 1 / 4;
}

.item2 {
  grid-row: 2 / span 2;
}
```

![image](https://github.com/user-attachments/assets/c21c27cd-312f-4ee1-b78d-7bf5498bebdb)

## grid-column
縦線の番号を指定してアイテムを配置します。指定方法は`grid-row`プロパティと同じです。

### 1つの数値だけを指定
指定した番号の縦線の右にあるトラックに配置されます。

```css
.item1 {
  grid-column: 2;
}
```

![image](https://github.com/user-attachments/assets/8b747513-6cb3-4816-97f2-7497f17b4cde)

item1クラスの`div`要素が、縦線2の右に配置されました。item1クラスがいなくなった場所は、他の要素に埋められることなく空になりました。

### 2つの数値を指定
2つの数値を指定した場合は、開始する縦線と終了する縦線の指定となります。ここでは、2つの数値は /（スラッシュ）で区切ることに注意が必要です。

```css
.item1 {
  grid-column: 1 / 4;
}
```

![image](https://github.com/user-attachments/assets/c997717a-7885-4eb2-94ef-86921f424c81)

item1クラスの`div`要素が、縦線1の右から始まり縦線4までの位置に配置されました。

### spanを使って指定
spanと数値をスペース区切りで指定することで、現在の位置からいくつトラックを使用するかを指定できます。

```css
.item1 {
  grid-column: 1 / 4;
}

.item2 {
  grid-column: span 2;
}
```

![image](https://github.com/user-attachments/assets/f9757bde-149a-4c8d-ad93-43429f5e0d5a)

item2クラスの`div`要素が、横方向に2つのトラックを使用して配置されました。  
こちらも`grid-row`プロパティと同様に、開始位置の指定とspanを使ってトラック使用数をまとめて指定することもできます。

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
  <div class="container">
    <div class="item1">div1</div>
    <div class="item2">div2</div>
    <div class="item3">div3</div>
    <div class="item4">div4</div>
    <div class="item5">div5</div>
    <div class="item6">div6</div>
  </div>
</body>
</html>
```

1. containerクラスの`div`要素にグリッドレイアウトで、100px×100pxのトラックを4行×3列定義してください。
    <details>
    <summary>回答例</summary>

    ```css
    /* containerクラスのdiv要素にスタイルを適用 */
    .container {
      display: grid;
      grid-template-rows: 100px 100px 100px 100px;
      grid-template-columns: 100px 100px 100px;
    }
    ```
    </details>

2. アイテムを以下の配置になるよう、必要なitem〇クラスにスタイルを適用してください。

    ![image](https://github.com/user-attachments/assets/9c82c1da-3f92-479e-9c5e-ad0959746c14)

    <details>
    <summary>回答例</summary>

    ```css
    /* item〇クラスにスタイルを適用 */
    .item2 {
      grid-row: span 2;
    }
    
    .item3 {
      grid-column: 1;
      grid-row: 3 / span 2;
    }
    
    .item4 {
      grid-column: 3;
    }
    
    .item5 {
      grid-column: 3;
    }
    
    .item6 {
      grid-row: span 2;
      grid-column: span 2;
    }
    ```
    </details>

うまく表示されない場合は、コードを良く見返して修正しましょう。

## GitHubへプッシュしよう
編集した内容をステージング＆コミットし、自身のGitHubにあるリモートリポジトリにプッシュしましょう。以下のコマンドを実行します。

```bash
# すべてのファイルをステージング
git add .

# コミット（コミットメッセージは自由に記述してください）
git commit -m "Par14 グリッドレイアウト2"

# リモートリポジトリへプッシュ
git push origin main
```