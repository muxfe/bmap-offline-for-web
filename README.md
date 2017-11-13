# bmap-offline-for-web

Baidu Map Web Localization Solution（百度地图Web端离线解决方案）

# Getting Started

## Download

`$ git clone https://github.com/muxfe/bmap-offline-for-web.git`

or 

[Download ZIP](https://github.com/muxfe/bmap-offline-for-web/archive/master.zip)

## Configuration

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

default configuration:

```js
{
    enable: false, // main switch
    host: 'http://localhost/', // local server host
    // static resources path (relative host root path)
    path: 'bmap-offline-for-web/', 
    // tile pics resources path (relative host root path)
    tilePath: 'tiles/tile', 
    // satellite pics resources path (relative host root path)
    satellitePath: 'tiles/it', 
    // satellite street pics resources path (relative host root path)
    roadPath: 'tiles/road', 
    tileUdt: '20170927', // tile updated date
    satelliteUdt: '20170927', // satellite updated date
    roadUdt: '20170927', // satellite street updated date
    modules: [ // localized modules (path is [host][path][getmodules]/)
        'map,scommon,mapclick,oppc,newvectordrawlib,style,tile,navictrl',
        'canvablepath,common,symbol,marker,copyrightctrl',
        'draw,drawbycanvas,drawbysvg,drawbyvml,poly'
    ],
    interceptor: function (url) { // BMap request interceptor
        return /(qt=vQuest|qt=verify|qt=cen)/.test(url);
    }
}
```

## Deploy

Example nginx or others.

# Download Baidu Map Tiles

- <https://github.com/muxfe/BaiduMap_tiles>
