# WebServer

> 支持传统应用，支持单页应用。

## 一个简单易用的Web服务。

> 特色：

#### 1.为单页应用提供服务时，不会出现history路由模式下刷新404问题。
#### 2.项目打包时，无需压缩源文件，服务运行后，会根据客户端访问动态使用gzip压缩并缓存至本地。

## 使用方式：

> 调整目录结构如下：

```
├── webServer
├── web
│ └── index.html
│ └── css
│ └── js
│ └── fonts
```

### 运行

```
./webServer
```

## 查看

```
(http://localhost)[http://localhost]
```
