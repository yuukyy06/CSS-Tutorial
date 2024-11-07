## フレックスボックスとは？
要素を横方向もしくは縦方向の1次元に配置する方法です。Webサイトでは、要素が規則的に配置されることが多くありますが、フレックスボックスを使うことでそれを簡単に実現することができます。

## フレックスボックスでのレイアウト
スタイルを適用する要素の親要素に対し、以下のプロパティを指定します。この親要素のことを「コンテナ」と呼びます。

【使用する主なプロパティ】
- `display`：flexを指定することで以下のレイアウトを適用（`display: flex;`）
- `flex-direction`：要素を並べる方向を指定
- `align-items`：要素をどの位置に配置するかを指定
    - 要素が横並びの時（`flex-direction: row;`）は縦方向の配置を指定します。
    - 要素が縦並びの時（`flex-direction: column;`）は横方向の配置を指定します。
- `justify-content`：要素をどの位置に配置するかを指定
    - 要素が横並びの時（`flex-direction: row;`）は横方向の配置を指定します。
    - 要素が縦並びの時（`flex-direction: column;`）は縦方向の配置を指定します。
- `gap`：要素同士の隙間（余白）を指定

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
  <main>
    <div>div1</div>
    <div>div2</div>
    <div>div3</div>
    <div>div4</div>
    <div>div5</div>
    <div>div6</div>
    <div>div7</div>
    <div>div8</div>
    <div>div9</div>
    <div>div10</div>
  </main>
</body>
</html>
```
```css
* {
  padding: 0;
  margin: 0;
}

body {
  margin-top: 20px;
}

div {
  box-sizing: border-box;
  width: 160px;
  height: 160px;
  border: 1px solid black;
}
```

わかりやすいように、`div`要素のサイズを指定して`border`を追加していますが、レイアウトに関してはデフォルトのままとなっています。画面が長くなるので少し加工していますが、以下のように表示されます。

![image](https://github.com/user-attachments/assets/71cc10d7-33fc-4acb-a673-ace80e66408c)

## flex-direction
コンテナ内の要素の並べる方向を指定します。

【指定できる値】
- row：要素を左から右へ横方向に配置
- row-reverse：要素を右から左へ横方向に配置
- column：要素を上から下へ縦方向に配置
- column-reverse：要素を下から上へ縦方向に配置

現在はcolumnで指定した場合と同じレイアウトの為、columnは省いて他の値をみていきます。

### row
ここからのCSSは上記に追加した部分だけになるので注意してください。

```css
/* rowを適用 */
main {
 display: flex;
 flex-direction: row;
}
```

![image](https://github.com/user-attachments/assets/a015efd0-dec1-4c08-b8c3-89ca39b3db83)

### row-reverse

```css
/* row-reverseを適用 */
main {
  display: flex;
  flex-direction: row-reverse;
}
```

![image](https://github.com/user-attachments/assets/a946c63f-ea63-47c6-ae28-9f2b2f3a7441)

### column-reverse

```css
/* column-reverseを適用 */
main {
  display: flex;
  flex-direction: column-reverse;
}
```

![image](https://github.com/user-attachments/assets/b7ab3922-e9d7-4d3e-bc66-d21fa3025220)

## align-items
コンテナとなる要素に`flex-direction: row;`が指定され、要素が横並びになっている時は、縦方向（垂直方向）の配置、`flex-direction: column;`が指定され、要素が縦並びになっている時は、横方向（水平方向）の配置を指定します。

【指定できる値】
- stretch（初期値）：要素の幅もしくは高さをコンテナに合わせて伸縮
- center：中央揃え
- flex-start：上端もしくは左端揃え
- flex-end：下端もしくは右端揃え
- baseline：要素のベースライン（テキストなどの下端もしくは左端）を揃えて配置

ここでは、要素を横並びにした時の`align-items`プロパティを見ていきます。わかりやすいように`main`要素の高さを指定して枠線を追加しています。

### stretch

```css
main {
  height: 300px;
  border: 1px solid black;
  display: flex;
  flex-direction: row;
}
```

![image](https://github.com/user-attachments/assets/44cc4ad2-1386-4553-bb46-894b214a56cf)

`align-items`プロパティを指定していない場合、初期値のstretchが適用されますが、要素自身に`height`プロパティを指定しているので要素は伸縮しません。`height`プロパティをコメントアウトして再度表示してみます。

```css
div {
  box-sizing: border-box;
  width: 160px;
  /* height: 160px; */
  border: 1px solid black;
}

main {
  height: 300px;
  border: 1px solid black;
  display: flex;
  flex-direction: row;
}
```

![image](https://github.com/user-attachments/assets/41a3d138-f56e-492e-b2d4-d77005f4b35e)

### center
要素の`height`プロパティは戻しておきます。

```css
div {
  box-sizing: border-box;
  width: 160px;
  height: 160px;
  border: 1px solid black;
}

main {
  height: 300px;
  border: 1px solid black;
  display: flex;
  flex-direction: row;
  align-items: center;
}
```

![image](https://github.com/user-attachments/assets/90b6a7c5-3ff5-4c9d-adbe-53a6c4109a08)

コンテナである`main`要素の中央に要素が揃いました。各`div`要素の高さが違う場合では以下のような表示になります。

![image](https://github.com/user-attachments/assets/592a2211-dc47-40a0-807b-b294f3542f7b)

### flex-start

```css
main {
  height: 300px;
  border: 1px solid black;
  display: flex;
  flex-direction: row;
  align-items: flex-start;
}
```

![image](https://github.com/user-attachments/assets/7d31cec5-4c39-499b-9230-250cd7308aac)

### flex-end

```css
main {
  height: 300px;
  border: 1px solid black;
  display: flex;
  flex-direction: row;
  align-items: flex-end;
}
```

![image](https://github.com/user-attachments/assets/97a9cfa0-fa60-413e-b28a-91717445f4b8)

### baseline

```css
main {
  height: 300px;
  border: 1px solid black;
  display: flex;
  flex-direction: row;
  align-items: baseline;
}
```

![image](https://github.com/user-attachments/assets/951b3be8-f4a6-4537-a7b0-8d908beade84)

flex-startと同じに見えますが、各要素のテキストの位置が揃っているのでbaselineが適用されています。テキストがdiv1の要素にだけ`line-height: 160px;`を適用してみると、「テキストの下端」で揃うのがわかります。

![image](https://github.com/user-attachments/assets/4ecdf955-744e-46b2-95d0-6faefb5930c3)

## justify-content
コンテナとなる要素に`flex-direction: row;`が指定され、要素が横並びになっている時は、横方向（水平方向）の配置、`flex-direction: column;`が指定され、要素が縦並びになっている時は、縦方向（垂直方向）の配置を指定します。

【指定できる値】
- flex-start（初期値）：左端もしくは上端揃え
- flex-end：右端もしくは下端揃え
- center：中央揃え
- space-between：左端（上端）の要素を左端（上端）に、右端（下端）の要素を右端（下端）に配置し、間の要素を等間隔に配置
- space-around：コンテナ内に中央揃えで要素を等間隔に配置
    - 各要素の左右もしくは上下に同じ値の余白を追加します。
- space-evenly：コンテナ内に中央揃えで要素を等間隔に配置
    - 各要素の隙間の値を一定にします。

ここでは、要素を横並びにした時の`justify-content`プロパティをみていきます。

### flex-end

```css
main {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
}
```

![image](https://github.com/user-attachments/assets/4f438091-e770-4cf9-bc0a-b0bbdd0936be)

### center

```css
main {
  display: flex;
  flex-direction: row;
  justify-content: center;
}
```

![image](https://github.com/user-attachments/assets/33a6b6a2-392a-4054-b0a5-732dcc4b4062)

### space-between

```css
main {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
```

![image](https://github.com/user-attachments/assets/3c589d70-c99c-4788-85aa-869d8d32f698)

### space-around

```css
main {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
```

![image](https://github.com/user-attachments/assets/d56d5465-d875-4877-814c-c169981088c8)

div1の左の隙間とdiv10の右の隙間は同じ幅ですが、要素間の隙間はその2倍になっています。

### space-evenly

```css
main {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
}
```

![image](https://github.com/user-attachments/assets/fd0a32de-bfb8-4500-85b7-6e368db7c8f5)

div1の左の隙間もdiv10の右の隙間も要素間の隙間も同じ幅になっています。

## gap
コンテナ内の要素同士の隙間（余白）を指定します。値はpxやem、%で指定できます。`flex-direction`プロパティでrowをしていしてもcolumnを指定しても適用されます。  
ここではrowの場合でみていきます。`justify-content`プロパティで中央揃えにし、要素間の隙間を10pxで指定します。

```css
main {
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 10px;
}
```

![image](https://github.com/user-attachments/assets/6599f8cf-8bfd-4231-a903-5310150fc6c8)

`justify-content`プロパティでspace-betweenやspace-around、space-evenlyを指定した場合とはまた違った配置ができるようになります。

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
    <ul>
      <li><a href="">Home</a></li>
      <li><a href="">Blog</a></li>
      <li><a href="">Gallery</a></li>
    </ul>
  </header>
  <main>
    <div>div1</div>
    <div>div2</div>
    <div>div3</div>
    <div>div4</div>
    <div>div5</div>
    <div>div6</div>
    <div>div7</div>
    <div>div8</div>
    <div>div9</div>
    <div>div10</div>
  </main>
  <footer>
    <p>RareTECH</p>
  </footer>
</body>
</html>
```

1. `body`要素にある`header`、`main`、`footer`要素を中央揃えの縦並びにし、各要素の隙間を50pxにしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* body要素にスタイルを適用 */
    body {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 50px;
    }
    ```
    </details>

2. `header`要素にある`h1`、`ul`要素を下端揃えの横並びにし、各要素が左右の端に配置されるようにしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* header要素にスタイルを適用 */
    header {
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      align-items: flex-end;
    }
    ```
    </details>

3. `ul`要素にある`li`要素を横並びにし、各要素の隙間を24pxにしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* ul要素にスタイルを適用 */
    ul {
      display: flex;
      flex-direction: row;
      gap: 24px;
    }
    ```
    </details>

4. `div`要素の幅と高さを200pxにし、テキストが中央揃えになるように`text-align`、`line-height`プロパティを指定してください。
    <details>
    <summary>回答例</summary>

    ```css
    /* div要素にスタイルを適用 */
    div {
      width: 200px;
      height: 200px;
      text-align: center;
      line-height: 200px;
    }
    ```
    </details>

5. `main`要素にある`div`要素を横並びにし、各要素の隙間を10pxにしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* main要素にスタイルを適用 */
    main {
      display: flex;
      flex-direction: row;
      justify-content: center;
      gap: 10px;
    }
    ```
    </details>

すべて記述できるとブラウザでは以下のように表示されます。うまく表示されない場合は、コードを良く見返して修正しましょう。

![image](https://github.com/user-attachments/assets/d53e4da3-c51b-4b09-a763-cf1a0ec6436e)

## GitHubへプッシュしよう
編集した内容をステージング＆コミットし、自身のGitHubにあるリモートリポジトリにプッシュしましょう。以下のコマンドを実行します。

```bash
# すべてのファイルをステージング
git add .

# コミット（コミットメッセージは自由に記述してください）
git commit -m "Par12 フレックスボックス"

# リモートリポジトリへプッシュ
git push origin main
```