### docker-compose.yml 文件如下

```
web:
  image: 'gitlab/gitlab-ce:latest'
  container_name: 'gitlab'
  restart: always
  hostname: 'localgitlab.com'
  environment:
    GITLAB_OMNIBUS_CONFIG: |
      external_url 'http://localgitlab.com'
      gitlab_rails['gitlab_shell_ssh_port'] = 30001
      gitlab_rails['gitlab_ssh_host'] = 'localgitlab.com'
      gitlab_rails['gitlab_default_can_create_group'] = true
      gitlab_rails['gitlab_username_changing_enabled'] = true
  ports:
    - '30000:80' # web 端口
    - '30001:22' # ssh 端口
    - '30002:443'# https 端口
  volumes:
    - '{$HOME}/gitlab/config:/etc/gitlab'
    - '{$HOME}/gitlab/logs:/var/log/gitlab' 
    - '{$HOME}/gitlab/data:/var/opt/gitlab'
```

### 启动步骤

#### 1.改变 $HOME 变成你的路径即可，并且保证 gitlab 有读写权限

#### 2.配置 hostname 位你的访问地址

#### 3.执行 docker-compose up --build 前台启动

#### 4.执行 docker-compose up -d 后台启动

#### 5.访问 {hostname}:{port} 比如我的 http://localgitlab.com：30000 就是 gitlab 访问地址