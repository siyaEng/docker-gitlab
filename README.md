[chinese lanuage](https://github.com/siyaEng/docker-gitlab/blob/master/README.md)

### edit ```.env```  to yourself

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

### about ${HOME}

you can change ${HOME} to your directory, make sure you have writable and readable

### about VOLUMES

```
volumes:
    - '${HOME}/gitlab/config:/etc/gitlab'  #gitlab config
    - '${HOME}/gitlab/logs:/var/log/gitlab'#gitlab logs
    - '${HOME}/gitlab/data:/var/opt/gitlab'#gitlab datas
```
all about gitlab info is volumed ${HOME}/gitlab，so it is very import to you.

### build step

#### 1. change path to the docker-gitlab project 
```cd ${docker-gitlab-project}```

#### 2.run a command nodeamon
```docker-compose up --build```

#### or run a command deamon
```docker-compose up -d```

#### 3.check the contain status
```docker ps```

```
CONTAINER ID        IMAGE                     COMMAND             CREATED             STATUS                            PORTS                                                                  NAMES
a347ed312115        gitlab/gitlab-ce:latest   "/assets/wrapper"   17 minutes ago      Up 3 seconds (health: starting)   0.0.0.0:30001->22/tcp, 0.0.0.0:30000->80/tcp, 0.0.0.0:30002->443/tcp   gitlab
```
#### 4. view {hostname}:{port} on web

like ```http://localgitlab.com：30000``` is my gitlab-web address