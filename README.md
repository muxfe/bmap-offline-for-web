# bmap-offline-for-web

Baidu Map Web Localization Solution（百度地图Web端离线解决方案）

# 开始使用 (Getting Started)

## 下载 (Download)

`$ git clone https://github.com/muxfe/bmap-offline-for-web.git`

或者 (or)

[下载压缩包 (Download ZIP)](https://github.com/muxfe/bmap-offline-for-web/archive/master.zip)

## 配置 (Configuration)

加载 `BaiduApi_2.0.js` 之前修改自定义配置：

custom config before load `BaiduApi_2.0.js`:

```js
window.__BMAP_EXTRA_CONFIG__ = {
    enable: true,
    host: 'http://localhost/', // exmaple in nginx container
    path: 'bmap-offline-for-web/',
    tilePath: 'tiles/tile',
    satellitePath: 'tiles/it',
    roadPath: 'tiles/road'
}
```

默认配置 (default configuration):

```js
{
    // 是否启用离线地图 (main switch)
    enable: false,
    // 部署离线地图的服务器地址 (deploy bmap-offline server host)
    host: '',
    // 静态资源路径，相对于 host
    // (static resources path (relative host root path))
    path: '',
    // 瓦片图资源路径，相对于 host 或 tileHost
    // (tile pics resources path (relative host or tileHost root path))
    tilePath: 'tiles/tile',
    // 卫星图资源路径，相对于 host 或 tileHost
    // (satellite pics resources path (relative host or tileHost root path))
    satellitePath: 'tiles/it',
    // 混合地图中的路网图资源路径，相对于 host 或 tileHost
    // (satellite street pics resources path (relative host root path))
    roadPath: 'tiles/road',
    // 瓦片图时间戳 (tile updated date)
    tileUdt: '20170927',
    // 卫星图时间戳 (satellite updated date)
    satelliteUdt: '20170927',
    // 混合地图中的路网图时间戳 (satellite street updated date)
    roadUdt: '20170927',
    // 离线化的功能模块 js 文件
    // (localized modules (path is [host][path][getmodules]/))
    modules: [
        'map,scommon,mapclick,oppc,newvectordrawlib,style,tile,navictrl',
        'canvablepath,common,symbol,marker,copyrightctrl',
        'draw,drawbycanvas,drawbysvg,drawbyvml,poly'
    ],
    // 百度地图自身 API 请求拦截器 (BMap request interceptor)
    interceptor: function (url) {
        return /(qt=vQuest|qt=verify|qt=cen)/.test(url);
    }
}
```

## 部署 (Deploy)

可以部署在 nginx 等 web 容器中。(Example nginx or others).

# 百度地图瓦片图和卫星图下载器 (Download Baidu Map Tiles)

- <https://github.com/muxfe/BaiduMap_tiles>
