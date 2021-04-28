# sed介绍

sed（stream editor）是一种非交互式的流编辑器，通过多种转换修改流经它的文本。

默认情况下，sed并不会改变原文件本身，而只是对流经sed命令的文本进行修改，并将修改后的结果打印到标准输出中（也就是屏幕）。

sed处理文本时是以行为单位的，每处理完一行就立即打印出来，然后再处理下一行，直至全文处理结束。

sed可做的编辑动作包括删除、查找替换、添加、插入、从其他文件中读入数据等。

**使用场景：**

1. 常规编辑器编辑困难的文本。
2. 太过于庞大的文本，使用常规编辑器难以胜任（比如说vi一个几百兆的文件）。
3. 有规律的文本修改，加快文本处理速度（比如说全文替换）。

```shell
# 数据准备
$ cat sed.txt
this is line 1, this is First line
this is line 2, the Second line, Empty line followed

this is line 4, this is Third line
this is line 5, this is Fifth line

# 用法
# command 25个sed命令集
# -e 选项连接多个命令
$ sed [options] 'command' file

# -e 示例
# 替换 this -> That
# 替换 line -> LINE
$ sed -e 's/this/That/g' -e 's/line/LINE/g' sed.txt
That is LINE 1, That is First LINE
That is LINE 2, the Second LINE, Empty LINE followed

That is LINE 4, That is Third LINE
That is LINE 5, That is Fifth LINE
```



# 删除

```shell
# d命令可以删除指定的行
# 删除第一行
$ sed '1d' set.txt

# -i 原地修改
$ sed -i '1d' file

# 范围删除
$ sed '1,3d' sed.txt

# 到最后一行
$ sed '1,$d' sed.txt

# 删除最后一行
$ sed '$d' sed.txt

# 删除指定范围以外的行
$ sed '5!d' sed.txt

# 删除所有包含Empty的行
$ sed '/Empty/d' sed.txt

# 删除空行
$ sed '/^$/d' sed.txt
```



# 查找替换

```shell
# 默认只替换第一项（每一行第一个）
$ sed 's/line/LINE/' sed.txt

# 替换第二个
$ sed 's/line/LINE/2' sed.txt

# 全部替换
$ sed 's/line/LINE/g' sed.txt

# 替换开头的this为that
$ sed 's/^this/that/' sed.txt
```



# 字符转换

```shell
# y命令，将一系列字符逐个映射为另一系列字符
$ sed 'y/OLD/NEW/' file

$ sed 'y/123/ABCD/' sed.txt
```



# 插入文本

```sh
# i或a命令插入文本，i在匹配行之前插入，a在之后
$ sed '2 i Insert' sed.txt
$ sed '2 a Insert' sed.txt
```



# 读入文本

```sh
# r命令可以从其他文件读取文本，并插入匹配行之后
$ sed '/^$/r /etc/passwd' sed.txt
```



# 打印

```shell
# p命令，打印
# -n选项，不打印没关系的行
$ sed -n '1p' sed.txt

$ sed -n 's/the/THE/p' sed.txt
```



# 写文件

```shell
# 1. 重定向
# 2. -i 选项
# 3. w命令保存为指定外部文件
$ sed -n '1,2 w output' sed.txt
$ cat output
```



# sed脚本

```shell
$ cat sed.rules
s/this/THAT/g
/^$/d

# -f选项，指定脚本
$ sed -f sed.rules sed.txt
```



# 高级替换

# sed总结

