# mongdb
-----

## 安装  
1.  windows安装  
  1.1 [mongodb官网地址](http://www.mongodb.org) 下载安装包  
  1.2 将安装目录下的`bin/`目录,放到系统全局变量下面   
  1.3 将mongodb将入到windows服务 ,用以下命令   
   mongod.exe --logpath d:/websoft/mongodb/logs --logappend --dbpath d:/websoft/mongodb/data --directoryperdb --serviceName MongoDB -install  
2. mongod 命令部分参数详解
  1.1 --logpath arg   `输出日志目录`  
  1.2 --dbpath arg    `数据库存放目录`  
  1.3 --logappend   `使用追加的方式写日志`  
  1.4 --directoryperdb   `设置每个数据库将被保存在一个单独的目录`  
  1.5 --serviceName arg  `服务器的名字`  
  1.6  --install         `在windows安装服务`  
  1.7  --uninstall   `在windows卸载服务`  
  1.8 --reinstall    `重新安装服务`    
  1.9 --port arg	`指定服务端口号，默认端口27017`   
  1.10  --bind_ip arg    `绑定服务IP，若绑定127.0.0.1，则只能本机访问，不指定默认本地所有IP`  
  1.11   --fork	`以守护进程的方式运行MongoDB，创建服务器进程`   
  1.12  --shutdown  `杀死mongod进程`
  1.13  --config  arg  `指定配置文件`  
      
## 启动
1. 启动命令 `mongod --dbpath='指定文件存放的目录'`  
    **默认的端口号是`27017`** 
2. 然后继续开启命令行交互模式,输入命令 `mongo`   
   **mongo 命令给我提供了和mongodb交互的环境,他就是一个javascript解析器**  
3. 开始你的mongodb之旅
4. 如果您不想通过命令行操作,可安装可视化图形工具 `mongvue`, 1.0版本的开始收费了，[免费破解版v1.5.3](http://download.csdn.net/detail/sunboy_2050/6770483) 
          
  
  
 