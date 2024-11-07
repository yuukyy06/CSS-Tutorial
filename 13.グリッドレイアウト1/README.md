## グリッドレイアウトとは？
フレックスボックスは、横方向もしくは縦方向の1次元に配置する方法でしたが、グリッドレイアウトは、要素を**2次元**に配置する方法です。グリッドレイアウトを使用することで、フレックスボックスよりも複雑なレイアウトができるようになります。

## グリッドレイアウトの用語
### コンテナ
フレックスボックスでも出てきましたが、レイアウトを適用する要素の親要素を「コンテナ」と呼びます。このコンテナに要素のレイアウトを指定します。

### アイテム
スタイルを適用する要素自身を「アイテム」と呼びます。

### トラック
要素を配置するエリアを「トラック」と呼びます。アイテムは1つのトラック内に配置することも、2つ以上のトラックにまたがって配置することも可能です。

グリッドレイアウトでは、図のようにコンテナ内を格子状に分割します。その分割されたエリアがトラックです。

![Group 1](https://github.com/user-attachments/assets/5707a93f-f755-40ac-a8a8-982e9307ab5d)

このトラックにアイテムを配置します。

![Group 2](https://github.com/user-attachments/assets/7c1dd41a-cc3c-4b58-9727-69aa06a336ea)

## グリッドレイアウトの指定
コンテナに以下のプロパティを指定することで、トラックのサイズや数を指定したり、アイテムの配置を指定できます。

【使用する主なプロパティ】

- `display`：gridを指定することでグリッドレイアウトを適用（`display: grid;`）
- `grid-template-rows`：縦方向（垂直方向）にトラックを並べる数とサイズを指定
- `grid-template-columns`：横方向（水平方向）にトラックを並べる数とサイズを指定
- `justify-content`：コンテナ内の横方向のどの位置にアイテムを配置するかを指定
- `justify-items`：トラック内の横方向のどの位置にアイテムを配置するかを指定
- `align-content`：コンテナ内の縦方向のどの位置にアイテムを配置するかを指定
- `align-items`：トラック内の縦方向のどの位置にアイテムを配置するかを指定
- `gap`：アイテム同士の隙間（余白）を指定

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
    <div>div1</div>
    <div>div2</div>
    <div>div3</div>
    <div>div4</div>
    <div>div5</div>
    <div>div6</div>
  </div>
</body>
</html>
```
```css
.container {
  display: grid;
  height: 600px;
}

div div {
  outline: 1px black solid;
}
```

コンテナとなる`div`要素に`display: grid;`と高さを指定し、わかりやすいように、itemクラスの`div`要素に枠線を指定しています。ブラウザで開くと以下のように表示されます。

![image](https://github.com/user-attachments/assets/8f6bb3ad-5a72-4377-a439-c34e65300340)

`display: grid;`を指定しているため、6行×1列のトラックが定義され、各トラックにトラックと同じサイズでアイテムが配置されています。

## grid-template-rows
縦方向（垂直方向）にトラックを並べる数とサイズを指定します。トラックの数だけスペース区切りでpxやem、frを単位として数値で指定します。frを指定した場合は、比率に合わせて自動的にサイズが分配されます。  
まずはpxで指定してみます。

```css
.container {
  display: grid;
  height: 600px;
  grid-template-rows: 50px 30px 50px;
}
```

![image](https://github.com/user-attachments/assets/b5d2d04f-bf29-405c-9341-2b95164a5599)

3つだけ指定したので、1つ目は高さ50px、2つ目は高さ30px、3つ目は高さ50px、残りの3つは600pxから50px・30px・50pxを引いた470pxを3等分した高さでトラックが定義され、その中にアイテムが配置されました。  
次にfrで指定してみます。

```css
.container {
  display: grid;
  height: 600px;
  grid-template-rows: 2fr 1fr 0.5fr 0.5fr 1fr 1fr;
}
```

![image](https://github.com/user-attachments/assets/16010f5d-f8fd-47b6-875f-713f9022c098)

600pxを2：1：0.5：0.5：1：1で分配しています。

## grid-template-columns
横方向（水平方向）にトラックを並べる数とサイズを指定します。トラックの数だけスペース区切りでpxやem、frを単位として数値で指定します。frを指定した場合は、比率に合わせて自動的にサイズが分配されます。  
まずはpxで指定してみます。

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px 100px 100px;
}
```

![image](https://github.com/user-attachments/assets/d4cf5af9-2c6e-456c-8316-017638b13455)

4つ指定したため、2行×4列の合計8つのトラックが定義され、左上から順にアイテムが配置されています。縦方向（`grid-template-rows`）は指定していないため、等分になっていますね。  
次にfrで指定してみます。

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}
```

![image](https://github.com/user-attachments/assets/6b5b1dd6-7187-4fb1-8d02-6ec2bae65cb4)

横方向の場合は、幅（`width`プロパティ）を指定していなくても、画面幅の制約があるため、画面幅に合わせて分配されます。縦方向の場合は、アイテムのデフォルト高さからコンテナにデフォルトの高さが設定されているため、意図しないレイアウトを避けるため、明示的に高さを指定することが多いです。

## justify-content
コンテナ内の横方向のどの位置にアイテムを配置するかを指定します。

【指定できる値】
- start（初期値）：左端揃え
- end：右端揃え
- center：中央揃え
- space-between：左端のアイテムを左端に、右端のアイテムを右端に配置し、間のアイテムを等間隔に配置
- space-around：コンテナ内に中央揃えでアイテムを等間隔に配置
    - 各アイテムの左右に同じ値の余白を追加します。
- space-evenly：コンテナ内に中央揃えでアイテムを等間隔に配置
    - 各アイテムの左右の隙間の値を一定にします。

各値の違いを確認するために、3行×2列にトラックを配置した状態で比較していきます。

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  justify-content: start;
}
```

![image](https://github.com/user-attachments/assets/91e52f1a-fe0b-4214-9735-df4b161750d0)

`justify-content`プロパティは指定していませんが、初期値のstartが適用されている状態になります。

### end

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  justify-content: end;
}
```

![image](https://github.com/user-attachments/assets/af8cbc1b-263a-4d91-9158-2556e4cf353c)

### center

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  justify-content: center;
}
```

![image](https://github.com/user-attachments/assets/f2db172c-33bc-42c0-9e94-6815222637a8)

### space-between

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  justify-content: space-between;
}
```

![image](https://github.com/user-attachments/assets/b91eea3f-7087-49a9-b0a8-a124816d1bfd)

この状態でもトラックはあくまでも3行×2列の6個で、トラック自体のサイズもアイテムと同じサイズのままで、トラック間の隙間（横方向）が大きくなっていることに注意してください。以下の2つの値を指定した場合も同じです。

### space-around

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  justify-content: space-around;
}
```

![image](https://github.com/user-attachments/assets/b2244634-8ed1-4666-a84b-b6b0511e8e29)

### space-evenly

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  justify-content: space-evenly;
}
```

![image](https://github.com/user-attachments/assets/9d5e86be-bda7-44ec-9f1f-cf68ecf91be7)

## justify-items
トラック内の横方向のどの位置にアイテムを配置するかを指定します。

【指定できる値】
- stretch（初期値）：トラック幅に合わせてアイテムを伸ばす
    - アイテムに幅が指定されていればそちらが優先されます。
- start：左端揃え
- end：右端揃え
- center：中央揃え

各値の違いを確認するために、3行×2列にトラックを配置した状態で比較していきます。

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  justify-content: start;
}
```

![image](https://github.com/user-attachments/assets/56a3fed8-eba0-4f0c-baf1-beb785f21931)

`justify-items`プロパティは指定していませんが、初期値のstretchが適用されている状態になります。

### start

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  justify-items: start;
}
```

![image](https://github.com/user-attachments/assets/92707be3-d854-4600-9596-a33b101c0841)

### end

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  justify-items: end;
}
```

![image](https://github.com/user-attachments/assets/00023d10-3375-4cf5-a8e8-9a9195338732)

### center

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  justify-items: center;
}
```

![image](https://github.com/user-attachments/assets/c85a8b24-e0ef-4db5-aecf-f77dd83c5a76)

## align-content
コンテナ内の縦方向のどの位置にアイテムを配置するかを指定します。

【指定できる値】
- start：上端揃え
- end：下端揃え
- center：中央揃え
- space-between：上端のアイテムを上端に、下端のアイテムを下端に配置し、間のアイテムを等間隔に配置
- space-around：コンテナ内に中央揃えでアイテムを等間隔に配置
    - 各アイテムの上下に同じ値の余白を追加します。
- space-evenly：コンテナ内に中央揃えでアイテムを等間隔に配置
    - 各アイテムの上下の隙間の値を一定にします。

各値の違いを確認するために、3行×2列にトラックを配置した状態で比較していきます。

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  justify-content: start;
}
```

![image](https://github.com/user-attachments/assets/3c7110be-b512-4d59-b610-8821c2ccce17)

### start

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  align-content: start;
}
```

![image](https://github.com/user-attachments/assets/bf403781-2fb4-4637-8765-6c10abd5e8db)

### end

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  align-content: end;
}
```

![image](https://github.com/user-attachments/assets/7f0b72d3-3c67-4b20-ae7f-9353b729ad45)

### center

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  align-content: center;
}
```

![image](https://github.com/user-attachments/assets/de0b0661-cdde-4551-b23f-39d80c269ba3)

### space-between

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  align-content: space-between;
}
```

![image](https://github.com/user-attachments/assets/7c0e58a8-a978-4f59-a372-3ce91355588e)

この状態でもトラックはあくまでも3行×2列の6個で、トラック自体のサイズもアイテムと同じサイズのままで、トラック間の隙間（縦方向）が大きくなっていることに注意してください。以下の2つの値を指定した場合も同じです。

### space-around

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  align-content: space-around;
}
```

![image](https://github.com/user-attachments/assets/dc271a47-1e7c-4046-812e-b9561f907871)

### space-evenly

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  align-content: space-evenly;
}
```

![image](https://github.com/user-attachments/assets/343a9323-a2f4-462b-8e4a-e79057f7f6ef)

## align-items
トラック内の縦方向のどの位置にアイテムを配置するかを指定します。

【指定できる値】
- stretch（初期値）：トラック高さに合わせてアイテムを伸ばす
    - アイテムに高さが指定されていればそちらが優先されます。
- start：上端揃え
- end：下端揃え
- center：中央揃え

各値の違いを確認するために、3行×2列にトラックを配置した状態で比較していきます。

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  justify-content: start;
}
```

![image](https://github.com/user-attachments/assets/47f503e1-adab-4800-b6f5-952678b895ed)

`align-items`プロパティは指定していませんが、初期値のstretchが適用されている状態になります。

### start

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  align-items: start;
}
```

![image](https://github.com/user-attachments/assets/7938f191-6e93-476e-a704-6a14b0604b62)

### end

```css
.container {
	display: grid;
	height: 600px;
	grid-template-columns: 100px 100px;
	align-items: end;
}
```

![image](https://github.com/user-attachments/assets/2f863f34-af62-4bfc-8cfc-dac3e371fea4)

### center

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  align-items: center;
}
```

![image](https://github.com/user-attachments/assets/7b5420ae-05d2-45f6-87f3-a1f3acf5ad44)

## gap
アイテム同士の隙間（余白）を指定します。値はpxやem、%で指定できます。ここでも、3行×2列にトラックを配置した状態のレイアウトにgapを追加していきます。以下は`gap`プロパティの宣言前です。

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  justify-content: start;
}
```

![image](https://github.com/user-attachments/assets/69fa9042-894e-4dd3-b451-a4665f9d22ec)

では、`gap`プロパティを宣言してみましょう。

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  gap: 10px;
}
```

![image](https://github.com/user-attachments/assets/72d65bfb-8a2f-4786-aa85-1e2cccf6cdf0)

10pxの隙間ができました。これは、トラック間にある線が10pxになっており、トラック自体のサイズは変更されていません。グリッドレイアウトでは、`gap`プロパティは「トラック間にある線の太さを指定している」と言えます。なお、指定する値をスペース区切りで2つ指定することで、横線・縦線をそれぞれ指定することができます。1つ目が横線の値で、2つ目が縦線の値になります。

```css
.container {
  display: grid;
  height: 600px;
  grid-template-columns: 100px 100px;
  gap: 10px 20px;
}
```

![image](https://github.com/user-attachments/assets/aaf00704-1283-4ee3-ad84-ca93bdb69160)

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
    <div>div1</div>
    <div>div2</div>
    <div>div3</div>
    <div>div4</div>
    <div>div5</div>
    <div>div6</div>
    <div>div7</div>
    <div>div8</div>
    <div>div9</div>
  </div>
</body>
</html>
```

1. containerクラスの`div`要素にグリッドレイアウトで、高さが100pxで3行、幅が1：1：1の3列になるようにトラックを定義してください。

    ![image](https://github.com/user-attachments/assets/c3b3dd98-441a-45eb-8098-10b3ed6c5a5b)

    <details>
    <summary>回答例</summary>

    ```css
    /* 1. containerクラスにスタイルを適用 */
    .container {
      display: grid;
      grid-template-rows: 100px 100px 100px;
      grid-template-columns: 1fr 1fr 1fr;
    }
    ```
    </details>

2. containerクラスの`div`要素にグリッドレイアウトで、高さが100pxで3行、幅が100pxで3列になるようにトラックを定義し、横方向の各アイテムの隙間と両サイドの隙間が同じになるように配置してください。

    ![image](https://github.com/user-attachments/assets/b525cfee-b9e6-46bf-981a-76fbefc42f64)

    <details>
    <summary>回答例</summary>

    ```css
    /* 2. containerクラスにスタイルを適用 */
    .container {
      display: grid;
      grid-template-rows: 100px 100px 100px;
      grid-template-columns: 100px 100px 100px;
      justify-content: space-evenly;
    }
    ```
    </details>

3. containerクラスの`div`要素にグリッドレイアウトで、高さが100pxで3行、幅が1：1：1の3列になるようにトラックを定義し、各アイテムが各トラックの下側になるように配置してください。

    ![image](https://github.com/user-attachments/assets/9dca6a50-0527-4e0e-9fd5-624ad154e8dc)

    <details>
    <summary>回答例</summary>

    ```css
    /* 3. containerクラスにスタイルを適用 */
    .container {
      display: grid;
      grid-template-rows: 100px 100px 100px;
      grid-template-columns: 1fr 1fr 1fr;
      align-items: end;
    }
    ```
    </details>

4. containerクラスの`div`要素にグリッドレイアウトで、高さが100pxで3行、幅が1：1：1の3列になるようにトラックを定義し、トラック間の線が横線は10px、縦線は150pxになるように配置してください。

    ![image](https://github.com/user-attachments/assets/c76b6936-a6dc-4d58-b97e-a754a4f4bf85)

    <details>
    <summary>回答例</summary>

    ```css
    /* 4. containerクラスにスタイルを適用 */
    .container {
      display: grid;
      grid-template-rows: 100px 100px 100px;
      grid-template-columns: 1fr 1fr 1fr;
      align-items: stretch;
      gap: 10px 150px;
    }
    ```
    `align-items`プロパティでstretchを指定しないと、上部にある値が適用されるので注意してください。
    </details>

うまく表示されない場合は、コードを良く見返して修正しましょう。

## GitHubへプッシュしよう
編集した内容をステージング＆コミットし、自身のGitHubにあるリモートリポジトリにプッシュしましょう。以下のコマンドを実行します。

```bash
# すべてのファイルをステージング
git add .

# コミット（コミットメッセージは自由に記述してください）
git commit -m "Par13 グリッドレイアウト1"

# リモートリポジトリへプッシュ
git push origin main
```