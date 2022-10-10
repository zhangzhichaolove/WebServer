# 镜像仅2M大小

### 超简单的web部署服务，支持vue/react等框架开发的单页应用部署并使用gzip压缩，更省流量。

## 使用说明：

## 拉取镜像：
```
docker pull peakchao/web-server:v5
```

##### 启动容器时，需要挂载你的资源目录(需要发布的目录)到容器/data/路径下，并开放你想要使用的端口，第一次运行容器会自动在你挂载的目录生成`app.yaml`配置文件，修改配置文件后，请重启容器生效，容器默认使用http服务，端口80，默认读取挂载目录/data/dist/index.html

## 启动示例：

> 默认`/Users/chao/Downloads/data`目录结构(如果无需https配置，可以省去ssl目录)：

```
├── ssl
│   ├── ssl.key
│   └── ssl.pem
└── dist
    ├── css
    │   ├── app.6b546ac1.css
    │   └── chunk-vendors.f79c1e5f.css
    ├── favicon.ico
    ├── index.html
    └── js
        ├── app.9fa010c9.js
        └── chunk-vendors.2c045c43.js
```

> 默认配置启动示例：

```
docker container run -d -p 80:80 -p 443:443 -v /Users/chao/Downloads/data:/data --name web-server peakchao/web-server:v5
```

> 首次启动后会在`/Users/chao/Downloads/data`目录生成的默认`app.yaml`配置文件,修改配置文件后重启容器生效：

1. `path`代表使用哪个目录进行发布，例如：path: web | path: ./test | path: /data/html | path: .
2. `https` 为true时，pem/key必填，会使用https启动服务
3. `port`服务端口，可以自定义，例如：port: 80 ｜ port: 88 ｜ port: 443
4. `pem`ssl证书的pem，例如：pem: ./ssl/ssl.pem | pem: ssl/ssl.pem | pem: ssl.pem
5. `key`ssl证书的key，例如：key: ./ssl/ssl.key | key: ssl/ssl.key | key: ssl.key

```
server:
  path: dist
  https: false
  port: 80
  pem: ./ssl/ssl.pem
  key: ./ssl/ssl.key
```

# 以下是v4版本配置:

## 启动命令：
```
docker container run -d -p 80:80 -p 443:443 -v /Users/chao/Downloads:/data --name web-server peakchao/web-server:v4
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
