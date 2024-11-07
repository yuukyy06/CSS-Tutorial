疑似クラスとはセレクターに付加するキーワードで、選択された要素に対して特定の状態を指定し、その状態に応じてスタイルを適用するために使用します。例えば、カーソルをボタン要素上に持ってきた時や、テキストエリアに文字を入力しようとした時に、要素の見た目が変わる時がありますよね？これは各要素に疑似クラスを使用してスタイルを適用しているためです。疑似クラスは非常に多くあるので、代表的なものを学んでいきましょう！

## hover
カーソルを要素の上に配置した状態のスタイルを設定します。以下のコードで見てみましょう。

```html
<button>クリック</button>
```
```css
button {
  border-radius: 5px;
  background-color: darkgray;
  border: darkgray solid 1px;
  font-weight: bold;
}

button:hover {
  background-color: lightgray;
}
```

![image](https://github.com/user-attachments/assets/4e0864f6-02c4-40c7-8004-d7d4843c4bcb)

カーソルが要素上にある時と無い時でスタイルが変わりますね？今回の場合は背景色だけを変更しています。

## focus
インプット要素などの入力欄にテキストを入力しよと、要素をクリックした状態のスタイルを設定します。以下のコードで見てみましょう。

```html
<input type="text" placeholder="ここに入力してください" />
```

```css
input {
  height: 24px;
  outline: gray solid 1px;
  border-radius: 5px;
  border: none;
}

input:focus {
  background-color: lightgoldenrodyellow;
  outline-color: black;
}
```

![image](https://github.com/user-attachments/assets/fdd0a37f-bacb-407b-8d39-8d7d213de011)

背景色と枠線の色が変化しました。ここで、`border: none;`を指定しているのは、ブラウザがデフォルトで`input`要素に適用したスタイルを無効にするためです。ブラウザは疑似クラスもデフォルトで適用してくれます。

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
    <h3>Part10</h3>
  </header>
  <main>
    <form>
      <input type="text" placeholder="今日の目標を入力">
      <button type="submit">送信</button>
    </form>
  </main>
</body>
</html>
```

1. 入力欄をクリックした時に、背景色が#CCFFCC、枠線色が緑色になるようにしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* input要素に疑似クラスfocusのスタイルを適用 */
    input:focus {
      background-color: #CCFFCC;
      outline-color: green;
    }
    ```
    </details>

2. 送信ボタンにカーソルを置いた時に、背景色が#FFFFA8、幅が52pxになるようにしてください。
    <details>
    <summary>回答例</summary>

    ```css
    /* button要素に疑似クラスhoverのスタイルを適用 */
    button:hover {
      background-color: #FFFFA8;
      width: 52px;
    }
    ```
    </details>

すべて記述できるとブラウザでは以下のように表示されます。実際にブラウザ上で変化を確認してください。うまく表示されない場合は、コードを良く見返して修正しましょう。

![image](https://github.com/user-attachments/assets/25743d79-b0ce-4aa6-b4c9-adfd43a880a9)

## GitHubへプッシュしよう
編集した内容をステージング＆コミットし、自身のGitHubにあるリモートリポジトリにプッシュしましょう。以下のコマンドを実行します。

```bash
# すべてのファイルをステージング
git add .

# コミット（コミットメッセージは自由に記述してください）
git commit -m "Part10 疑似クラス"

# リモートリポジトリへプッシュ
git push origin main
```