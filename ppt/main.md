title: Linux常用命令行工具
speaker: 王明
transition: slide3
theme: dark

[slide]
# Linux常用命令行工具

[slide]
# 常用工具有哪些？

```bash
➜ history | awk '{print $2}' | sort | uniq -c | sort -nr
```

[slide]
# 常用工具有哪些？

`git` `cd` `rm` `cat` `find` `curl` `ls` `cp` `mv` `go` `mkdir` `subl` `vim` `touch` `echo` `mua` `http` `ping` `bower` `sudo` `npm` `nc` `sed` `brew` `grep` `history|grep` `date` `ssh` `open` `tar` `lsof` `scp` `for` `du` `fresh` `ll` `telnet` `ps` `which` `make` `dig` `gb` `(for` `node` `chmod` `export` `say` `rename` `iconv` `man`


[slide]
# 常用工具有哪些？

`nc` `find` `ls` `grep` `sed` `awk` `head` `tail` `sort` `uniq` `wc` `date` `man` `xargs` `rename` `iconv` 

[slide]
# nc

> netcat，江湖人称脑残命令

- http协议抓包
- 传输文件
- 聊天

[slide]
# `nc`命令之**http协议抓包**

- 抓包
```bash
➜  nc -l 8080
➜  curl 127.0.0.1:8080 ＃或者浏览器中访问此端口
```

- 访问网页
```bash
➜  echo "GET / HTTP/1.1\r\nHost:www.baidu.com\r\n\r\n" | nc www.baidu.com 80
```


[slide]
# `nc`命令之**传输文件**

> 同一个办公室传文件还用U盘，LOW

- 发送方
```bash
➜  nc -l 2345 < file.tar.gz
```

- 发送方
```bash
➜  nc src_ip 2345 > file.tar.gz
```

> 顺序其实无所谓


[slide]
# `nc`命令之**聊天**

> 就是这么屌

[slide]
# `ls`

```bash
➜ ls **/*.go #列举所有go 文件

➜ ls -lSr #按文件大小逆序显示

➜ ls -ltr #按更新时间逆序显示
```

[slide]
# `wc`

```bash
➜ wc -l **/*.go # 统计go代码行数
```

[slide]
# `find`

```bash
➜ find ./ -name "*.go" #当前文件夹下找go文件

# 最近7内访问过，小于2MB的所有word文档
➜ find ./ -name "*.doc" -size -2M -atime -7 
```


> 之前的两个命令在文件太多时会出错！
```bash
ls **/*.go
wc -l **/*.go
```

> 换个姿势可解决
```bash
find ./ -name "*.go"
find ./ -name "*.go"|xargs wc -l
```



[slide]
# `grep`

```bash
➜ grep　-n -A 3 -B 4 -e REGEX_PATTEN FILE_NAME # 正则匹配，并显示后3行，前4行和行号
➜ grep -v #反匹配
➜ grep -o #仅显示匹配部分
```

> 抠片神器，一键下载
[2015主打美剧《行尸走肉 第六季》更新第16集[中英双字]](http://www.dy2018.com/i/95808.html)
```bash
➜ grep -o -e 'ftp:[^"]*'
```

[slide]
# `sed`

```
➜ sed -i 's/Person/People/g' *.go
```

> 天天用，但也就是替换用的多
可以参考:[sed简明教程](http://coolshell.cn/articles/9104.html)


[slide]
# `awk`
> 光从名字看不出是什么鬼，格式化文本处理语言，比如日志

```
➜ history | awk '{print $2}' | sort | uniq -c | sort -nr
```

- 生成表格
```
cat mobiles|gawk -F '"' '{ printf("\"%s\"\t%s\n",$16,strftime("%F %T", $22/1000000000)) }'
```

[slide]
# 综合应用
> 统计手机号归属地

>`curl` `sh` `awk` `iconv` `grep` `sort` `uniq` 