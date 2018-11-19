<p align="center"><a href="https://wyydsb.xin" target="_blank" rel="noopener noreferrer"><img width="100" src="https://cdn.nlark.com/yuque/0/2018/jpeg/104214/1540358574166-46cbbfd2-69fa-4406-aba9-784bf65efdf9.jpeg" alt="Spider logo"></a></p>
<h1 align="center">Spider Press Man</h1>

[![GitHub](https://img.shields.io/github/license/iofu728/spider.svg?style=popout-square)](https://github.com/iofu728/spider/master/LICENSE)
[![GitHub tag](https://img.shields.io/github/tag/iofu728/spider.svg?style=popout-square)](https://github.com/iofu728/spider)
[![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/iofu728/spider.svg?style=popout-square)](https://github.com/iofu728/spider)

<div align="center"><strong>高可用代理IP池 高并发爬虫 不均匀的压力分发系统 </strong></div>
<div align="center"><strong>Highly Available Proxy IP Pool, Highly Concurrent Spider, Uneven Pressure Distribution System</strong></div>

## Key

* <u>`高可用IP代理池`</u>
  + 通过获得Gatherproxy, Goubanjia, xici 等Free Proxy WebSite 数据建立代理池
  + 解析Goubanjia port数据
  + 快速检验IP可用性
  + 配合Requests 自动分配代理Ip, 带有Retry机制, 失败写入DB机制
* <u>`Netease`</u>
  + classify -> playlist id -> song_detail
  + V1 写文件 一次运行版本 无代理，无记录进度机制
  + V1.5 少量代理IP
  + V2 代理IP池 记录进度 写入MySQL
    - 对写库进行优化 Load data/ Replace INTO
* <u>`Press Test`</u>
  + By highly available proxy IP pool to pretend user.
  + Give some web service uneven pressure
  + To do: press uniform

## 开发指南

```bash
$ git clone https://github.com/iofu728/spider.git
$ cd spider
$ ipython
# netease spider
$ import netease.netease_music_db
$ xxx = netease.netease_music_db.Get_playlist_song()
# press
$ import press.press
$ xxx = press.press.Press_test()
$ xxx.one_press_attack(url, host, qps, types, total)
```

## 目录结构
```bash
.
├── LICENSE                        // LICENSE
├── README.md                      // README
├── log                           // failured log
├── netease
│   ├── netease_music_base.py      // v1 spider
│   ├── netease_music_db.py        // v2 spider
│   ├── result.txt                 // result
│   └── table.sql                  // netease sql
├── press
│   └── press.py                   // press
├── proxy
│   ├── gatherproxy                // gatherproxy data
│   ├── getproxy.py                // proxy pool
│   └── table.sql                  // proxy sql
├── song_detail
└── utils
    ├── db.py                      // db operation
    └── utils.py                   // requests operation
```

## 设计文档
* [Netease Music Spider for DB](https://wyydsb.xin/other/neteasedb.html)
* [Netease Music Spider](https://wyydsb.xin/other/netease.html)

