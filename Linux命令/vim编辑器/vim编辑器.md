# 模式介绍

vim编辑器有3种模式，分别是一般模式、编辑模式、末行指令模式。打开一个文件时，默认一般模式，编辑模式不能直接转换到末行指令模式。

**一般模式：** 移动光标，复制、粘贴、删除。

**编辑模式：** 输入文字

**末行指令模式：** 一般模式中，按`":" "/" "?"`，会在最后一行出现相应的符号。

# 基本使用

- `i`键进入编辑模式；`Ecs`退出编辑模式。
- `yy`复制当前行，`p`粘贴到下一行。
- `dd`删除当前行。
- `dw`删除当前词，`x`向后删除一个字符，`X`向前删除一个字符。
- `u`撤销；`Ctrl+r`重做。
- `:wq`保存退出，可以使用`:x`替代。
- `:n`移动到第n行。
- `n`往下移动n行。
- `$`移动到本行末尾。
- `G`移动到文件末尾。
- `Ctrl+f`向下一页，`Ctrl+b`向上一页；`Ctrl+d`向下半页，`Ctrl+u`向上半页。

# 搜索和替换

- /word向下搜索，n下一个，N上一个。
- ?word向上搜索，n上一个，N下一个。
- `:n1,n2s/word1/word2/g`，将n1到n2行之间的所有word1替换成word2。
- `:1,$s/word1/word2/g`，将第1行到最后一行的进行替换。
- `:s/word1/word2/g`，将本行的word1替换成word2。
- `:s/word1/word2`，将本行第一个出现的word1替换成word2。

