# 附 B - 其他样例

!!! tip ""
    切换至日间模式以获得更好的显示效果

这里是一些综合运用的样例

### 提示框

其实是复刻 [Collapsible Blocks](https://squidfunk.github.io/mkdocs-material/reference/admonitions/#removing-the-title) 。

=== "演示"
    --8<-- "examples/appendix/B_note.txt"

=== "源码"
    ```latex
    --8<-- "examples/appendix/B_note.txt"
    ```

### 伪窗口

=== "演示"
    --8<-- "examples/appendix/B_fakewin.txt"

=== "源码"
    ```latex
    --8<-- "examples/appendix/B_fakewin.txt"
    ```

### 心形曲线

=== "演示"

    --8<-- "examples/appendix/B_heart.txt"

=== "源码"
    ```latex
    --8<-- "examples/appendix/B_heart.txt"
    ```

心形部分代码由 [生成器（已停止更新）](https://github.com/HanPiM/katex_complex_img_generator) 制作。

### €€￡ Logo

=== "演示"

    --8<-- "examples/appendix/B_CCFlogo.txt"

=== "源码"
    ```latex
    --8<-- "examples/appendix/B_CCFlogo.txt"
    ```

!!! note ""
    ~~为了防止被 D，说一下，~~ €€￡团里那个就是我画的：[洛谷-画了个协会标志](https://www.luogu.com.cn/discuss/415288)

### 像素画 - 钟

=== "演示"

    --8<-- "examples/appendix/B_MCbell.txt"

=== "源码"
    ```latex
    --8<-- "examples/appendix/B_MCbell.txt"
    ```

```py title="生成器"
from PIL import Image

# 用于生成简单的图片的 KaTeX 表达方式（长*宽必须小于 234，大于会导致渲染失败）
path=input("图片路径: ")

img=Image.open(path)
img.convert('RGB')
data=img.getdata()
w=img.size[0]
h=img.size[1]

def hex_col(pos):
    return '#'+format(data[pos][0],'x').zfill(2)+format(data[pos][1],'x').zfill(2)+format(data[pos][2],'x').zfill(2)
    
bitw=float(input('每像素大小（mm）: '))

print(
        "$\\newcommand{\\x}{0}\\newcommand{\\bitsize}{"+str(bitw)+
        "mm}\\newcommand{\\b}[1]{\\color{#1}\\rule[-\\x mm]{\\bitsize}{\\bitsize}}\\newcommand{\\bw}{\\bitsize}\\newcommand {\\w}{"+
        str(bitw*w)+
        "mm}\\newcommand{\\rx}[1]{\\renewcommand{\\x}{#1}}\\newcommand{\\k}{\kern{-\\w}}")
res=''
cnt=0
for i in range(w*h):
    res+='\\b{'+hex_col(i)+'}'
    cnt+=1
    if((i+1)%w==0):
        res+='\\k\\rx{'+str(round((i//w)*bitw,1))+'}'
res+='$'

print(res)
```