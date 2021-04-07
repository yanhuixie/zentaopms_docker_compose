# zentaopms & docker_compose
使用docker_compose部署禅道，怎么简单怎么来。

zentaopms（禅道）是据我所知最为优秀的广受欢迎的国产开源项目管理系统。  
  
禅道的官方部署文档已经非常丰富完善，详见 https://www.zentao.net/book/zentaopmshelp/40.html 。禅道也提供了docker部署的方式（https://hub.docker.com/r/easysoft/zentao & https://www.zentao.net/book/zentaopmshelp/303.html ），可惜官方的docker镜像里面塞进了一个MySQL，这种方式虽然方便了一些用户，但是并不符合docker的使用惯例，而且我的场景是公司已经有共享的MySQL服务器可用，并不需要单独为禅道提供一个了。所以我并不希望使用禅道官方的docker镜像。  
  
因此我需要一个自定义的Dockerfile，正好看到tonynii 同学已经做了一些基础工作（https://github.com/tonynii/zentao_docker-compose ），我沿用了他的工作成果，在此表示感谢。当然tonynii做的工作很多，包含了单独的MySQL Dockerfile，我这里就没有沿用，如有需要请前往参考。因此我的docker-compose.yml也简单很多。我采用的是自行下载源码包的方式（https://www.zentao.net/dynamic/zentaopms12.5.3-80319.html & https://www.zentao.net/dl/zentao/12.5.3/ZenTaoPMS.12.5.3.zip ），下载后在docker-compose.yml 相同目录unzip即可。  
  
编辑好Dockerfile和docker-compose.yml之后，只需要
```
docker build -t zentaopms:latest .
docker-compose up -d
```
然后进入http://yoursite:port/ ，会自动跳转到禅道install页面，根据向导完成安装工作即可。
