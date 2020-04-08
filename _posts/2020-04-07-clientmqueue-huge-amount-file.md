---
title: /var/spool/clientmqueue 目录下大量文件
date: 2020-04-07 16:14:38
category: Linux
disqus: y
---

最近小百科 <http://xyzpedia.org> 的服务器到期了，续了费上去重启服务，怎么也启动不起来。后来发现是 /var/spool/clientmqueue 目录下有大量小文件，把 inode 耗尽了。

进 /var/spool/clientmqueue 目录多 ls 了几下，有几次是卡住，有几次提示

```
$ cd /var/spool/clientmqueue
$ ls
ls: 内存耗尽
```

试图用 rm 删除，参数太长也不行。

```
$ cd /var/spool/clientmqueue
$ rm -rf *
-bash: /bin/rm: 参数列表过长
```

## 原因分析

系统中有用户开启了 crontab，而 crontab 执行的程序有输出内容，输出内容会以邮件形式发给 crontab 的用户，而 sendmail 没有启动，所以就产生了这些文件。

事实上，我确实在 root 账号下开启了一个 crontab，用来自动监控微博的。

```shell
*/1 * * * * lynx -dump xyzpedia.org/site/cronweibo >> /root/weibo.log
```

所以这么多年，每分钟都会产生一个小文件堆在磁盘里…

## 解决办法

在 crontab 的自动执行语句后加上`> /dev/null 2>&1`

例如：

```shell
4 3 * * * /usr/bin/w > /dev/null 2>&1
```

然后，为了避免直接 rm 参数列表过长的问题，用如下命令删除 /var/spool/clientmqueue 目录里的文件

```shell
ls /var/spool/clientmqueue | xargs -I '{}' rm -f '{}'
```

这是把 ls 的输出通过管道的形式，通过内存缓存传递给了 rm，等几分钟，即可成功删除。

