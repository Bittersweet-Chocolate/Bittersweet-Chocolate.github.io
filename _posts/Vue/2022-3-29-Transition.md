---
layout:     post
title:      Transition-group
subtitle:   Vue和Animate设置列表动画
date:       2020-3-29
author:     BY czh
header-img: img/desk.jpg
catalog: true
tags:
    - vue
    - vue transition-group
---

###  Vue transition-group

版本：@vue/cli 4.2.3

目的：利用`animate.css`和Vue自带组件`transition-group`设置列表动画

起手式：

```
 <transition-group
        enter-active-class="animated bounceInLeft"
        @before-enter="beforeEnter"
      >
        <li
          v-for="(item,index) in topInfo.tracks"
          :key="item.id"
          :data-index="index"
        >
        </li>
</transition-group>     
```

#### 元素绑定动画

上面例子使用了animate.css给enter-active-class加入了`animated bounceInLeft`。

同时使用了`before-enter`钩子函数在v-for循环时对每个元素的style中的animationDelay进行延时。这里对li元素中的data-index属性对循环中的下标绑定。便于`before-enter`钩子函数拿到每个li元素进行对应的延时设定。形成每个元素分别执行动画。

###### before-enter取值

```
beforeEnter(el) {
	// el 即每次循环的元素
      let delayNum = "." + el.dataset.index * 100 + "s";
      el.style.animationDelay = delayNum;
}
```



