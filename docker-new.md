# V3版本镜像仅2M大小

### 超简单的web部署服务，支持vue/react等框架开发的单页应用部署并使用gzip压缩，更省流量。

## 使用说明：

## 拉取镜像：
```
docker pull peakchao/web-server:v3
```

##### 启动容器时，需要挂载你的资源目录到容器/data/路径下，并开放你想要使用的端口，第一次运行容器会自动在你挂载的目录生成`app.yaml`配置文件，修改配置文件后，请重启容器，容器默认使用http服务，端口80，默认读取挂载目录/data/web/index.html

## 启动示例：

> 默认`/Users/chao/Downloads`目录结构(如果无需https配置，可以省去ssl目录)：

```
── ssl
   ├── ssl.key
   └── ssl.pem
── web
   ├── css
   │   ├── app.6b546ac1.css
   │   └── chunk-vendors.f79c1e5f.css
   ├── favicon.ico
   ├── fonts
   │   └── element-icons.d9491be2.woff
   ├── index.html
   └── js
       ├── app.9fa010c9.js
       ├── .....
       └── chunk-vendors.2c045c43.js
```

> 默认配置启动示例：

```
docker container run -d -p 80:80 -p 443:443 -v /Users/chao/Downloads:/data --name web-server peakchao/web-server:v2
```

> 首次启动后会在`/Users/chao/Downloads`目录生成的默认`app.yaml`配置文件,修改配置文件后重启容器生效：

```
server:
  path: ./web
  https: false
  port: 80
  pem: ./ssl/ssl.pem
  key: ./ssl/ssl.key
```

## 启动命令：
```
docker container run -d -p 80:80 -p 443:443 -v /Users/chao/Downloads:/data --name web-server peakchao/web-server:v2
```
## 打开浏览器验证：
```
http://localhost
https://localhost
```
## 配置参考：
app.yaml
```
server:
  https: true
  path: /data/web
  pem: "/data/ssl/ssl.pem"
  key: "/data/ssl/ssl.key"
  port: 443

```
## data挂载目录结构：
```
├── app.yaml
├── ssl
│   ├── ssl.key
│   └── ssl.pem
└── web
    ├── css
    │   ├── app.6b546ac1.css
    │   └── chunk-vendors.f79c1e5f.css
    ├── favicon.ico
    ├── index.html
    └── js
        ├── app.9fa010c9.js
        └── chunk-vendors.2c045c43.js
```
