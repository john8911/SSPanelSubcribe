
# geekSubcribeX

## 简介

使用 EasySwoole 开发的适用于 SSPanel-Uim 的独立订阅服务提供

## 使用

- 将 `config.php` 重命名为 [生产] `produce.php` 或 [测试] `dev.php`
- 将 `appprofile.example.php` 重命名为 `appprofile.php`

## 其他

进入你的vps并且选择合适的目录，我这里选择home目录:

cd /home/
git clone https://github.com/GeekQuerxy/SSPanelSubcribe.git #没有git 请使用yum install -y git 下载
Bash 复制
进入项目，修改文件：

cd /home/SSPanelSubcribe/   #进入项目目录
wget https://getcomposer.org/installer -O composer.phar && php composer.phar && php composer.phar install    #装依赖
cp appprofile.example.php appprofile.php  #把appprofile.example.php改为appprofile.php
cp config.php dev.php  #把config.php改为dev.php 测试环境的意思，也可以改为produce.php 生产环境

修改dev.php 文件：

vi dev.php #编辑文件
修改的内容部分如下，（其他随缘修改）：

    'database' => [
        'driver'    => 'mysql',
        'host'      => '127.0.0.1', #数据库地址
        'port'      => 3306, #数据库端口
        'database'  => 'ceshi', #数据库名
        'username'  => 'ceshi123', #数据库用户名
        'password'  => 'ceshi123', #数据库密码
        'charset'   => 'utf8',
        'collation' => 'utf8_general_ci',
        'prefix'    => ''
    ],

修改完文件以后,启动服务：

php easyswoole start #开发模式
php easyswoole start d  #守护模式 ，按我的修改，直接使用这个命令就可以了。
-------
使用:
  easyswoole [操作] [选项]

操作:
  install       安装easySwoole
  start         启动easySwoole
  stop          停止easySwoole(守护模式下使用)
  reload        热重启easySwoole(守护模式下使用)
  restart       重启easySwoole(守护模式下使用)
  help          查看命令的帮助信息
  phpunit       启动协程单元测试
  config        easyswoole配置管理
  process       easyswoole 自定义进程/task进程管理
  status        easyswole 服务运行状态
  task          easyswoole task进程状态
  crontab       easyswoole crontab管理

成功启动后,界面如下：

             o     o-o       o               o        o   o 
             | /  |          |             o |         \ /  
o--o o-o o-o OO    o-o  o  o O-o   o-o o-o   O-o  o-o   O   
|  | |-' |-' | \      | |  | |  | |    |   | |  | |-'  / \  
o--O o-o o-o o  o o--o  o--o o-o   o-o o   | o-o  o-o o   o 
   |
o--o

Started...
  ______                          _____                              _
 |  ____|                        / ____|                            | |
 | |__      __ _   ___   _   _  | (___   __      __   ___     ___   | |   ___
 |  __|    / _` | / __| | | | |  \___ \  \ \ /\ / /  / _ \   / _ \  | |  / _ \
 | |____  | (_| | \__ \ | |_| |  ____) |  \ V  V /  | (_) | | (_) | | | |  __/
 |______|  \__,_| |___/  \__, | |_____/    \_/\_/    \___/   \___/  |_|  \___|
                          __/ |
                         |___/
main server                   SWOOLE_WEB
listen address                0.0.0.0
listen port                   9501
ip@eth0                       10.0.0.2
worker_num                    8
reload_async                  true
max_wait_time                 3
pid_file                      /home/SSPanelSubcribe/Temp/pid.pid
log_file                      /home/SSPanelSubcribe/Log/swoole.log
daemonize                     true
user                          root
swoole version                4.4.16
php version                   7.2.32
easy swoole                   3.3.4
develop/produce               develop
temp dir                      /home/SSPanelSubcribe/Temp
log dir                       /home/SSPanelSubcribe/Log
Bash 复制
现在应该可以通过你的ip ：9501 进行访问了。然后再通过nginx反代到你的域名就可以开启https和隐藏端口了。！

nginx反代：

里面宝塔的nginx进行反代（先用准备好的域名创建一个站点），进入站点配置



反代完成以后就可以通过域名来访问了。
