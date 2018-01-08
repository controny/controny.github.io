---
layout: post
title:  "vi常用命令之修改文本"
tag:
- vi
- Linux
comments: true
---

vi编辑器拥有众多命令，可以按如下方式分为三类：

* 移动光标的命令
* 进入输入模式的命令
* 进行修改的命令

这里记录常用的第三类命令。

## 简单替换

* r：替换一个字符
* R：替换多个字符
* s：以插入方式替换一个字符
* C：以插入方式从当前光标替换到行尾
* S或cc：以插入方式替换整行
* c[*move*]：以插入方式从当前光标替换到[*move*]给出的位置（如`cw`可以向后替换一个单词，因为`w`使光标移动到下一个单词词首）

## 复杂替换

* **:s**/*pattern*/*replace*/：替换当前行
* **:**_line_**s**/*pattern*/*replace*/：替换指定行
* **:**_line_,_line_**s**/*pattern*/*replace*/：替换指定范围的行
* **:%s**/*pattern*/*replace*/：替换所有行

其中，*pattern*是替换的正则表达式匹配模式，*replace*是要替换的文本，*line*是行号。  
此外，该命令有几个注意事项：

1. 为了删除特定项，只需将替换文本留空，如删除`root`为**：s/root//**。
2. 以上命令默认只匹配每一行的第一项，在命令末尾加上**g**（global）可匹配所有项。
3. 在命令末尾加上**c**（confirm）可使vi在改变每一项前发出确认提示。
4. 可用**.**代表当前行，**$**代表文本最后一行。

## 删除文本

* x：删除当前光标位置的字符
* X：删除当前光标位置前的字符
* D：删除从当前光标位置到行尾的所有字符
* d[*move*]：删除从当前光标位置到[*move*]所给位置的字符（用法同c[*move*]）
* dd：删除当前行
* **:**_line_**d**：删除指定行
* **:**_line_,_line_**d**：删除指定范围的行

## 复制文本

主要有**y**和**yy**两个命令，用法与**d**和**dd**相同。

## 粘贴

* p：插入到光标后
* P：插入到光标前

两者不仅可插入复制的文本，也可插入刚被删除的文本，充当剪切-粘贴的用途。