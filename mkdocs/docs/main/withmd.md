# 与 MarkDown 结合

## 链接

可以用来绘制按钮。

### 简单按钮

!!! tip ""
    切换至日间模式以获得更好的显示效果

```latex
[$
\rule{40pt}{14pt}\kern{-31.5pt}\color{white}
\raisebox{4.7pt}{\footnotesize\sf Button}
$]()
```
[$
\rule{40pt}{14pt}\kern{-31.5pt}\color{white}
\raisebox{4.7pt}{\footnotesize\sf Button}
$]()

### 带边框的圆角按钮
  
其实就是 圆角边框+文本 的组合。

```
[$
\def\w{40pt}\def\h{10pt}
\def\arcoffest{3.7pt}
\color{#bebebe}
\rule[-3pt]{0.5pt}{\h}\kern{-1.2pt}
\raisebox{\arcoffest}{◜}\kern{-5pt}
\rule[\h]{\w}{0pt}
\kern{-4.5pt}\raisebox{\arcoffest}{◝}\kern{-1pt}
\rule[-3pt]{0.5pt}{\h}\kern{-\w}
\kern{-6.9pt}\raisebox{-6pt}{◟}\kern{-5pt}
\rule[-6pt]{\w}{0pt}\kern{-4.3pt}
\raisebox{-6pt}{◞}
\kern{-\w}\color{#404040}\kern{5pt}
\raisebox{-0.3pt}{\sf{\footnotesize Button}}
$]()
```
[$
\def\w{40pt}\def\h{10pt}
\def\arcoffest{3.7pt}
\color{#bebebe}
\rule[-3pt]{0.5pt}{\h}\kern{-1.2pt}
\raisebox{\arcoffest}{◜}\kern{-5pt}
\rule[\h]{\w}{0pt}
\kern{-4.5pt}\raisebox{\arcoffest}{◝}\kern{-1pt}
\rule[-3pt]{0.5pt}{\h}\kern{-\w}
\kern{-6.9pt}\raisebox{-6pt}{◟}\kern{-5pt}
\rule[-6pt]{\w}{0pt}\kern{-4.3pt}
\raisebox{-6pt}{◞}
\kern{-\w}\color{#404040}\kern{5pt}
\raisebox{-0.3pt}{\sf{\footnotesize Button}}
$]()

### 伪立体按钮

#### 普通的示例

```
[$
\color{#F6F8FA}\rule{59pt}{16pt}
\kern{-53pt}
\raisebox{6pt}{
\color{#24292F}\sf{\scriptsize 这是一个按钮}
}\kern{-52pt}
\color{#D5D8DA}\rule{57pt}{0pt}\kern{0.5pt}
\rule[1pt]{0.1pt}{15pt}
$]()
```
[$
\color{#F6F8FA}\rule{59pt}{16pt}
\kern{-53pt}
\raisebox{6pt}{
\color{#24292F}\sf{\scriptsize 这是一个按钮}
}\kern{-52pt}
\color{#D5D8DA}\rule{57pt}{0pt}\kern{0.5pt}
\rule[1pt]{0.1pt}{15pt}
$]()

#### Win95 风格

=== "演示"

    [$
    \color{c0c0c0}
    \rule{35pt}{10pt}\kern{-35pt} % 中间的填充
    \kern{-1pt}
    %
    \color{e0e0e0}
    \rule[0pt]{1pt}{10pt} % left
    \rule[10pt]{35pt}{0.5pt} % top
    %
    \kern{-35pt}\color{808080}
    \rule[0.5pt]{35pt}{0pt} % bottom0
    \rule[0.5pt]{0.5pt}{10pt} % right0
    %
    \kern{-35pt}\color{000000}
    \rule{35pt}{0pt} % bottom1
    \rule{0.5pt}{10pt} % right1
    \kern{-0.5pt}
    %
    \kern{-35pt}\kern{4pt} % 宽度+文本前的空白
    \raisebox{3.5pt}{\color{black}{\tt
    {\tiny\kern{5pt}\underline{S}tart}
    }}
    $]()


    $
    \def\winbtnNineFive#1#2{
    \color{c0c0c0}
    \rule{#1}{#2}\kern{-#1} % 中间的填充
    \kern{-1pt}
    %
    \color{e0e0e0}
    \rule[0pt]{1pt}{#2} % left
    \rule[#2]{#1}{0.5pt} % top
    %
    \kern{-#1}\color{808080}
    \rule[0.5pt]{#1}{0pt} % bottom0
    \rule[0.5pt]{0.5pt}{#2} % right0
    %
    \kern{-#1}\color{000000}
    \rule{#1}{0pt} % bottom1
    \rule{0.5pt}{#2} % right1
    \kern{-0.5pt}
    %
    \kern{-#1}\kern{-0.5pt} % 宽度+偏移
    }
    \winbtnNineFive{201pt}{50pt}\kern{0.5pt}
    \color{040084}\rule[41pt]{200pt}{8pt}\kern{-200pt}
    \kern{2pt}\raisebox{43.5pt}
    {\color{white}\tiny\tt Windows 95 style}\kern{30pt}
    {}^{\winbtnNineFive{30pt}{10pt}
    \raisebox{3pt}{\kern{8.5pt}\tt\tiny \underline{E}xit}
    }\kern{-103pt}\color{020202}
    \raisebox{30pt}{\sf\tiny
    \quad依赖于浮雕和阴影的外观来区分它们与周围元素：使用边框、渐变和
    }\kern{-171pt}
    \raisebox{20pt}{\sf\tiny
    阴影使元素突出，更易于识别为可点击元素
    }
    $

=== "源码"

    ```latex
    [$
    \color{c0c0c0}
    \rule{35pt}{10pt}\kern{-35pt} % 中间的填充
    \kern{-1pt}
    %
    \color{e0e0e0}
    \rule[0pt]{1pt}{10pt} % left
    \rule[10pt]{35pt}{0.5pt} % top
    %
    \kern{-35pt}\color{808080}
    \rule[0.5pt]{35pt}{0pt} % bottom0
    \rule[0.5pt]{0.5pt}{10pt} % right0
    %
    \kern{-35pt}\color{000000}
    \rule{35pt}{0pt} % bottom1
    \rule{0.5pt}{10pt} % right1
    \kern{-0.5pt}
    %
    \kern{-35pt}\kern{4pt} % 宽度+文本前的空白
    \raisebox{3.5pt}{\color{black}{\tt
    {\tiny\kern{5pt}\underline{S}tart}
    }}
    $]()


    $
    \def\winbtnNineFive#1#2{
    \color{c0c0c0}
    \rule{#1}{#2}\kern{-#1} % 中间的填充
    \kern{-1pt}
    %
    \color{e0e0e0}
    \rule[0pt]{1pt}{#2} % left
    \rule[#2]{#1}{0.5pt} % top
    %
    \kern{-#1}\color{808080}
    \rule[0.5pt]{#1}{0pt} % bottom0
    \rule[0.5pt]{0.5pt}{#2} % right0
    %
    \kern{-#1}\color{000000}
    \rule{#1}{0pt} % bottom1
    \rule{0.5pt}{#2} % right1
    \kern{-0.5pt}
    %
    \kern{-#1}\kern{-0.5pt} % 宽度+偏移
    }
    \winbtnNineFive{201pt}{50pt}\kern{0.5pt}
    \color{040084}\rule[41pt]{200pt}{8pt}\kern{-200pt}
    \kern{2pt}\raisebox{43.5pt}
    {\color{white}\tiny\tt Windows 95 style}\kern{30pt}
    {}^{\winbtnNineFive{30pt}{10pt}
    \raisebox{3pt}{\kern{8.5pt}\tt\tiny \underline{E}xit}
    }\kern{-103pt}\color{020202}
    \raisebox{30pt}{\sf\tiny
    \quad依赖于浮雕和阴影的外观来区分它们与周围元素：使用边框、渐变和
    }\kern{-195pt}
    \raisebox{20pt}{\sf\tiny
    阴影使元素突出，更易于识别为可点击元素
    }
    $
    ```