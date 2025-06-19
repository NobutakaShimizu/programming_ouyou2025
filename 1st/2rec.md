---
layout: section
color: amber-light
---

# 再帰関数

---
layout: top-title
color: amber-light
---
::title::
# 再帰関数
::content::

<div class="topic-box">

プログラミングにおいて, 関数の中で関数を呼び出すという操作を**再帰**と呼び, 再帰を行う関数を**再帰関数**という.

</div>

- 元来「再帰」という用語は様々な分野(言語学, 論理学, 数学など)で登場する用語である
  - 端的に言えば, ある概念$X$を定義する際に, その記述が$X$自身を含むことを指す
- 例: フィボナッチ数列$(a_n)_{n\in\Nat}$の定義は
  $$
    a_n =
    \begin{cases}
      0 & (n=0) \\
      1 & (n=1) \\
      a_{n-1} + a_{n-2} & (n\geq 2)
    \end{cases}
  $$
  これは$a_n$の定義の中に$a_{n-1}$や$a_{n-2}$が含まれているので, 再帰である
- より一般に漸化式は全て再帰であるといえる

---
layout: top-title
color: amber-light
---
::title::
# 再帰関数の例
::content::
- 再帰関数の例として, フィボナッチ数列を求める関数を考える

```python
def fib(n):
    if n == 0:
        return 0
    if n == 1:
        return 1
    else:
        return fib(n - 1) + fib(n - 2)

```

<v-clicks>

- この関数は, $n$が0または1のときは直接値を返し, それ以外のときは再帰的に`fib(n-1)`と`fib(n-2)`を計算してその和を返す (7行目)
  - このように, 自分自身の呼び出しのことを**再帰呼び出し**という
- どんな$n>1$であっても再帰呼び出しを繰り返すといずれ4行目の条件が満たされるので, 再帰呼び出しは必ず終了する
  - しかし, 例えば`fib(-1)`を実行しようとすると, 再帰呼び出しは`fib(-2)`, `fib(-3)`と続き, 終了しない
  - 再帰関数を実装する際は必ず終了するように気をつけなければならない

</v-clicks>


---
layout: top-title
color: amber-light
---
::title::
# 再帰関数の例
::content::
- 再帰関数の別の例として, 階乗を求める関数を考える

```python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)
```

<v-clicks>

- この関数は, $n$が0のときは1を返し, それ以外のときは再帰的に`factorial(n-1)`を計算してその結果に$n$を掛けた値を返す (7行目)
- この関数も再帰呼び出しを繰り返すことで, いずれ2行目の条件`n==0`が満たされるので, 再帰呼び出しは必ず終了する

</v-clicks>

---
layout: top-title
color: amber-light
---
::title::
# 再帰関数の応用: べき乗法
::content::

<div class="question">

与えられた$a,b\in\Nat$に対し, $a^b$を計算せよ (計算量は演算回数で測る).

</div>

普通に計算すると, $a,a^2,a^3,\dots,a^b$ と順に計算していくことになるので, $b$回の掛け算が必要となる
```python
def power(a, b):
    result = 1
    for _ in range(b):
        result *= a
    return result
```

<v-click>

<div class="theorem">

計算量$O(\log b)$で$a^b$を計算できる.

</div>

- 上のアルゴリズムの計算量$O(b)$よりはるかに高速
- これを可能にするアルゴリズムがべき乗法

</v-click>