## idとclass
HTMLの要素にid属性やclass属性を指定し、セレクターでそのidやclassを指定するとその特定の要素にだけにスタイルを適用することができます。例として、以下のようなHTMLファイルがあるとします。

```html
<p>ここの色を緑色にしてください。</p>
<p>ここの色を赤色にしてください。</p>
<p>ここの色を緑色にしてください。</p>
```

今までのように`p`要素に`color: green;`を適用すると、3つある`p`要素のすべての文字色が緑色になります。2つ目の`p`要素のみ文字色を赤色にしたい場合にid属性やclass属性を使用します。

**id属性を使用した書き方**

```html
<p>ここの色を緑色にしてください。</p>
<p id="red">ここの色を赤色にしてください。</p>
<p>ここの色を緑色にしてください。</p>
```
```css
p {
  color: green;
}

/* セレクターでid属性を指定（idセレクター）する場合は値の前に#を付ける */
#red {
  color: red;
}
```

**class属性を使用した書き方**

```html
<p>ここの色を緑色にしてください。</p>
<p class="red">ここの色を赤色にしてください。</p>
<p>ここの色を緑色にしてください。</p>
```
```css
p {
  color: green;
}

/* セレクターでclass属性を指定（classセレクター）する場合は値の前に.を付ける */
.red {
  color: red;
}
```

どちらの場合もブラウザでの表示は同じ結果になります。

![image](https://github.com/user-attachments/assets/91d4b9ae-c91d-475b-ab91-fba2f98e0793)

## id属性とclass属性の違い
id属性は1つの値を1つの要素にしか適用できません。class属性は1つの値を複数の要素に適用することができます。この違いを理解しておくことはとても重要なので、しっかり確認していきましょう。  
以下のようなHTMLで、`p`要素の「この色を赤色にしてください」という文章のすべての文字色を赤色にしたい場合はclass属性を使用します。7つある`p`要素うちの3つにスタイルを適用したいからです。

```html
<p>ここの色を緑色にしてください。</p>
<p class="red">ここの色を赤色にしてください。</p>
<p>ここの色を緑色にしてください。</p>
<p class="red">ここの色を赤色にしてください。</p>
<p>ここの色を緑色にしてください。</p>
<p class="red">ここの色を赤色にしてください。</p>
<p>ここの色を緑色にしてください。</p>
```
```css
p {
  color: green;
}

.red {
  color: red;
}
```

![image](https://github.com/user-attachments/assets/a2b874f3-6a6d-4f01-b0f7-4d473228fee4)

以下のようなHTMLで、`p`要素の「この色を赤色で背景は青色にしてください」という文章と「この色を赤色で背景は黄色にしてください」という文章にのみスタイルを適用したい場合は、id属性を使用します。9つある`p`要素うちの4つにスタイルを適用し、さらにそのうちの1つずつにだけ別のスタイルを適用したいからです。id属性は値が異なれば複数の要素に適用することができます。

```html
<p>ここの色を緑色にしてください。</p>
<p class="red">ここの色を赤色にしてください。</p>
<p>ここの色を緑色にしてください。</p>
<p class="red">ここの色を赤色にしてください。</p>
<p>ここの色を緑色にしてください。</p>
<p class="red" id="blue">この色を赤色で背景は青色にしてください</p>
<p>ここの色を緑色にしてください。</p>
<p class="red" id="yellow">この色を赤色で背景は黄色にしてください</p>
<p>ここの色を緑色にしてください。</p>
```
```css
p {
  color: green;
}

.red {
  color: red;
}

#blue {
  background-color: blue;
}

#yellow {
  background-color: yellow;
}
```

![image](https://github.com/user-attachments/assets/df385a62-95fd-4b74-8927-bef76cf8f41b)

このように、**複数の要素をグループ化**してスタイルを適用したい場合はclass属性を、**1つの要素にだけ**適用したいスタイルがある場合はid属性を使用します。

## 優先順位
CSSでは後で書かれた宣言が優先されるというルールがありましたね？これ以外にも優先順位に関わるルールがあります。以下のようなCSSファイルの場合を見てみましょう。

```css
p {
  color: green;
}

.red {
  color: red;
}

#blue {
  background-color: blue;
}
```

ここではセレクターとして`p`要素、class属性`red`、id属性`blue`が宣言されています。この順番を入替えるとHTMLの表示は変わってしまうのでしょうか？

```css
#blue {
  background-color: blue;
}

.red {
  color: red;
}

p {
  color: green;
}
```

いいえ、表示は変わりません。これは、要素、class属性、id属性で優先順位が異なるからです。見ての通り、id属性の優先順位が最も高く、続いてclass属性、要素の順になります。

```css
p {
  color: green;           /* 優先順位 6位 */
}

.red {
  color: red;             /* 優先順位 4位 */
}

#blue {
  background-color: blue; /* 優先順位 2位 */
}

#blue {
  background-color: red;  /* 優先順位 1位 */
}

.red {
  color: green;           /* 優先順位 3位 */
}

p {
  color: blue;            /* 優先順位 5位 */
}
```

## class属性に複数の値を適用
class属性では複数の値を適用することができます。値をスペースを区切ることで、以下の場合は`red`、`back-yellow`の2つのclass属性の値が適用されています。

```html
<p class="red back-yellow">文字色は赤、背景色は黄!</p>
```

以下のように指定して、複雑なグループ分けも行えます。

```html
<p>文字色は青、背景色は赤!</p>
<p class="red back-yellow">文字色は赤、背景色は黄!</p>
<p class="red back-green">文字色は赤、背景色は緑!</p>
<p class="yellow back-green">文字色は黄、背景色は緑!</p>
<p>文字色は青、背景色は赤!</p>
```
```css
p {
  color: blue;
  background-color: red;
}

.red {
  color: red;
}

.yellow {
  color: yellow;
}

.back-yellow {
  background-color: yellow;
}

.back-green {
  background-color: green;
}
```

![image](https://github.com/user-attachments/assets/6011b1de-15d6-4560-a721-f0aee0cf4e1d)

## CSSを書いてみよう
インプットした内容を基に、手を動かして試してみましょう。同じディレクトリにあるindex.htmlとstyles.cssに指示に従ってコードを書いてください。わからなければ回答例を見てもOKです。index.htmlをブラウザで表示して、ビフォーアフターも確認してみてください。

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
  <h3>Part3</h3>
  <p>背景色は青色、文字色は白色ですよ</p>
  <p>背景色は青色、文字色は白色ですよ</p>
  <p>背景色は青色、文字色は白色ですよ</p>
  <p>背景色は青色、文字色は黄色ですよ</p>
  <p>背景色は青色、文字色は赤色ですよ</p>
  <p>背景色は青色、文字色は黄色ですよ</p>
  <ul>
    <li>文字色は黄色、背景色は灰色、文字サイズは16px</li>
    <li>文字色は青色、背景色は灰色、文字サイズは16px</li>
    <li>文字色は赤色、背景色は緑色、文字サイズは16px</li>
    <li>文字色は青色、背景色は緑色、文字サイズは16px</li>
    <li>文字色は黄色、背景色は茶色、文字サイズは16px</li>
    <li>文字色は赤色、背景色は茶色、文字サイズは12px</li>
  </ul>
</body>
</html>
```

1. index.html内にある6つの`p`要素に文章に合ったスタイルを適用するCSSを書いてください。必要に応じてid属性やclass属性をHTMLファイルに追記してください。
    <details>
    <summary>回答例</summary>

    id属性`red`はclass属性で指定してもOKです。
    
    ```html
    <p class="white">背景色は青色、文字色は白色ですよ</p>
    <p class="white">背景色は青色、文字色は白色ですよ</p>
    <p class="white">背景色は青色、文字色は白色ですよ</p>
    <p class="yellow">背景色は青色、文字色は黄色ですよ</p>
    <p id="red">背景色は青色、文字色は赤色ですよ</p>
    <p class="yellow">背景色は青色、文字色は黄色ですよ</p>
    ```
    ```css
    /* 6つのp要素に適用するスタイルを宣言 */
    p {
      background-color: blue;
    }
    
    .white {
      color: white;
    }
    
    .yellow {
      color: yellow;
    }
    
    #red {
      color: red;
    }
    ```
    </ditails>

2. index.html内にある6つの`li`要素に文章に合ったスタイルを適用するCSSを書いてください。必要に応じてid属性やclass属性をHTMLファイルに追記してください。
    <details>
    <summary>回答例</summary>
    id属性`small`はclass属性で指定してもOKです。
    
    ```html
    <ul>
      <li class="string-yellow back-gray">文字色は黄色、背景色は灰色、文字サイズは16px</li>
      <li class="string-blue back-gray">文字色は青色、背景色は灰色、文字サイズは16px</li>
      <li class="string-red back-green">文字色は赤色、背景色は緑色、文字サイズは16px</li>
      <li class="string-blue back-green">文字色は青色、背景色は緑色、文字サイズは16px</li>
      <li class="string-yellow back-brown">文字色は黄色、背景色は茶色、文字サイズは16px</li>
      <li class="string-red back-brown" id="small">文字色は赤色、背景色は茶色、文字サイズは12px</li>
    </ul>
    ```
    ```css
    /* 6つのli要素に適用するスタイルを宣言 */
    li {
      font-size: 16px;
    }
    
    .string-yellow {
      color: yellow;
    }
    
    .string-blue {
      color: blue;
    }
    
    .string-red {
      color: red;
    }
    
    .back-gray {
      background-color: gray;
    }
    
    .back-green {
      background-color: green;
    }
    
    .back-brown {
      background-color: brown;
    }
    
    #small {
      font-size: 12px;
    }
    ```
    </details>

すべて記述できるとブラウザでは以下のように表示されます。うまく表示されない場合は、コードを良く見返して修正しましょう。

![image](https://github.com/user-attachments/assets/abb21383-6ad2-4611-babf-c1ce7ecd84aa)

## GitHubへプッシュしよう
編集した内容をステージング＆コミットし、自身のGitHubにあるリモートリポジトリにプッシュしましょう。以下のコマンドを実行します。

```bash
# すべてのファイルをステージング
git add .

# コミット（コミットメッセージは自由に記述してください）
git commit -m "Part3 id属性とclass属性"

# リモートリポジトリへプッシュ
git push origin main
```