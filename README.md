# weixin-wepy-swipe-delete
微信小程序-wepy-侧滑删除组件，支持自定义内容区

在最近的微信小程序开发过程中需要用到侧滑删除的功能，微信小程序官方是没有提供这样的组件，再加上我们的微信小程序使用的是wepy组件开发框架开发的，wepy也没有提供这样的组件，之前也在github上搜索这方面的组件，没有发现合适的，当时只发现了一个开源的:https://github.com/GeoffZhu/wepy-swipe-delete
只不过该组件功能单一已经被作者废弃了，无奈自己动手撸了一个侧滑删除组件，现在把它开源出来吧。

### Requirements
- wepy: "^1.7.3"

## 支持功能和特点
- 自定义内容区域：支持之定义内容区域，组件内使用 slot占位。
- 自定义滚动高度：可以自定义scroll-view的高度，默认为屏幕的高度。
- 自定义menu ：如果默认的menu样式不喜欢可以自定义，也可以显示或者隐藏指定的menu。
- 左右滑动：支持左右滑动也可以设置只左右或者右滑。

## 如何使用
目前支持两种使用模式：
#### 1.page页面模式
```javascript 1.8
优点：可定制化高，扩展性强。
缺点：集成复杂，代码复用性差。
```
#### 效果如下：
![image](https://raw.githubusercontent.com/hu670014125/weixin-wepy-swipe-delete/master/screenshots/screenshots1.gif)
![image](https://raw.githubusercontent.com/hu670014125/weixin-wepy-swipe-delete/master/screenshots/screenshots2.gif)
![image](https://raw.githubusercontent.com/hu670014125/weixin-wepy-swipe-delete/master/screenshots/screenshots3.gif)
![image](https://raw.githubusercontent.com/hu670014125/weixin-wepy-swipe-delete/master/screenshots/screenshots4.gif)
![image](https://raw.githubusercontent.com/hu670014125/weixin-wepy-swipe-delete/master/screenshots/screenshots5.gif)
![image](https://raw.githubusercontent.com/hu670014125/weixin-wepy-swipe-delete/master/screenshots/screenshots6.gif)
![image](https://raw.githubusercontent.com/hu670014125/weixin-wepy-swipe-delete/master/screenshots/screenshots7.gif)
![image](https://raw.githubusercontent.com/hu670014125/weixin-wepy-swipe-delete/master/screenshots/screenshots8.gif)


#### 2.component 组件模式
```javascript 1.8
优点：集成简单，代码复用性强，减少包的大小。
缺点：可定制到低。
```

不建议使用page页面模式，下面详细介绍component 组件模式的使用

### 如何使用

```javascript
// 导入组件
import SwipeDeleteView from '@/components/wepy-swipe-delete-view'

// 声明组件

 components = {
      swipeDelete: SwipeDeleteView
    }
    
  // 引用组件
  <template>
  <swipeDelete :list.sync="list">
      <view class="item">{{item.userName}}</view>
    </swipeDelete>
  </template>

```

配置如下：
```html
<swipeDelete   :list.sync="list"
               :scrollHeight="scrollHeight"
               @deleteTap.user="deleteTap"
               @deleteLongTap.user="deleteLongTap"
               @editTap.user="editTap"
               @editLongTap.user="editLongTap"
               @addTap.user="addTap"
               @addLongTap.user="addLongTap"
               @markTap.user="markTap"
               @markLongTap.user="markLongTap">

```

属性 | 属性说明 |备注
---|---|---
list | 要显示的列表的原始数据，最好是加上.sync这样可以异步传值|必传
scrollHeight | 设置scroll-view的高度，默认为屏幕高度|选传
deleteTap.user | 删除menu单击事件回调|必要时传
deleteLongTap.user | 删除menu长按事件回调|必要时传
editTap.user | 编辑menu单击事件回调|必要时传
editLongTap.user| 编辑menu长按事件回调|必要时传
addTap.user| 添加menu单击事件回调|必要时传
addLongTap.user| 添加menu长按事件回调|必要时传
markTap.user| 标记menu单击事件回调|必要时传
markLongTap.user| 标记menu长按事件回调|必要时传

每个点击事件或者长按事件都会返回两个参数

```javascript
methods = {
      deleteTap(view, item) {
        console.log(item)
        view.deleteItem()
      },
      deleteLongTap(view, item) {
        console.log(item)
        wx.showModal({
          title: '提示',
          content: '确定要删除吗？',
          success: function (res) {
            if (res.confirm) {
              view.deleteItem()
            } else {
              view.closeItem()
            }
          }
        })
      }
   }
   
```
 - view ：view 是SwipeDeleteView对象的本身，可以通过view来做一些其他操作，如:删除当前的item
 - item : item 就是当前操作的原始数据，可以通过item获取真正需要的数据
 
 当前SwipeDeleteView对外暴露的函数有：
 
 函数名称 | 函数说明 |参数
 ---|---|---
 deleteItem | 删除当前操作的item(原始数据+view)都会被删除|不需要参数
 closeItem | 关闭当前操作的item，原始数据不变|不需要参数
### LICENSE

Copyright 2017 CJT2325

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
