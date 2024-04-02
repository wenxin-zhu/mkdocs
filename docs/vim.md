# vim

vim个人常用命令

1.   必要的

```bash
vim filename # 使用vim编辑文件（不存在会创建）
i # 进入insert模式（normal）
Esc # 返回normal模式（insert）
ctrl+shift+v # 粘贴（insert）
:wq # 保存并退出（normal）
:q # 不保存直接退出（normal）
:q! # 不保存强制退出（normal）
:w # 保存但不退出
```

2.   高效的

```bash
G # 调到最后一行（normal）
o # 在光标所在行的下插入新的一行（normal）与G配合实现文档尾部添加!

ctrl + d # 向下翻半屏（normal）
行号+G # 快速定位光标到指定行（normal）
gg # 调到首行（normal）
ctrl + u # 向上翻半屏（normal）

dd # 剪切（删除）（normal）
p # 粘贴（normal）
yy # 复制（normal）
u # 撤销（normal）
crtl+r # 重做（normal）

/内容 # 搜索内容
N/n # 在搜索结果中切换上/下一个结果

:s/要替换的关键词/替换后的关键词# 只替换光标所在这一行的第一个满足条件的结果
:%s/要替换的关键词/替换后的关键词/g # 替换全部的关键词

:set nu # 显示行号
:set nonu # 隐藏行号

# 复制多行操作
# 第一步：在命令模式下，直接按小v，进入可视化模式
# 第二步：使用方向键↑ ↓ ← →选择要复制的内容，然后按y键
# 第三步：移动光标，停在需要粘贴的位置，按p键进行粘贴操作
```

# 模式


### 插入模式

| i    | 光标前插入( insert)        |
| ---- | -------------------------- |
| I    | 在行首插入                 |
| a    | 在光标前插入(append)       |
| A    | 在行尾插入                 |
| o    | 在下一行插入(one line)     |
| O    | 在上一行插入               |
| ESC  | jj	Capslok 退出插入模式 |

### 可视模式

| v        | 进入 |
| -------- | ---- |
| ESC	v | 退出 |

### 命令模式

： 进入

ESC 退出



# 光标移动

普通模式下：

h ←	j ↓	k ↑	l →

| w    | 跳到下一个单词开头(word)         |
| ---- | :------------------------------- |
| b    | 跳到本单词或下一个单词结尾(back) |
| e    | 跳到本单词或上一个单词开头(end)  |
| ge   | 跳到上一个单词结尾               |
| 0    | 跳到行首                         |
| ^    | 跳到从行首开始第一个非空字符     |
| $    | 跳到行尾                         |
| gg   | 跳到第一行                       |
| G    | 跳到最后一行                     |



![image-20220203144707592](https://zwx-pic.oss-cn-beijing.aliyuncs.com/img/01b485d5d0a109664019ee84c7e0370b.png) 

# 操作符

![image-20220203145538127](https://zwx-pic.oss-cn-beijing.aliyuncs.com/img/af4ca98a31f2f538109af9a10b4863ec.png) 

# 操作符+动作

| p            | 粘贴                             |
| ------------ | -------------------------------- |
| u            | 撤销动作+操作符                  |
| ciw          | 选中单词删除并进入插入模式       |
| yiw          | 选中并复制单词                   |
| diw          | 选中并删除单词                   |
| ndd/ncc/nyy  | 向下删除/修改/复制n行,包括当前行 |
| d/c/yf{char} | 删除/修改/复制到向后的char字符   |
| d/c/y ^/$    | 删除/修改/复制到开头/结尾        |
| die          | 删除整个文件                     |
| cie          | 删除整个文件并进入写入模式       |

v+各种操作（可以看到啥被选中了）+操作符（y/c/d）

# 大小写转换

<img src="https://zwx-pic.oss-cn-beijing.aliyuncs.com/img/3a6cb9f53dde063073ae57117d3daa80.png" alt="image-20220203155235967" style="zoom: 50%;" /> 

