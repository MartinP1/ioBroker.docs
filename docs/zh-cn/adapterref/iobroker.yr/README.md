---
translatedFrom: en
translatedWarning: 如果您想编辑此文档，请删除“translatedFrom”字段，否则此文档将再次自动翻译
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/zh-cn/adapterref/iobroker.yr/README.md
title: ioBroker.yr
hash: 909x94OluM0AUh1dlVG5z1r/erV0JsQft+dBUJGOXWo=
---
![商标](../../../en/adapterref/iobroker.yr/admin/yr.png)

![安装数量](http://iobroker.live/badges/yr-stable.svg)
![NPM 版本](http://img.shields.io/npm/v/iobroker.yr.svg)
![下载](https://img.shields.io/npm/dm/iobroker.yr.svg)

# IoBroker.yr
![测试和发布](https://github.com/ioBroker/ioBroker.yr/workflows/Test%20and%20Release/badge.svg)[![翻译状态](https://weblate.iobroker.net/widgets/adapters/-/yr/svg-badge.svg)](https://weblate.iobroker.net/engage/adapters/?utm_source=widget)

**此适配器使用 Sentry 库自动向开发人员报告异常和代码错误。**有关更多详细信息以及如何禁用错误报告的信息，请参阅[Sentry 插件文档](https://github.com/ioBroker/plugin-sentry#plugin-sentry)！从 js-controller 3.0 开始使用哨兵报告。

## Yr.no ioBroker 适配器
从[年号](https://yr.no)获取 10 天天气预报

[yr.no](https://yr.no) 是由 [挪威气象研究所](https://met.no) 和 [挪威广播公司] 联合提供的服务](https://nrk.no)

https://api.met.no/weatherapi/locationforecast/2.0/documentation

**注意** - 如果 _“将缺失的翻译发送到 iobroker.net”_ 被激活（默认）缺失的翻译将被发送到 iobroker.net 服务器。不会存储或分析任何 IP 或任何其他信息。只是缺少翻译。

## 图标
图标取自此处[https://api.met.no/weatherapi/weathericon/2.0/documentation](https://api.met.no/weatherapi/weathericon/2.0/documentation)，属于 yr.no。

＃＃ 去做
* 添加气象图（png 可能会停止使用新的 API）
*根据每小时预测添加每日预测
* 添加html表格

<!-- 下一个版本的占位符（在行首）：

### **正在进行中** -->
＃＃ 去做
* 设置状态预测对象

## Changelog
### 5.1.4 (2022-04-03)
* (bluefox) Used package "axios" instead of "get"

### 5.1.3 (2022-03-20)
* (Apollon77) Prevented crash when symbols are not provided for forecasts (seen on Sentry)

### 5.1.2 (2022-03-10)
* (Apollon77) Fixed some invalid object default values

### 5.1.1 (2022-03-10)
* (Apollon77) Added legend file to release also and fix usage

### 5.1.0 (2022-03-05)
* (Apollon77) Moved schedule if default is used on request of met.no
* (Apollon77) Do not query legend/icons dynamically, but deliver with the version
* (Apollon77) made sure to not execute logic when adapter stopped already

### 5.0.0 (2021-11-08)
* (klein0r) Fixed translations
* (klein0r) Update dates data type

### 3.0.5 (2021-07-26)
* (Apollon77) prevent calls and other errors to Yr when no location is defined

### 3.0.4 (2021-07-16)
* (Apollon77) prevent last js-controller 3.3 warnings

### 3.0.3 (2021-07-12)
* (Apollon77) prevent js-controller 3.3 warnings

### 3.0.2 (2021-07-07)
* (Apollon77) Fix crash issue from Sentry

### 3.0.1 (2021-07-06)
* (Apollon77) Optimizations and Fixes
* (Apollon77) Add Sentry crash reporting

### 3.0.0 [2021-06-06]
* (withstu) Switch to new JSON API and change data Structure (breaking)
* (withstu) Update project dependencies
* (arteck) Type of state was corrected

### 2.0.3 [2018-10-10]
* (bluefox) added translations

### 2.0.2 [2018-08-01]
* (bluefox) Warning! Breaking changes! States are renamed.
* (bluefox) Refactoring of states and roles

### 1.0.6 [2017-05-27]
* (Andre) Updated icon-set

### 1.0.5 [2016-10-10]
* (bluefox) moved weather widgets to this adapter

### 1.0.3 [2016-05-17]
* (bluefox) changed readme path

### 1.0.2 [2016-05-16]
* (bluefox) added translations

### 1.0.1 [2016-04-25]
* (bluefox) added translations

### 1.0.0 [2016-03-15]
* (bluefox) changed parsing of cities

### 0.1.9 [2015-10-28]
* (bluefox) fixed error with translations

### 0.1.8 [2015-10-27]
* (bluefox) translations
* (bluefox) automatically upload of missing translations to iobroker.net

### 0.1.7 [2015-07-10]
* (bluefox) made yr works with metro widgets

### 0.1.6 [2015-06-12]
* (bluefox) translations

### 0.1.5 [2015-03-26]
* (bluefox) translations

### 0.1.4 [2015-03-24]
* (bluefox) removed unit "%" for "wind direction"

### 0.1.3 [2015-03-22]
* (bluefox) fixed error with tomorrow and day after tomorrow

### 0.1.2 [2015-03-08]
* (bluefox) corrected links to yr.no web site

### 0.1.1
* (bluefox) added translates for the weather states in other languages

### 0.1.0
* (bluefox) updated yr on the new objects model

### 0.0.4
* (hobbyquaker) prepend "forecast." to state IDs

### 0.0.3
* (hobbyquaker) settings ui with autocomplete for location
* (hobbyquaker) renamed yr_forecast to forecast
* (hobbyquaker) added children attribute
* (hobbyquaker) decreased log verbosity
* (hobbyquaker) fixes

### 0.0.2
* (hobbyquaker) fixes

### 0.0.1
* (hobbyquaker) first release

## License
The MIT License (MIT)

Copyright (c) 2014-2022 hobbyquaker <hq@ccu.io>, Bluefox <dogafox@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.