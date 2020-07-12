# 此文件夹用于UI自动化测试例子演示
## 环境准备
- 编译镜像  
```docker
docker build -t automation-test .
```
## UI自动化例子
- 打开浏览器输入bing.com
- 搜索框输入test并回车

## 运行方式
- 脚本运行在本地，运行环境也在本地
```shell script
python BingAutomationTest_local.py
```
- 通过selenium-grid方式在容器里面运行。脚本运行在本地，UI测试环境在容器里。
```shell script
# 启动容器
docker run -d --rm -p 5904:25900 -p 4444:24444 --name automation-container -v "$(pwd)":/home/seluser/automation -e SCREEN_WIDTH=1024 -e SCREEN_HEIGHT=768 automation-test:latest
python BingAutomationTest_container.py
```

- 脚本在也在容器里面运行。
```shell script
sh run_script_in_container_2.sh
```

## 多容器化运行
- 启动两个容器
- 在两个容器里面分别运行脚本
