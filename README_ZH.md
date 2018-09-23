[英文 readme](https://github.com/siyaEng/docker-gitlab/blob/master/README.md)

### 编辑 ```.env``` 成你自己的配置

```
GITLAB_URL=localgitlab.com
GITLAB_HTTP_URL=http://localgitlab.com
GITLAB_URL=localgitlab.com
GITLAB_DEFAULT_CAN_CREATE_GROUP=true
GITLAB_USERNAME_CHANGING_ENABLED=true
GITLAB_WEB_PORT=30000
GITLAB_SHELL_SSH_PORT=30001
GITLAB_HTTPS_PORT=30002
```

### 关于变量 ${HOME}

你可以改变 ${HOME} 变成你自己的目录, 确保这个目录有可写权限

### 关于 VOLUMES

```
volumes:
    - '${HOME}/gitlab/config:/etc/gitlab'  #gitlab的配置文件
    - '${HOME}/gitlab/logs:/var/log/gitlab'#gitlab的日志目录
    - '${HOME}/gitlab/data:/var/opt/gitlab'#gitlab的数据目录
```
gitlab 的相关信息都挂载到 ${HOME}/gitlab，所以此目录尤其重要

### 构建步骤

#### 1. 进入到 docker-gitlab 项目目录中
```cd ${docker-gitlab-project}```

#### 2.执行前台启动,可以看到构建的 log
```docker-compose up --build```

#### 或者执行后台启动，这个看不到构建的 log
```docker-compose up -d```

#### 3.查看容器的运行状态
```docker ps```

如下
```
CONTAINER ID        IMAGE                     COMMAND             CREATED             STATUS                            PORTS                                                                  NAMES
a347ed312115        gitlab/gitlab-ce:latest   "/assets/wrapper"   17 minutes ago      Up 3 seconds (health: starting)   0.0.0.0:30001->22/tcp, 0.0.0.0:30000->80/tcp, 0.0.0.0:30002->443/tcp   gitlab
```
#### 4. 在浏览器中输入 {hostname}:{port}
比如 ```http://localgitlab.com：30000``` 就是我的 gitlab 地址
