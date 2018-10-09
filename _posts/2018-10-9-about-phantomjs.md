# 总结一下最近在使用网页截图库phantomjs遇到的问题
## phantomjs简介
Phantomjs是一个软件，是一个webkit的内核。其实就是一个npm的库。用它在服务器端对一个网页进行
截图是非常的方便。
## 遇到的问题
在centos上面安装phantomjs成功后，使用shell命令行进行调用，传递的参数过程中，网页的query string
中有&关键字，这个在shell命令行是一个运算符，居然栽在此处，花了我不少时间
## PHP调用phantomjs的问题
使用网页走PHP调用phantomjs命令行，发现exec函数的返回值是127，后来才明白是权限问题，nginx的用户组没有
执行phantomjs的权限。
## 使用crontab进行定时任务模式
*/1 * * * * cd XXX && /usr/bin/php crontab.php
上面是命令行，记得先cd进目录下面，还有，所有的命令行要记得使用绝对路径，包括phantomjs
/usr/local/bin/phantomjs 
路径原因耽搁了好久，后来通过查看crontab的日志才找到原因：
cd /var/log 然后 tail -n 100 cron来进行查看输出的日志。


