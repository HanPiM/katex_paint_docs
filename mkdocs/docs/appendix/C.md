# 附 C - 高亮代码

!!! tip ""
    此文仅供娱乐，不建议使用此方法高亮代码。

众所周知，洛谷的 LaTeX 环境不支持 Listings 等更方便的代码高亮包，所以我们只能使用 MarkDown 来高亮代码

我找到了 [GNU Source-highlight](https://www.gnu.org/software/src-highlite/) 这个好东西。可以用来高亮代码，这没什么，但它竟然可以将高亮后的代码以 LaTeX 格式输出。

但是它输出的代码并不能直接用在洛谷上（而且配色很拉），于是我把他的配置改了一下：

```title="lglatex.outlang"
extension "tex"

doctemplate
"% Generator: GNU source-highlight, by Lorenzo Bettini, http://www.gnu.org/software/src-highlite
$header\begin{array}{ll}
"
"\end{array}$footer"
end

bold "\textbf{$text}"
italics "\textit{$text}"
underline "\underline{$text}"
fixed "\texttt{$text}"

notfixed "\texttt{$text}&" # only for latex

translations
"_" "\newline_"
"{" "\newline{"
"}" "\newline}"
#"<" "$<$"
#"\newline\>" "$\newline\>$"
"&" "\newline&"
"\newline" "\newlineverb|\|"
"^" "\newlinetextasciicircum{}"
"~" "\newlinetextasciitilde{}"
"\n" " \newline\newline\n"
#"  " "\newlinehspace*{2ex} "
#"\t" "\newlinehspace*{8ex} "
" " "\newline "
"\t" "\newline \newline \newline \newline \newline \newline \newline \newline "
"%" "\newline%"
"#" "\newlineverb|#|"
"$" "\newline$"
#"\"" "\"{}" # avoids problems with some inputenc
end

color "\textcolor{$style}{$text}"

colormap
"green" "Green"
"red" "Red"
"darkred" "BrickRed"
"blue" "Blue"
"brown" "Brown"
"pink" "Pink"
"yellow" "Yellow"
"cyan" "Cyan"
"purple" "Purple"
"orange" "Orange"
"brightorange" "YellowOrange"
"brightgreen" "YellowGreen"
"darkgreen" "ForestGreen"
"black" "Black"
"teal" "TealBlue"
"gray" "Gray"
"darkblue" "RoyalBlue"
default "Black"
end
```

```title="lglatex.style"
keyword #569CD6 f; 	// for language keywords
type #569CD6 f;	// for basic types
string #D39B83 f;		// for strings and chars
comment #57A64A f;	// for comments
number #718C00;		// for literal numbers
preproc #9B9B9B f;	// for preproc directives (e.g. #include, import)
symbol black f;	// for simbols (e.g. <, \newline\>, +)
function #F5871F f;	// for function calls and declarations
cbracket black f;		// for block brackets (e.g. {, })

normal black f;

// line numbers
linenum gray nf;

// Internet related
url #569CD6 u, f;

// other elements for ChangeLog and Log files
date blue b ;
time darkblue b ;
ip darkgreen ;
file darkblue b ;
name darkgreen ;

// for Prolog, Perl...
variable darkgreen ;

// explicit for Latex
italics darkgreen i;
bold darkgreen b;
underline darkgreen u;
fixed green f;
argument darkgreen;
optionalargument purple;
math orange;
```

```title="执行命令"
source-highlight --data-dir "安装目录\share\source-highlight" -s cpp -f lglatex --style-file lglatex.style -i test.cpp --line-number
```

`--line-number` 选项可选，表示是否输出行号

于是就可以在洛谷用 LaTeX 渲染代码了~

_此代码来自 [P1001 的一篇题解](https://www.luogu.com.cn/blog/Num233/solution-p1001) (有改动)_

=== "演示"

    !!! tip ""
        切换至日间模式以获得更好的显示效果。

        由于 LaTeX 版本不同，此处渲染的代码经过了修改，与源码不同，但确保源码可在洛谷云剪贴板正确渲染。

    $
    \footnotesize
    % Generator: GNU source-highlight, by Lorenzo Bettini, http://www.gnu.org/software/src-highlite
    \begin{array}{ll}
    \texttt{\textcolor{#9B9B9B}{\verb|#|include}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#D39B83}{<stdio.h\>}} \newline
    \texttt{\textcolor{#569CD6}{int}}\texttt{\textcolor{Black}{\ a}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ b}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ c}}\texttt{\textcolor{Black}{;}} \newline
    \texttt{\textcolor{#569CD6}{int}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#F5871F}{main}}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{Black}{)}} \newline
    \texttt{\textcolor{Black}{\verb|{|}} \newline
    \texttt{\textcolor{Black}{\verb|    |}}\texttt{\textcolor{#569CD6}{long}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#569CD6}{long}}\texttt{\textcolor{Black}{\ l\ }}\texttt{\textcolor{Black}{=}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{-}}\texttt{\textcolor{#569CD6}{int}}\texttt{\textcolor{Black}{(}}\textcolor{#718C00}{1e9}\texttt{\textcolor{Black}{)}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{<}}\texttt{\textcolor{Black}{<}}\texttt{\textcolor{Black}{\ }}\textcolor{#718C00}{1}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ r\ }}\texttt{\textcolor{Black}{=}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#569CD6}{int}}\texttt{\textcolor{Black}{(}}\textcolor{#718C00}{1e9}\texttt{\textcolor{Black}{)}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{<}}\texttt{\textcolor{Black}{<}}\texttt{\textcolor{Black}{\ }}\textcolor{#718C00}{1}\texttt{\textcolor{Black}{;}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#57A64A}{//}}\texttt{\textcolor{#57A64A}{左边界和右边界}} \newline
    \texttt{\textcolor{Black}{\verb|    |}}\texttt{\textcolor{#F5871F}{scanf}}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{#D39B83}{"\%d\%d"}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{\&}}\texttt{\textcolor{Black}{a}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{\&}}\texttt{\textcolor{Black}{b}}\texttt{\textcolor{Black}{)}}\texttt{\textcolor{Black}{;}} \newline
    \texttt{\textcolor{Black}{\verb|    |}}\texttt{\textcolor{#569CD6}{while}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{Black}{r\ }}\texttt{\textcolor{Black}{-}}\texttt{\textcolor{Black}{\ l\ }}\texttt{\textcolor{Black}{\>}}\texttt{\textcolor{Black}{\ }}\textcolor{#718C00}{1}\texttt{\textcolor{Black}{)}} \newline
    \texttt{\textcolor{Black}{\verb|    |}}\texttt{\textcolor{Black}{\verb|{|}} \newline
    \texttt{\textcolor{Black}{\verb|        |c\ }}\texttt{\textcolor{Black}{=}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{Black}{l\ }}\texttt{\textcolor{Black}{+}}\texttt{\textcolor{Black}{\ r}}\texttt{\textcolor{Black}{)}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{\>}}\texttt{\textcolor{Black}{\>}}\texttt{\textcolor{Black}{\ }}\textcolor{#718C00}{1}\texttt{\textcolor{Black}{;}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#57A64A}{//}}\texttt{\textcolor{#57A64A}{二分的步骤啦}} \newline
    \texttt{\textcolor{Black}{\verb|        |}}\texttt{\textcolor{#569CD6}{if}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{Black}{c\ }}\texttt{\textcolor{Black}{-}}\texttt{\textcolor{Black}{\ b\ }}\texttt{\textcolor{Black}{<}}\texttt{\textcolor{Black}{\ a}}\texttt{\textcolor{Black}{)}} \newline
    \texttt{\textcolor{Black}{\verb|            |l\ }}\texttt{\textcolor{Black}{=}}\texttt{\textcolor{Black}{\ c}}\texttt{\textcolor{Black}{;}} \newline
    \texttt{\textcolor{Black}{\verb|        |}}\texttt{\textcolor{#569CD6}{else}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#569CD6}{if}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{Black}{c\ }}\texttt{\textcolor{Black}{-}}\texttt{\textcolor{Black}{\ b\ }}\texttt{\textcolor{Black}{\>}}\texttt{\textcolor{Black}{\ a}}\texttt{\textcolor{Black}{)}} \newline
    \texttt{\textcolor{Black}{\verb|            |r\ }}\texttt{\textcolor{Black}{=}}\texttt{\textcolor{Black}{\ c}}\texttt{\textcolor{Black}{;}} \newline
    \texttt{\textcolor{Black}{\verb|        |}}\texttt{\textcolor{#569CD6}{else}} \newline
    \texttt{\textcolor{Black}{\verb|            |}}\texttt{\textcolor{#569CD6}{return}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#F5871F}{printf}}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{#D39B83}{"\%d\verb|\\|n"}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ c}}\texttt{\textcolor{Black}{)}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ }}\textcolor{#718C00}{0}\texttt{\textcolor{Black}{;}} \newline
    \texttt{\textcolor{Black}{\verb|    |}}\texttt{\textcolor{Black}{\verb|}|}} \newline
    \texttt{\textcolor{Black}{\verb|    |}}\texttt{\textcolor{#569CD6}{if}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{Black}{l\ }}\texttt{\textcolor{Black}{!}}\texttt{\textcolor{Black}{=}}\texttt{\textcolor{Black}{\ r}}\texttt{\textcolor{Black}{)}} \newline
    \texttt{\textcolor{Black}{\verb|        |}}\texttt{\textcolor{#569CD6}{return}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#F5871F}{printf}}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{#D39B83}{"\%d\verb|\\|n"}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ r}}\texttt{\textcolor{Black}{)}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ }}\textcolor{#718C00}{0}\texttt{\textcolor{Black}{;}} \newline
    \texttt{\textcolor{Black}{\verb|}|}}\end{array}
    $

=== "源码"

    ```latex
    $
    \footnotesize
    % Generator: GNU source-highlight, by Lorenzo Bettini, http://www.gnu.org/software/src-highlite
    \begin{array}{ll}
    \texttt{\textcolor{#9B9B9B}{\#include}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#D39B83}{<stdio.h>}} \\
    \texttt{\textcolor{#569CD6}{int}}\texttt{\textcolor{Black}{\ a}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ b}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ c}}\texttt{\textcolor{Black}{;}} \\
    \texttt{\textcolor{#569CD6}{int}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#F5871F}{main}}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{Black}{)}} \\
    \texttt{\textcolor{Black}{\{}} \\
    \texttt{\textcolor{Black}{\ \ \ \ }}\texttt{\textcolor{#569CD6}{long}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#569CD6}{long}}\texttt{\textcolor{Black}{\ l\ }}\texttt{\textcolor{Black}{=}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{-}}\texttt{\textcolor{#569CD6}{int}}\texttt{\textcolor{Black}{(}}\textcolor{#718C00}{1e9}\texttt{\textcolor{Black}{)}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{<}}\texttt{\textcolor{Black}{<}}\texttt{\textcolor{Black}{\ }}\textcolor{#718C00}{1}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ r\ }}\texttt{\textcolor{Black}{=}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#569CD6}{int}}\texttt{\textcolor{Black}{(}}\textcolor{#718C00}{1e9}\texttt{\textcolor{Black}{)}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{<}}\texttt{\textcolor{Black}{<}}\texttt{\textcolor{Black}{\ }}\textcolor{#718C00}{1}\texttt{\textcolor{Black}{;}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#57A64A}{//}}\texttt{\textcolor{#57A64A}{左边界和右边界}} \\
    \texttt{\textcolor{Black}{\ \ \ \ }}\texttt{\textcolor{#F5871F}{scanf}}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{#D39B83}{"\%d\%d"}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{\&}}\texttt{\textcolor{Black}{a}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{\&}}\texttt{\textcolor{Black}{b}}\texttt{\textcolor{Black}{)}}\texttt{\textcolor{Black}{;}} \\
    \texttt{\textcolor{Black}{\ \ \ \ }}\texttt{\textcolor{#569CD6}{while}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{Black}{r\ }}\texttt{\textcolor{Black}{-}}\texttt{\textcolor{Black}{\ l\ }}\texttt{\textcolor{Black}{>}}\texttt{\textcolor{Black}{\ }}\textcolor{#718C00}{1}\texttt{\textcolor{Black}{)}} \\
    \texttt{\textcolor{Black}{\ \ \ \ }}\texttt{\textcolor{Black}{\{}} \\
    \texttt{\textcolor{Black}{\ \ \ \ \ \ \ \ c\ }}\texttt{\textcolor{Black}{=}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{Black}{l\ }}\texttt{\textcolor{Black}{+}}\texttt{\textcolor{Black}{\ r}}\texttt{\textcolor{Black}{)}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{>}}\texttt{\textcolor{Black}{>}}\texttt{\textcolor{Black}{\ }}\textcolor{#718C00}{1}\texttt{\textcolor{Black}{;}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#57A64A}{//}}\texttt{\textcolor{#57A64A}{二分的步骤啦}} \\
    \texttt{\textcolor{Black}{\ \ \ \ \ \ \ \ }}\texttt{\textcolor{#569CD6}{if}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{Black}{c\ }}\texttt{\textcolor{Black}{-}}\texttt{\textcolor{Black}{\ b\ }}\texttt{\textcolor{Black}{<}}\texttt{\textcolor{Black}{\ a}}\texttt{\textcolor{Black}{)}} \\
    \texttt{\textcolor{Black}{\ \ \ \ \ \ \ \ \ \ \ \ l\ }}\texttt{\textcolor{Black}{=}}\texttt{\textcolor{Black}{\ c}}\texttt{\textcolor{Black}{;}} \\
    \texttt{\textcolor{Black}{\ \ \ \ \ \ \ \ }}\texttt{\textcolor{#569CD6}{else}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#569CD6}{if}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{Black}{c\ }}\texttt{\textcolor{Black}{-}}\texttt{\textcolor{Black}{\ b\ }}\texttt{\textcolor{Black}{>}}\texttt{\textcolor{Black}{\ a}}\texttt{\textcolor{Black}{)}} \\
    \texttt{\textcolor{Black}{\ \ \ \ \ \ \ \ \ \ \ \ r\ }}\texttt{\textcolor{Black}{=}}\texttt{\textcolor{Black}{\ c}}\texttt{\textcolor{Black}{;}} \\
    \texttt{\textcolor{Black}{\ \ \ \ \ \ \ \ }}\texttt{\textcolor{#569CD6}{else}} \\
    \texttt{\textcolor{Black}{\ \ \ \ \ \ \ \ \ \ \ \ }}\texttt{\textcolor{#569CD6}{return}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#F5871F}{printf}}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{#D39B83}{"\%d\verb|\|n"}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ c}}\texttt{\textcolor{Black}{)}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ }}\textcolor{#718C00}{0}\texttt{\textcolor{Black}{;}} \\
    \texttt{\textcolor{Black}{\ \ \ \ }}\texttt{\textcolor{Black}{\}}} \\
    \texttt{\textcolor{Black}{\ \ \ \ }}\texttt{\textcolor{#569CD6}{if}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{Black}{l\ }}\texttt{\textcolor{Black}{!}}\texttt{\textcolor{Black}{=}}\texttt{\textcolor{Black}{\ r}}\texttt{\textcolor{Black}{)}} \\
    \texttt{\textcolor{Black}{\ \ \ \ \ \ \ \ }}\texttt{\textcolor{#569CD6}{return}}\texttt{\textcolor{Black}{\ }}\texttt{\textcolor{#F5871F}{printf}}\texttt{\textcolor{Black}{(}}\texttt{\textcolor{#D39B83}{"\%d\verb|\|n"}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ r}}\texttt{\textcolor{Black}{)}}\texttt{\textcolor{Black}{,}}\texttt{\textcolor{Black}{\ }}\textcolor{#718C00}{0}\texttt{\textcolor{Black}{;}} \\
    \texttt{\textcolor{Black}{\}}}\end{array}
    $
    ```