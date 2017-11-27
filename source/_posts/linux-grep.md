---
title: linux grep
date: 2017-10-18 17:19:28
tags: grep,linux
---

grep的常规用法

| 参数     |含义     |
| --- | --- |
| -A `num`,--after-context=`num`    | 显示匹配行的后面`num`行     |
| -B `num`,--before-context=`num`    |显示匹配行的前面`num`行     |
| -i    |忽略大小写匹配     |
| -w    |整个单词匹配     |
| -n    |显示匹配行行号，行号从1开始，如果带有-c -L -l -q参数，该参数将被忽略      |
| -c    |输出匹配行行数|
| -v    |显示不匹配字符串文本的所有行|
| -o    |只输出匹配部分|

- 匹配包含特定字符串的行

```bash?linenums
root@fchen:/# grep root /etc/passwd
root:x:0:0:root:/root:/bin/bash
```

- 查找不包含特定字符串的行

```bash?linenums
root@fchen:/# cat data.csv # 查看data.csv数据
abc
bcd
aaa
root@fchen:/# grep -v aaa data.csv
abc
bcd

```

- 匹配所有以t/T开头的行

```shell?linenums
root@fchen:/# cat /tmp/regular_express.txt
"Open Source" is a good mechanism to develop programs.
apple is my favorite food.
Football game is not use feet only.
this dress doesn't fit me.
However, this dress is about $ 3183 dollars.
GNU is free air not free beer.
Her hair is very beauty.
I can't finish the test.
Oh! The soup taste good.
motorcycle is cheap than car.
This window is clear.
the symbol '*' is represented as start.
Oh!     My god!
The gd software is a library for drafting programs.
You are the best is mean you are the no. 1.
The world <Happy> is the same with "glad".
I like dog.
google is the best tools for search keyword.
goooooogle yes!
go! go! Let's go.
# I am VBird
root@fchen:/#
root@fchen:/#
root@fchen:/# grep -i  "^t" /tmp/regular_express.txt
this dress doesn't fit me.
This window is clear.
the symbol '*' is represented as start.
The gd software is a library for drafting programs.
The world <Happy> is the same with "glad".

```

- 匹配不包含is和are的行

```shell?linenums
root@fchen:/# grep -v -e "is" -e "are" /tmp/regular_express.txt
Oh! The soup taste good.
Oh!     My god!
I like dog.
goooooogle yes!
go! go! Let's go.
# I am VBird
```
- 输出包含`is`单词的行数

```shell?linenums
root@fchen:/# grep -c -w is /tmp/regular_express.txt
13
```

- 与`tail`配合使用
 
![grep with tail](./1.gif)



