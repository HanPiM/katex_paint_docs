# 附 A - 讨论区无法使用的命令

  讨论区的 LaTeX 版本与剪贴板和博客不同。请注意以下：
  
  - 宏定义类
    
    包括但不限于 `\def \newcommand...`
    
    均无法使用。
    
  - 换行类
    
    `\\ \cr \newline`
    
    无法直接使用，但可在 `array gathered` 等排版环境下使用
    
  - 其他
    
    `\char` : 无法使用