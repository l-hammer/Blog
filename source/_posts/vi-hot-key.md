---
title: 🛠VIM常用操作笔记
lang: zh-CN
direction: ltl
date: 2017.08.12 20:29:29
tags:
  - vim
---

![](https://images-cdn.shimo.im/OuPlkXGqRHUXSvv7/vi-vim-cheat-sheet-sch.gif!thumbnail)

vi === vim
g === global
':'    表示命令模式下输入
Vi 语

动词：表示我们将要进行什么操作
d === delete    # → 表示删除
r === replace    # → 表示替换
c === change    # → 表示修改
y === yank    # → 表示复制
v === visual select    # → 表示选取
名词：表示我们将要处理的文本
w === word    # → 表示一个单词
s === sentence    # → 表示一个句子
p === paragraph    # → 表示一个段落
t === tag    # → 表示一个HTML标签
介词：界定了待编辑文本的范围或者位置
i === inside    # → 表示“在...之内”
a === around    # → 表示“环绕...”
t === to    # → 表示“到...位置前”
f ===forward    # → 表示“到...位置上”

数词：指定了待编辑文本对象的数量或执行操作的次数
c3w === change three words    # → 修改三个单词
d2w === delete two words    # → 删除两个单词
2dw === twice delete word    # → 两次删除单词
3x === three times delete character    # → 三次删除字符
组词：动词+介词+名词
dip === delete inside paragraph    # → 删除一个段落:
vis === visual select inside sentence    # → 选取一个句子  
ciw === change inside word    # → 修改一个单词
caw === change around word    # → 修改一个单词
dtx === delete to x    # → 删除文本直到字符“x”（不包括字符“x”)
dfx === delete forward x    # → 删除文本直到字符“x”（包括字符“x”)

常用快捷键

启动vi
$ vim
vi常见模式
正常模式：又称命令模式，可以使用快捷键命令，或按:输入命令行。
插入模式：可以输入文本，在正常模式下，按i、a、o等都可以进入插入模式。
可视模式：正常模式下按v可以进入可视模式， 在可视模式下，移动光标可以选择文本。按V进入可视行模式， 总是整行整行的选中。ctrl+v进入可视块模式。
替换模式：正常模式下，按R进入。
打开文件
vi filea  # → 打开文件filea，光标默认在第一行
vi + filea  # → 打开文件filea，并将光标定位到最后一行
vi +8/n filea  # → 打开文件filea，并将光标定位到第8/n行 
vi +/xxx filea  # → 打开文件filea，并将光标定位到xxx第一次出现的位置
vi filea fileb filec  # → 同时打开文件filea，fileb，filec
:n(next)  # → 切换下一个文件
:N(prev)  # → 切换上一个文件  
折叠打开
zi  # → 关闭/打开折叠
zc  # → 折叠
zC/zR  # → 对所在范围内所有嵌套的折叠点进行折叠
zo  # → 展开折叠
zO/zM  # → 对所在范围内所有嵌套的折叠点展开
打开目录
:Ex <clipname>  # → 打开当前文件所在目录或指定目录
:Se <clipname>  # → 上下分割并打开当前目录或指定目录
:Ve <clipname>  # → 左右分割并打开当前目录或指定目录
:Te <clipname>  # → 新建标签并打开当前目录或指定目录
注：打开目录之后可通过移动光标打开相应文件，常用操作如下：
enter  # → 回车会在当前窗口打开光标所在文件,即目录会被关闭
:p  # → 在预览窗口打开光标所在文件
:pclose  # → 关闭预览串口
:o  # → 在新浏览窗口打开光标所在文件，使用上下分割
:t  # → 在新标签页里打开光标所在文件(推荐)
替换
% s/old/new/  # → 替换当前行第一个old
% s/old/new/g  # → 替换当前行所有old
8，29 s/old/new/g  # → 替换8-29行出现的所有old
1，$ s/old/new/g  # → 替换整个文件中出现的所有old，等价于 % s/old/new/g
g/string/s//new/g  # → 查找并替换，也等价于 % s/old/new/g
gU  # → 将选定范围全部大写
gu  # → 将选定范围全部小写
gUw/gUe  # → 将光标所在位置的单词转为大写
guw/gue  # → 将光标所在位置的单词转为小写
查找
/<search>  # → 向后查找指定字符串
?<search>  # → 向后查找指定字符串
n  # → 查找下一个
N  # → 查找上一个
移动
h  # → 向左一字符
j  # → 下一行
k  # → 上一行
l  # → 向右一字符
w or W  # → 向右移动到下一单词开头
e or E  # → 向右移动到单词结尾
b or B  # → 向左移动到单词开头
gg  # → 到文档第一行
G  # → 到文档最后一行
0  # → 到行首（第 1 列）
^  # → 到第一个非空白字符
$  # → 到行尾
:<N> or <N>gg  # → 跳转到第 N 行
:+<N> or <N>j  # → 向下跳 N 行
:-<N> or <N>k  # → 向上跳 N 行
翻屏
Ctrl-d  # → 向下移动半页
Ctrl-u  # → 向上移动半页
Ctrl-f  # → 向下移动一页
Ctrl-b  # → 向上移动一页
插入
i  # → 当前字符前插入
a  # → 当前字符后插入
I  # → 行首插入
A  # → 行尾插入
o  # → 在下一行插入
O  # → 在上一行插入
注：以上任何一个命令都会使 vim 进入 insert 模式

删除
x  # → 删除当前字符，相当于 insert 模式下的 Delete
X  # → 删除前一个字符，相当于 insert 模式下的 Backspace
D  # → 删除到行尾
dd  # → 删除当前行，并将删除的内容保存到 vim 剪贴板
ndd  # → 删除从当前行开始的n行
de or dw  # → 删除一个单词/光标之后的单词剩余部分
d<X>  # → 删除指定内容并保存到 vim 剪贴板
c<X>  # → 删除指定内容并保存到 vim 剪贴板，同时进入 insert 模式
8,29 de  # → 删除8-29行
复制
yy  # → 复制当前行到 vim 剪贴板
nyy  # → 复制光标以下的n行到 vim 剪贴板
y<X>  # → 复制指定内容到 vim 剪贴板
:9，15 co 16  # → 将9~15行内容复制到第16行（文件内复制推荐）
粘贴
p  # → 在当前位置后粘贴
P  # → 在当前位置前粘贴
合并/撤销/重做
J  # → 将当前行与下一行合并
u  # → 撤销
ctrl r  # → 重做
保存
:w  # → 保存当前文件
:q!  # → 退出
:wq!  # → 保存并退出
:wa  # → 保存全部文件
:saveas <new filename>
行号
set nu or set number  # → 显示行号
set nonu or set nonumber  # → 隐藏行号
注释
:8,29 s#^#//#g  # → 在8到29行添加‘//'注释
:8,29 s#^//##g  # → 在8到29行删除'//'注释
:8,29 s/^/#/g  # → 在8到29行添加‘#'注释
:8,29 s/^#//g  # → 在8到29行删除'#'注释
:8,29 s/^/<!--/g  # → 在8到29行开头添加'<!--'注释
:8,29 s/^/-->/g  # → 在8到29行结尾添加'-->'注释
:8,29 s/^<!--//g  # → 在8到29行开头删除'<!--'注释
:8,29 s/^/<!--/g  # → 在8到29行结尾删除'-->'注释
注：如果匹配'//'那么使用'#'作为分割符这样不需要对‘//'做转义处理

分屏
:sp(split)  # → 上下分屏
:vs(vsplit)  # → 左右分屏
ctrl w w  # → 激活下一个窗口
标签页(NERDTree)
:tabe <new filename>  # → 打开新标签页
gt or tabn(tabnext)  # → 切换下一个标签页
gT or tabp(tabprevious)  # → 切换上一个标签页
:tabr(tabrewind) or tabfi(tabfirst)  # → 切换到第一个标签页
:tabl(tablast)  # → 切换到最后一个标签页
:tabc(tabclose)  # → 关闭当前标签页
:tabo(tabonly)  # → 关闭其他标签页
:tabs  # → 查看buffer list
块操作
<n>gg  # → 跳转光标到起始行
ctrl v   # → 进入快操作模式
j  # → 移动光标到需要编辑的相同位置
A/I  # → 开始在字符后/前插入指定内容,按esc退出块模式即可完成操作
<n>gg$x  # → 删除指定行末尾的字符
vi中的宏
qx  # → 开始录制宏，x为a到z或0~9的任意字符 
q  # → 终止录制宏 
@x  # → 调用先前录制的宏
小技巧
.  # → 重复执行上一个命令
>>  # → 向右自动缩进（结合块模式使用可进行多行缩进）
<<  # → 向左自动缩进（结合块模式使用可进行多行缩进）
=  # → 自动排版当前选中代码
gg=G  # → 对整个文件进行排版
:f  # → 显示vim当前的文件路径
:pwd  # → 显示vim的工作目录
:set ff  # → 显示当前文件的格式
NERDTree
o  # → 打开一个目录或者打开文件，创建的是buffer，也可以用来打开书签
go  # → 打开一个文件，但是光标仍然留在NERDTree，创建的是buffer
t  # → 打开一个文件，创建的是Tab，对书签同样生效
T  # → 打开一个文件，但是光标仍然留在NERDTree，创建的是Tab，对书签同样生效
i  # → 水平分割创建文件的窗口，创建的是buffer
gi  # → 水平分割创建文件的窗口，但是光标仍然留在NERDTree
s  # → 垂直分割创建文件的窗口，创建的是buffer
gs  # → 和gi，go类似
x  # → 收起当前打开的目录
X  # → 收起所有打开的目录
e  # → 以文件管理的方式打开选中的目录
D  # → 删除书签
P  # → 大写，跳转到当前根路径
p  # → 小写，跳转到光标所在的上一级路径
K  # → 跳转到第一个子路径
J  # → 跳转到最后一个子路径
<C-j>和<C-k>  # → 在同级目录和文件间移动，忽略子目录和子文件
C  # → 将根路径设置为光标所在的目录
u  # → 设置上级目录为根路径
U  # → 设置上级目录为跟路径，但是维持原来目录打开的状态
r  # → 刷新光标所在的目录
R  # → 刷新当前根路径
m  # → 显示文件系统菜单 
cd  # → 将 CWD 设为选中目录
F  # → 切换是否显示文件
B  # → 切换是否显示书签
I  # → 显示或者不显示隐藏文件
f  # → 打开和关闭文件过滤器
q  # → 关闭NERDTree
A  # → 全屏显示NERDTree，或者关闭全屏
Airline
Ctrl-N  # → 切换下一个buffer
Ctrl-P  # → 切换前一个buffer
:ls  # → 查看buffer list
:bd  # → 关闭当前buffer
:b n  # → 切换buffer，n为buffer序号
vim-multiple-cursors
Ctrl-n  # → 连续选中光标所在单词的下一个
Shift-i  # → 进入块插入模式



更新中……

附：VIM键位图
