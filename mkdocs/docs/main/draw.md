# 绘制

## 简单图形

对于常见的基本图形（如 $\huge\bigcirc$ `\huge\bigcirc` ）
可直接使用对应命令/字符。

但对于稍微复杂的图形，我们很难找到某个可以满足要求的字符/命令。此时我们则需要将多个基本图形结合到一起以达到目标效果。

??? example "例-圆角矩形边框"

    可以拆分成 4 条线段和 4 段 $\dfrac{1}{4}$ 圆弧。

    对于线段，直接使用 `\rule` 绘制。\
    对于圆弧，由于 $\LaTeX$ 中没有 $\dfrac{1}{4}$ 圆弧的命令，所以使用特殊字符： `◜◝◟◞` 

    缺点：无法自定义圆角大小，无法在讨论区渲染。

    ```latex
    --8<-- "examples/main/draw_roundrc.txt"
    ```
    <div class="result" markdown>

    --8<-- "examples/main/draw_roundrc.txt"

    </div>
      
??? example "例-信息角标"

    这个比较容易实现，使用 两个圆 + 一个矩形 就可以画出。

    
    ```latex
    --8<-- "examples/main/draw_infobadage.txt"
    ```
    <div class="result" markdown>

    --8<-- "examples/main/draw_infobadage.txt"

    </div>

??? example "例-简单提示框"

    用 圆 + 矩形 就可以画出。

    === "演示"

        --8<-- "examples/main/draw_simpnote.txt"

    === "源码"

        ```latex
        --8<-- "examples/main/draw_simpnote.txt"
        ```

## 其他
  
### 阴影
      
原理：绘制由灰到白的渐变色。（计算渐变色的方法有很多，但那超出了本文的范围）

示例：

```latex
\def\w{100pt}
\def\drawx#1#2{\color{#1}\rule[#2]{\w}{0pt}\kern{-\w}}
\drawx{bfbfbf}{0pt}
\drawx{d6d6d6}{-0.5pt}
\drawx{ececec}{-1.0pt}
\drawx{f8f8f8}{-1.5pt}\newline
\drawx{2a2a2a}{0pt}
\drawx{2e2e2e}{-0.5pt}
\drawx{2f2f2f}{-1.0pt}
\drawx{313131}{-1.5pt}
```
<div class="result" markdown>
$
\def\w{100pt}
\def\drawx#1#2{\color{#1}\rule[#2]{\w}{0pt}\kern{-\w}}
\drawx{bfbfbf}{0pt}
\drawx{d6d6d6}{-0.5pt}
\drawx{ececec}{-1.0pt}
\drawx{f8f8f8}{-1.5pt}\newline
\drawx{2a2a2a}{0pt}
\drawx{2e2e2e}{-0.5pt}
\drawx{2f2f2f}{-1.0pt}
\drawx{313131}{-1.5pt}
$
</div>

### 简单像素画
  
原理：逐一绘制像素。

缺点：公式中元素的数量似乎有限制，绘制大小有限。

可优化：对位于同一列/行的同颜色像素一起绘制。

=== "演示"

    !!! note inline end ""
        这是游戏 [minecraft](https://www.minecraft.net) 中的工具：铁镐

    --8<-- "examples/main/draw_simppic.txt"

=== "源码"
    ```latex
    --8<-- "examples/main/draw_simppic.txt"
    ```

[生成器](../../appendix/B/#-)