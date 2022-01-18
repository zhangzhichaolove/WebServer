# WebServer

> 支持传统应用，支持单页应用。

## 一个简单易用的Web服务。

### 下载：[Releases](https://github.com/zhangzhichaolove/WebServer/releases)

### 为了更加方便，现已支持[docker-v1部署](./docker.md)了
### 为了减小容器体积，现已支持[docker-v2部署](./docker-1.0.2.md)了,镜像大小仅4M.

## 更新:

> 2022-01-18更新版本->1.0.2
#### 1.支持后台运行

```shell
# 默认后台运行
./webServer
# 关闭后台运行
./webServer stop
# 前台方式运行
./webServer -d=false
```

---

> 2021-12-15更新版本->1.0.1
#### 1.添加服务配置文件（首次启动会自动生成）
#### 2.支持配置自定义端口。
#### 3.支持https配置（需要配置证书）

---

> 特色：

#### 1.为单页应用提供服务时，不会出现history路由模式下刷新404问题。
#### 2.项目打包时，无需压缩源文件，服务运行后，会根据客户端访问动态使用gzip压缩并缓存至本地。

## 使用步骤：

#### 1.将对应平台的`webServer`文件拷贝至项目目录。

> 结构如下：

```
├── dist (前端build之后的目录)
└── webServer
```


#### 2.运行`webServer`

```
./webServer
```

#### 3.修改运行配置并重启-可选

> 首次运行后，会在当前目录生成默认`app.yaml`配置文件，结构如下：

```
├── dist (前端build之后的目录)
├── app.yaml (生成的默认配置文件)
└── webServer
```

> `app.yaml`配置如下：

```
server:
  path: ./dist
  https: false
  port: 80
  pem: ./ssl/ssl.pem
  key: ./ssl/ssl.key
```

> 修改`app.yaml`配置到https：

```
server:
  path: ./dist
  https: true
  port: 443
  pem: ./ssl/ssl.pem
  key: ./ssl/ssl.key
```

> 重启生效：

```
./webServer
```

## 使用对比：

> 运行前目录结构如下：

```
├── web
│   ├── css
│   │   ├── app.6b546ac1.css
│   │   ├── chunk-02fc906a.8da36c38.css
│   │   ├── chunk-1197f7aa.b4f20442.css
│   │   ├── chunk-140d18fa.bd93c9c8.css
│   │   ├── chunk-4000137c.8e6782aa.css
│   │   └── chunk-vendors.f79c1e5f.css
│   ├── favicon.ico
│   ├── fonts
│   │   ├── element-icons.abe71f7d.ttf
│   │   └── element-icons.d9491be2.woff
│   ├── index.html
│   └── js
│       ├── app.9fa010c9.js
│       ├── chunk-02fc906a.6fdd9d21.js
│       ├── chunk-1197f7aa.f5666e9c.js
│       ├── chunk-140d18fa.48df1c3a.js
│       ├── chunk-2d0e5e97.86eb2ed4.js
│       ├── chunk-2d22d746.b90aba11.js
│       ├── chunk-4000137c.f3b90fe1.js
│       ├── chunk-6e9942cd.72d613aa.js
│       └── chunk-vendors.2c045c43.js
└── webServer

```

> 运行后目录结构如下：

```
├── web
│   ├── css
│   │   ├── app.6b546ac1.css
│   │   ├── app.6b546ac1.css.gz
│   │   ├── chunk-02fc906a.8da36c38.css
│   │   ├── chunk-02fc906a.8da36c38.css.gz
│   │   ├── chunk-1197f7aa.b4f20442.css
│   │   ├── chunk-1197f7aa.b4f20442.css.gz
│   │   ├── chunk-140d18fa.bd93c9c8.css
│   │   ├── chunk-140d18fa.bd93c9c8.css.gz
│   │   ├── chunk-4000137c.8e6782aa.css
│   │   ├── chunk-4000137c.8e6782aa.css.gz
│   │   ├── chunk-vendors.f79c1e5f.css
│   │   └── chunk-vendors.f79c1e5f.css.gz
│   ├── favicon.ico
│   ├── favicon.ico.gz
│   ├── fonts
│   │   ├── element-icons.abe71f7d.ttf
│   │   ├── element-icons.d9491be2.woff
│   │   └── element-icons.d9491be2.woff.gz
│   ├── index.html
│   ├── index.html.gz
│   └── js
│       ├── app.9fa010c9.js
│       ├── app.9fa010c9.js.gz
│       ├── chunk-02fc906a.6fdd9d21.js
│       ├── chunk-02fc906a.6fdd9d21.js.gz
│       ├── chunk-1197f7aa.f5666e9c.js
│       ├── chunk-1197f7aa.f5666e9c.js.gz
│       ├── chunk-140d18fa.48df1c3a.js
│       ├── chunk-140d18fa.48df1c3a.js.gz
│       ├── chunk-2d0e5e97.86eb2ed4.js
│       ├── chunk-2d0e5e97.86eb2ed4.js.gz
│       ├── chunk-2d22d746.b90aba11.js
│       ├── chunk-2d22d746.b90aba11.js.gz
│       ├── chunk-4000137c.f3b90fe1.js
│       ├── chunk-4000137c.f3b90fe1.js.gz
│       ├── chunk-6e9942cd.72d613aa.js
│       ├── chunk-6e9942cd.72d613aa.js.gz
│       ├── chunk-vendors.2c045c43.js
│       └── chunk-vendors.2c045c43.js.gz
└── webServer

```

## 压缩前后对比

> 压缩前

![压缩前](./before.png)

> 压缩后

![压缩后](./after.png)

## 使用方式：

### 运行

```
./webServer
```

### 查看

[http://localhost](http://localhost)
[https://localhost](https://localhost)

