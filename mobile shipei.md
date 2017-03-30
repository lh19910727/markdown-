#移动端适配

标签（空格分隔）： 未分类

---

在此输入正文
```
<meta name="viewport" content="width=device-width,user-scalable=no" />
```


## 移动端事件
1. touchstart 手指按下
2. touchmove 手指移动
3. touchend 手指抬起

绑定事件要用addEventListener()来绑定事件处理函数。

## 取消默认行为
> 阻止文字被选中   -阻止冒泡后可选中文字
> 阻止页面上系统菜单
> 消除回弹

隐患：造成页面中滚动条失效



### 移动端的点透

> 在移动端pc端有300ms延迟
> 点击后会记录原来坐标
> 300m后会在记录的坐标位置触发

当有元素覆盖，上层元素touchend之后，元素偏离或消失在原来位置，会触发下层能够获取焦点元素的一些行为；例如：a标签跳转；input获取焦点。。。

### 事件对象

当用户在浏览器下出发了某个行为，会把触发这次事件的细节保存在一个对象中，这个对象称之为事件对象。

获取操作手指列表：
1. touches 位于屏幕上所有手指的列表
2. targetTouches 位于当前DOM元素上手指列表
3. changedTouches 触发当前事件手指列表




### Iscroll

初始：
html:
```
<div id="wrapper">
    <div id="scroller">
        <ul>
            <li>...</li>
            <li>...</li>
            ...
        </ul>
    </div>
</div>
```
启动滚动：
```
var myScroll = new IScroll('.wrapper');
```
### 核心参数

**scrollX**
默认值有Y轴可滚动，要开启X轴需要设置scrollX为true

**startX，startY**
默认开始定位在left，top的0,0位置，可以设置startX，startY，初始定位。

### 滚动条

**scrollbars**
默认为false，设置为true，开启滚动条。如果设置为*custom*，那么可以自定义滚动条，使用以下类改变滚动条的样式：
```
.iScrollHorizontalScrollbar，这个样式应用到横向滚动条的容器。这个元素实际上承载了滚动条。
.iScrollVerticalScrollbar，适用于纵向滚动条容器。
.iScrollIndicator，滚动条。
.iScrollBothScrollbars，这个样式将在双向滚动条显示的情况下被加载到容器元素上。通常情况下其中一个（横向或者纵向）是可见的
```

**fadeScrollbars**
默认为false，但因淡出滚动条。

**interactiveScrollbars**
默认为false，拖动滚动条与页面进行交互。

### 指示器（indicators）
在选项中写入：
```
{
    indicators:{
        el:element
    }
    
}
```

程序接口：
通过提供的方法控制滚动：
```
myScroll.scrollTo(x, y, time, easing) 滚动到指定位置
```

滚动到指定元素的位置：
```
myScroll.scrollToElement(el, time, offsetX, offsetY, easing)
```
> el:指定的元素
> 持续时间
> offsetX:X轴偏移
> offsetY:Y轴偏移
> easing: 动画类型

### 刷新方法

如果滚动元素的内部元素发生了变化，则需要重新计算，需要刷新：

> myScoll.refresh();
## API
[https://iiunknown.gitbooks.io/iscroll-5-api-cn/scrollers.html](https://iiunknown.gitbooks.io/iscroll-5-api-cn/scrollers.html)






