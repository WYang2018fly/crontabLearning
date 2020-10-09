# crontabLearning
## 一、Linux Crontab

> base on ubuntu in docker 

### 1.crontab command line

- 通过编辑器来设定时程表（默认vi）

```bash
crontab -e
```

```bash
# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').
#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command

# 每分钟修改一次根目录下的updatedAt.txt
*/1 * * * * touch /updatedAt.txt
```

- result

```bash
root@e79f84fdc37f:/# ls -al
total 68K
drwxr-xr-x   1 root root 4.0K Oct  9 06:44 .
drwxr-xr-x   1 root root 4.0K Oct  9 06:44 ..
-rwxr-xr-x   1 root root    0 Oct  9 06:05 .dockerenv
lrwxrwxrwx   1 root root    7 Sep 25 01:20 bin -> usr/bin
drwxr-xr-x   2 root root 4.0K Apr 15 11:09 boot
drwxr-xr-x   5 root root  360 Oct  9 06:22 dev
drwxr-xr-x   1 root root 4.0K Oct  9 06:41 etc
drwxr-xr-x   2 root root 4.0K Apr 15 11:09 home
lrwxrwxrwx   1 root root    7 Sep 25 01:20 lib -> usr/lib
lrwxrwxrwx   1 root root    9 Sep 25 01:20 lib32 -> usr/lib32
lrwxrwxrwx   1 root root    9 Sep 25 01:20 lib64 -> usr/lib64
lrwxrwxrwx   1 root root   10 Sep 25 01:20 libx32 -> usr/libx32
drwxr-xr-x   2 root root 4.0K Sep 25 01:20 media
drwxr-xr-x   2 root root 4.0K Sep 25 01:20 mnt
drwxr-xr-x   2 root root 4.0K Sep 25 01:20 opt
dr-xr-xr-x 136 root root    0 Oct  9 06:22 proc
drwx------   1 root root 4.0K Oct  9 06:58 root
drwxr-xr-x   1 root root 4.0K Oct  9 06:39 run
lrwxrwxrwx   1 root root    8 Sep 25 01:20 sbin -> usr/sbin
drwxr-xr-x   2 root root 4.0K Sep 25 01:20 srv
dr-xr-xr-x  13 root root    0 Oct  9 06:22 sys
drwxrwxrwt   1 root root 4.0K Oct  9 06:58 tmp
-rw-r--r--   1 root root    0 Oct  9 06:58 updatedAt.txt
drwxr-xr-x   1 root root 4.0K Sep 25 01:20 usr
drwxr-xr-x   1 root root 4.0K Sep 25 01:23 var

# next minute
root@e79f84fdc37f:/# ls -al
total 68K
drwxr-xr-x   1 root root 4.0K Oct  9 06:44 .
drwxr-xr-x   1 root root 4.0K Oct  9 06:44 ..
-rwxr-xr-x   1 root root    0 Oct  9 06:05 .dockerenv
lrwxrwxrwx   1 root root    7 Sep 25 01:20 bin -> usr/bin
drwxr-xr-x   2 root root 4.0K Apr 15 11:09 boot
drwxr-xr-x   5 root root  360 Oct  9 06:22 dev
drwxr-xr-x   1 root root 4.0K Oct  9 06:41 etc
drwxr-xr-x   2 root root 4.0K Apr 15 11:09 home
lrwxrwxrwx   1 root root    7 Sep 25 01:20 lib -> usr/lib
lrwxrwxrwx   1 root root    9 Sep 25 01:20 lib32 -> usr/lib32
lrwxrwxrwx   1 root root    9 Sep 25 01:20 lib64 -> usr/lib64
lrwxrwxrwx   1 root root   10 Sep 25 01:20 libx32 -> usr/libx32
drwxr-xr-x   2 root root 4.0K Sep 25 01:20 media
drwxr-xr-x   2 root root 4.0K Sep 25 01:20 mnt
drwxr-xr-x   2 root root 4.0K Sep 25 01:20 opt
dr-xr-xr-x 136 root root    0 Oct  9 06:22 proc
drwx------   1 root root 4.0K Oct  9 06:58 root
drwxr-xr-x   1 root root 4.0K Oct  9 06:39 run
lrwxrwxrwx   1 root root    8 Sep 25 01:20 sbin -> usr/sbin
drwxr-xr-x   2 root root 4.0K Sep 25 01:20 srv
dr-xr-xr-x  13 root root    0 Oct  9 06:22 sys
drwxrwxrwt   1 root root 4.0K Oct  9 06:59 tmp
-rw-r--r--   1 root root    0 Oct  9 06:59 updatedAt.txt
drwxr-xr-x   1 root root 4.0K Sep 25 01:20 usr
drwxr-xr-x   1 root root 4.0K Sep 25 01:23 var
```

### 2.time parameters rule

```bash
m h dom mon dow command
```

- m(分钟)/h(小时)/dom(一个月份中的第几日)/mon(表示月份)/dow(表示一个星期中的第几天)
- command(执行的命令)
- m为*表示每分钟都执行一次command,以此类推...
- m为a-b时表示从第a分钟到第b分钟这段时间内要执行,以此类推...
- m为*/n时表示每 n 分钟个时间间隔执行一次,以此类推...
- m为a,b,c,...时表示第 a, b, c,...分钟要执行,以此类推...

```
*    *    *    *    *
-    -    -    -    -
|    |    |    |    |
|    |    |    |    +----- 星期中星期几 (0 - 7) (星期天 为0)
|    |    |    +---------- 月份 (1 - 12) 
|    |    +--------------- 一个月中的第几天 (1 - 31)
|    +-------------------- 小时 (0 - 23)
+------------------------- 分钟 (0 - 59)
```

## 二、Node Crontab

> base on node-cron

### 1.usage

```javascript
const CronJob = require('cron').CronJob;
const job = new CronJob('* * * * * *', function() {
  console.log('You will see this message every second');
}, null, true, 'America/Los_Angeles');
job.start();
```

```
PS D:\My Projects\crontabLearning> yarn start   
Active code page: 65001
yarn run v1.22.4
$ node index.js
You will see this message every second
You will see this message every second
You will see this message every second
You will see this message every second
You will see this message every second
You will see this message every second
You will see this message every second
You will see this message every second
You will see this message every second
You will see this message every second
You will see this message every second
```

### 2.api

```js
constructor(cronTime, onTick, onComplete, start, timezone, context, runOnInit, unrefTimeout)
```

- cronTime [必需] 配置定时任务的时间，可以使用这可以是cron语法或JS Date对象的形式。 

- onTick [必需] 在指定时间触发的回调。 

- onComplete [可选] 在作业停止时将触发的回调。 

- Start [可选] 指定是否在退出构造函数之前启动作业，默认情况下，此值设置为false。 

- timeZone [可选] 指定执行的时区。这将修改相对于您的时区的实际时间 ，不设置为当前所在时区。