---
title: 'Linux Shell指令'
date: '2021-12-11 02:30:00'
update: '2021-12-11 02:30:00'
description: '操作系统实验考试必备'
keywords: 'Linux'
categories: '知识'
top_img: https://images.weserv.nl/?url=https://article.biliimg.com/bfs/article/de1c94bac8cc0bfad5fd6b6de3c6e6d024cbf2af.jpg
cover: https://images.weserv.nl/?url=https://article.biliimg.com/bfs/article/de1c94bac8cc0bfad5fd6b6de3c6e6d024cbf2af.jpg
---

## Ubuntu安装和卸载应用程序

```shell
sudo apt install softwareName
sudo apt remove softwareName
```

```shell
#Eaxmple:
sudo apt install gcc
sudo apt remove vim
```





---





## 基础命令

### 1. ls

作用：显示当前目录下的所有文件

**参数：**

- `-a` 显示所有文件及目录 (**.** 开头的隐藏文件也会列出)
- `-l` 除文件名称外，亦将文件型态、权限、拥有者、文件大小等资讯详细列出
- `-r` 将文件以相反次序显示(原定依英文字母次序)
- `-t` 将文件依建立时间之先后次序列出
- `-F` 在列出的文件名称后加一符号；例如可执行档则加 “*”, 目录则加 “/”
- `-R` 若目录下有文件，则以下之文件亦皆依序列出



### 2. cd

作用：切换目录

```shell
cd .. #返回到上一层
cd ~ #返回到根目录
```



### 3. mkdir

作用：建立文件夹

**参数: **`-p`命令创建递归目录

```shell
mkdir -p 111/222/333/444/555
```



### 4. rm

作用：删除

**参数：**

- `-f`：强制删除（force），和 -i 选项相反，使用 -f，系统将不再询问，而是直接删除目标文件或目录。
- `-i`：在删除文件或目录之前，系统会给出提示信息，使用 -i 可以有效防止不小心删除有用的文件或目录。
- `-r`：递归删除，主要用于删除目录，可删除指定目录及包含的所有内容，包括所有的子目录和文件。



### 5.cp

作用：复制文件或目录

**参数：**

- `-a`：此选项通常在复制目录时使用，它保留链接、文件属性，并复制目录下的所有内容。其作用等于dpR参数组合。
- `-d`：复制时保留链接。这里所说的链接相当于 Windows 系统中的快捷方式。
- `-f`：覆盖已经存在的目标文件而不给出提示。
- `-i`：与 **-f** 选项相反，在覆盖目标文件之前给出提示，要求用户确认是否覆盖，回答 **y** 时目标文件将被覆盖。
- `-p`：除复制文件的内容外，还把修改时间和访问权限也复制到新文件中。
- `-r`：若给出的源文件是一个目录文件，此时将复制该目录下所有的子目录和文件。
- `-l`：不复制文件，只是生成链接文件。



### 6. mv

作用：移动或重命名

**参数：**

- `-b`: 当目标文件或目录存在时，在执行覆盖前，会为其创建一个备份。
- `-i`: 如果指定移动的源目录或文件与目标的目录或文件同名，则会先询问是否覆盖旧文件，输入 y 表示直接覆盖，输入 n 表示取消该操作。
- `-f`: 如果指定移动的源目录或文件与目标的目录或文件同名，不会询问，直接覆盖旧文件。
- `-n`: 不要覆盖任何已存在的文件或目录。
- `-u`：当源文件比目标文件新或者目标文件不存在时，才执行移动操作。



### 7. chmod

作用：更改文件或文件夹权限

|   权限类型    |  值  |
| :-----------: | :--: |
| 读取权限（r） |  4   |
| 写入权限（w） |  2   |
| 执行权限（x） |  1   |

依次是：文件所有者(Owner)，用户组(Group)，其它用户(Other Users)，将赋予的值相加

```shell
#使用ls -l查看当前目录下文件文件夹和它们的权限
chmod 731 example.c
#将example.c权限改为文件所有者rwx，用户组-wx，其它用户--x
```



### 8. touch

作用：创建新的空白文件或者更改现有文件和目录上的时间戳（`touch`命令会创建一个原来没有的文件（注意不是文件夹），如果文件存在，`touch`命令会将该文件的上次访问时间和修改时间更改为当前时间。）

**参数：**

- `-a`选项更改文件的访问时间为当前时间
- `-m`选项更改文件的修改时间为当前时间
- `-d`选项指定日期字符串，并使用它代替当前时间

```shell
#一次创建多个文件或者修改多个文件的时间戳
touch file1.txt file2.txt file3.txt
```





---





## Linux脚本基础操作

### 1. vim

作用：使用vim创建并编辑一个文件

```shell
vim example.sh # .sh shell脚本文件
```

创建文件并进入vim后，按下 `i` 或 [insert] 才可开始编辑

按下 [esc] 退出编辑，输入 `:wq` 保存退出，输入 `:q` 不保存退出



### 2. cat

作用：查看文本文件内容

**参数：**

- `-n`：由 1 开始对所有输出的行数编号。
- `-b`：和 -n 相似，只不过对于空白行不编号。
- `-s`：当遇到有连续两行以上的空白行，就代换为一行的空白行。
- `-v`：使用 `^` 和 `M-` 符号，除了 `LFD` 和 `TAB` 之外。
- -v : 在每行结束处显示 `$`。
- -t: 将 TAB 字符显示为 `^I`。
- `-A`：等价于 `-vET`。



### 3. bash

作用：运行.sh脚本

```shell
bash example.sh
```





---





## .sh 脚本

### 1. echo

作用：输出（`printf`）

```sh
echo #输出空白行
echo "hello world" #输出指定字符串
echo $HOSTNAME #输出变量HOSTNAME对应的值
echo "hello world" > 1.txt #输出字符串到指定文件
echo `date` #输出日期
```



### 2. Shell Variable变量

**一些特殊的变量，用户不能重新定义：**

![](https://images.weserv.nl/?url=https://article.biliimg.com/bfs/article/117087213e96c82cc6a503008ff90749d52cb77f.png)

**用户可以自定义的变量的要求：**

1. 使用变量无需提前声明
2. 首个字符必须为字母
3. 变量名里不得有空格，可以使用下划线 `_`
4. 不得使用标点符号或bash中的关键字



**用`echo`输出变量时，使用`${ }`将变量名框住**

```sh
#例：
eaxmple=hello #等号两边不得有空格
echo ${example}World
#输出：
helloWorld
```



**`${ }` 的特殊功能：** 

`${varName:Number}`

若Number为正数，Number从 0 开始，表示在变量中提取第Number个字符到末尾的所有字符 。若Number为负数，提取字符串最后面Number的绝对值个字符，使用时在冒号后面加空格或一个算术表达式或整个 num 加上括号，如`${varexam: -2} #注意冒号后加一个空格`  ，`${varexam:1-3}`，`${varexam:(-2)}`均表示提取最后两个字符

![](https://images.weserv.nl/?url=https://article.biliimg.com/bfs/article/29919d814279bb951012b7eda17fcb1bffd9dbb6.jpg)





### 3. File Operator文件操作

|          Operator          |                       Meaning                        |
| :------------------------: | :--------------------------------------------------: |
|        -e $fileName        |                   检测文件是否存在                   |
|        -f $fileName        | 检测文件是否是普通文件（既不是目录，也不是设备文件） |
|        -d $fileName        |                    检测是否是目录                    |
|        -c $fileName        |                检测是否是字符设备文件                |
|        -r $fileName        |                   检测文件是否可读                   |
|        -w $fileName        |                   检测文件是否可写                   |
|        -x $fileName        |                  检测文件是否可执行                  |
|        -s $fileName        |           检测文件是否为空（文件大小为0）            |
| $fileName1 -nt  $fileName2 |            判断fileName1是否比fileName2新            |
| $fileName -ot  $fileName2  |            判断fileName1是否比fileName2旧            |

![](https://images.weserv.nl/?url=https://article.biliimg.com/bfs/article/a9e50a6a4c4fb32e9a6f1ccb090a504dbf02d43e.png)





---

**未完待续**

---