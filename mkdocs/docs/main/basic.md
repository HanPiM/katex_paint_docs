# 基础知识

## 编辑环境

  本人推荐使用 Atom/VSCode + [Markdown Preview Enhanced](https://shd101wyy.github.io/markdown-preview-enhanced/#/zh-cn/) 插件。

  当然，使用洛谷自带的剪贴板也不是不可以。

## 基础命令

!!! note "注意"
    本章所出现的：

    - `offset` 参数，除特殊说明，均可以为负。

    - 用于输出的 `text` 参数，除特殊说明，均表示会**以文本模式输出**，相对应的的，`source` 表示会**以数学模式输出**。

### \rule

`\rule[offset]{w}{h}`

在当前位置上方 `offset` 处绘制一个长宽为 `w` 和 `h` 的矩形。

!!! tip "提示"
    - 如果指定的 `offset` 超出了当前块的范围，则会使当前块的高度改变以容纳绘制的矩形，而不是穿插到其他块。
    - 绘制的矩形会挡住同一层的文字，使用像 `\raisebox, \cancel, \underline` 之类的命令或在另一个块输出可以解决。
    - 洛谷渲染出来有时会丢失一些边角像素。（原因未知）

??? example "示例"
    ```latex
    \rule{10pt}{6pt}\quad
    \rule[5pt]{10pt}{6pt}\quad
    \rule[-10pt]{10pt}{6pt}\quad
    \rule[10pt]{10pt}{6pt}\quad
    \color{green}\rule{50pt}{10pt}\kern{-10pt}\color{red}aaa %文字被挡住了
    ```
    <div class="result" markdown>

    $
    \rule{10pt}{6pt}\quad
    \rule[5pt]{10pt}{6pt}\quad
    \rule[-10pt]{10pt}{6pt}\quad
    \rule[10pt]{10pt}{6pt}\quad
    \color{green}\rule{50pt}{10pt}\kern{-10pt}\color{red}aaa %文字被挡住了
    $

    </div>
  
### \raisebox

`\raisebox{offset}{text}` 

将文本 `text` 的输出上移 `offest`。

!!! tip "提示"
    - 同 `\rule` 一样不会穿插到其他块。

??? example "示例"
    ```
    text $\raisebox{10pt}{text}$

    $$\sin\raisebox{5pt}{$\tan$}\cos$$
    ```
    <div class="result" markdown>

    text $\raisebox{10pt}{text}$

    $$\sin\raisebox{5pt}{$\tan$}\cos$$

    </div>
  
### \kern

`\kern{offset}`

输出大小为 `offset` 的间距。（可用于水平移动当前位置）

??? example "示例"
    ```latex
    a \kern{20pt} b\newline
    a \kern{-15pt} b\kern{15pt}
    ```
    <div class="result" markdown>

    $
    a \kern{20pt} b\newline
    a \kern{-15pt} b\kern{15pt}
    $

    </div>

### \\\\

`\\[offset]`

输出竖直间距。或者说：先进行换行，再在竖直方向上移动 `offset` 距离。

!!! warning "警告"
    `\cr` 和 `\newline` 将不再能使用该参数。
    参见 [KaTeX Doc #newline-and-cr](https://katex.org/docs/migration.html#newline-and-cr)

!!! tip "提示"
    回到开头是指当前段落开头，而不是块的开头。

??? example "示例"
    ```latex
    $a\\[0pt]bcd\\[-20pt]efghij$

    $averyveryverylonglonglongsentence....\\[-13pt]\color{blue}\tt{cameback}$

    aaa $bb\\c$
    ```
    <div class="result" markdown>

    $a\\[0pt]bcd\\[-20pt]efghij$

    $averyveryverylonglonglongsentence....\\[-13pt]\color{blue}\tt{cameback}$

    aaa $bb\\c$
    </div>

### \cancel 系列

`\cancel{text}` / `\bcancel{text}` / `\xcancel{text}`

给文字 `text` 画斜线。

!!! tip "提示"
    - 内容高度 < 0.17 pt 不会显示
    - 内容宽度 < 4 pt 时显示宽度会变成 4 pt
    - 斜线宽度会略多于文字宽度，需要微调才能绘制的比较精准

        <small>【对于非讨论区】每种字体所对应的两边多出的宽度（单位pt）：</small>

        | 字体大小 | 大小 | 字体大小 | 大小 |
        | -------- | ---- | -------- | ---- |
        | normal   | 2    | large    | 2.4  |
        | tiny     | 1    | Large    | 2.8  |
        | script   | 1.4  | LARGE    | 3.5  |
        | footnote | 1.6  | huge     | 4    |
        | small    | 1.8  | Huge     | 5    |

$\cancel{cancel}\quad\bcancel{bcancel}\quad\xcancel{xcancel}$

`\cancel{cancel}\quad\bcancel{bcancel}\quad\xcancel{xcancel}`

当把文字换成透明的矩形时，就可以用来画斜线了：

$
\def\xcline#1#2{
    \kern{2pt}
    \cancel{\phantom{\rule{#1}{#2}}\kern{-4pt}}
    \kern{2pt}
}
\def\xbcline#1#2{
    \kern{2pt}
    \bcancel{\phantom{\rule{#1}{#2}}\kern{-4pt}}
    \kern{2pt}
}
\xcline{10pt}{10pt}
\xbcline{10pt}{10pt}
\xcline{10pt}{20pt}
$
    
```latex
\def\xcline#1#2{
    \kern{2pt}
    \cancel{\phantom{\rule{#1}{#2}}\kern{-4pt}}
    \kern{2pt}
}
\def\xbcline#1#2{
    \kern{2pt}
    \bcancel{\phantom{\rule{#1}{#2}}\kern{-4pt}}
    \kern{2pt}
}
\xcline{10pt}{10pt}
\xbcline{10pt}{10pt}
\xcline{10pt}{20pt}
```
    
[复杂示例](../../appendix/other_examples/#_3)

### \mathlap 系列

`\mathllap{source}` / `\mathclap{source}` / `\mathrlap{source}`

用于消除字符的碰撞体积，以减少公式输出时的不必要空白。
其中 llap，rlap，clap 分别对应着向左排版（右对齐）、向右排版（左对齐）、居中对齐。

$
S = \sum\limits_{1\le i\le j\le n} a_{ij}\quad
S = \sum\limits_{\mathclap{1\le i\le j\le n}} a_{ij}
$

```latex
S = \sum\limits_{1\le i\le j\le n} a_{ij}\quad
S = \sum\limits_{\mathclap{1\le i\le j\le n}} a_{ij}
```

对于绘制来说，这个命令可以用于消除绘制内容的碰撞箱。

这是相当有用的，例如你的绘制宏使用一串文字作为参数，在某处要输出文字后回到开头，因为是参数，你无法知道具体的宽度，这意味着你无法使用 `\kern`，但你只需要使用 `\mathrlap` 就可以了。

## 强行转换 math 模式

### 行间模式
用 `$...$` 将公式包裹起来

### 行内模式

讨论区暂无解决方法。
非讨论区可使用 `\boxed` 解除限制。

$\text{\color{transparent}\boxed{\color{black}xxxx}}$ `\text{\color{transparent}\boxed{xxxx}}`

!!! tip "提示"

    `\boxed` 限制：

    - 内容宽度 小于两边多出宽度之和 时碰撞箱会变成 两边多出宽度之和

        <small> 每种字体所对应的两边多出的宽度（单位pt）：</small>

        | 字体大小 | 大小 | 字体大小 | 大小 |
        | -------- | ---- | -------- | ---- |
        | normal   | 2.99 | large    | 3.6  |
        | tiny     | 1.49 | Large    | 4.31 |
        | script   | 2.1  | LARGE    | 5.18 |
        | footnote | 2.4  | huge     | 6.43 |
        | small    | 2.7  | Huge     | 7.46 |