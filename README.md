# weixin-wepy-swipe-delete
微信小程序-wepy-侧滑删除组件，支持自定义内容区

在最近的微信小程序开发过程中需要用到侧滑删除的功能，微信小程序官方是没有提供这样的组件，再加上我们的微信小程序使用的是wepy组件开发框架开发的，wepy也没有提供这样的组件，之前也在github上搜索这方面的组件，没有发现合适的，当时只发现了一个开源的:https://github.com/GeoffZhu/wepy-swipe-delete，只不过该组件功能单一已经被作者废弃了，无奈自己动手撸了一个侧滑删除组件，现在把它开源出来吧。

## 支持功能和特点
- 自定义内容区域：支持之定义内容区域，组件内使用 slot占位。
- 自定义滚动高度：可以自定义scroll-view的高度，默认为屏幕的高度。
- 自定义menu ：如果默认的menu样式不喜欢可以自定义，也可以显示或者隐藏指定的menu。
- 左右滑动：支持左右滑动也可以设置只左右或者右滑。

## 如何使用
目前支持两种使用模式：
#### 1.page页面模式
```javascript 1.8
优点：定制化搞，扩展性强。
缺点：集成负责，代码复用性差。
```
#### 效果如下：
![image](https://raw.githubusercontent.com/hu670014125/weixin-wepy-swipe-delete/master/screenshots/screenshots1.gif)

### LICENSE

Copyright 2017 CJT2325

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
