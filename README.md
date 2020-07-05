# 2020project created by ccz  20200625

### css动画基础

1. 过渡动画 transition  在鼠标悬移或者离开下css属性发生的改变

应用：

hover  active  focus

```
    div:hover{width:200px}

    div:active{width:200px}

    div:focus{width:200px}

```


语法：

transition : transition-property  transition-duration transition-timing-function  transition-delay

默认值：	all 0s ease 0s

简写属性

transition是上面四个过渡属性的简写，其中只有transition-duration是必填属性。

```
transition: 1s;
transition: all 5s linear .2s; // 以空格隔开属性
transition: all 5s linear .2s, height 3s ease-in-out; // 可以以逗号隔开多个过渡。
```

可过渡的样式
不是所有的CSS样式值都可以过渡，只有具有中间值的属性才具备过渡效果
```
    颜色: color background-color border-color outline-color
    位置: backround-position left right top bottom
    长度:
        [1]max-height min-height max-width min-width height width
        [2]border-width margin padding outline-width outline-offset
        [3]font-size line-height text-indent vertical-align  
        [4]border-spacing letter-spacing word-spacing
    数字: opacity visibility z-index font-weight zoom
    组合: text-shadow transform box-shadow clip
    其他: gradient

```

####  transition-property: 规定设置过渡效果的css属性的名称

语法：transition-property : none（默认值） | all |property


实例：

```
    div{transition-property:width;width:100px;}

    div:hover{width:200px}

```
```
    transition-property: all; // 默认为all，所有可被动画的属性都表现出过渡动画。

    transition-property: none; // 没有动画效果

    transition-property: width, height; //也可以取其他属性的值

```


#### transition-duration: 规定完成过渡效果需要多少秒或者毫秒 必填项 必须带单位

语法：

    transition-duration: ns | ms  默认值为0(表示不出现过渡动画)

    ```
        transition-duration: 1s;

        transition-duration: 1ms;

        transition-duration: 1s, 10s, 10ms; // 可以应用多个值，
        对应于transition-property的多个属性，表示每个属性对应的延时时间

    ```


#### transition-timing-function:规定速度效果的速度曲线

语法： transition-timing-function :linear | ease | ease-in | ease-out | ease-in-out | cubic-bezier(n,n,n,n)

```
    cubic-bezier(n, n, n, n); // 在bezier 函数中自定义 0 ~ 1 之间的数值

    ease; // 默认值，慢速开始，中间变快，慢速结束；相当于 cubic-bezier(0.25, 0.1, 0.25, 1)。

    linear; // 匀速运动；相当于 cubic-bezier(0, 0, 1, 1)。

    ease-in; // 慢速开始；相当于 cubic-bezier(0.42, 0, 1, 1)。

    ease-out; // 慢速结束；相当于 cubic-bezier(0, 0, 0.58, 1)

    ease-in-out; // 慢速开始，慢速结束；相当于 cubic-bezier(0.42, 0, 0.58, 1)

    step-start; //steps(1, start)

    step-end; //steps(1, end)

    steps(4, end);
    steps(4, start);

```

### 注意事项

1.属性值不要为auto

属性值不要从auto开始或者变到auto，因为不同浏览器不同版本效果可能不一样

2.对新增的DOM元素延迟应用过渡

不要在添加DOM元素，或者去掉display: none之后立即应用过渡，将没有过渡效果，只呈现最终态。可以通过延迟改变属性值来打破这个限制


3.不支持循环

transition没有循环，只是从初态到终态，animation有循环

4.子属性值数目自动匹配

如果各子属性值数目不一致，会自动重复填满或者截断，例如：

```
div {
  transition-property: opacity, left, top, height;
  transition-duration: 3s, 5s;
}
/*等价于*/
div {
  transition-property: opacity, left, top, height;
  transition-duration: 3s, 5s, 3s, 5s;
}

div {
  transition-property: opacity, left;
  transition-duration: 3s, 5s, 2s, 1s;
}
/*等价于*/
div {
  transition-property: opacity, left;
  transition-duration: 3s, 5s;
}
```

5.事件

过渡结束时触发transitionend事件，如下：

el.addEventListener('transitionend', callback);

事件对象携带3个特殊属性

propertyName 已完成过渡的属性名

elapsedTime 过渡执行的秒数，不受delay影响

pseudoElement 以::开头的伪元素名，只在给伪元素应用transition时才不为空串

特别注意：如果过渡执行期间，元素被display: none或者正在过渡的属性被改变了，就不会触发该事件

6.支持transition的属性

也叫animatable属性，因为animation用的也是这份属性表，具体见CSS Transitions，简单整理如下：

```
background相关：color, position
border相关：color, width，border-spacing（表格专用），可以给4条边分别应用transition，比如border-left-color
布局相关：[max- | min-]width, [max- | min-]height, top, left, bottom, right, margin-*, padding-*
文本相关：color, font-size, font-weight, letter-spacing, line-height, text-indent, text-shadow, vertical-align, word-spacing
显示隐藏相关：opacity, visibility, z-index
outline相关：color, offset, width
其它：clip（能裁剪出方图片，还支持动画）, crop（不知道是什么东西）
还有一些属性，据说支持性取决于浏览器内核：

background-size
border-*-radius
box-shadow
column-count, column-gap, column-rule-color, column-rule-width, column-width
font-size-adjust, font-stretch, marker-offset, text-decoration-color
transform, transform-origin

```




#### transition-delay:定义过度效果何时开始 默认为0

语法： transition-delay : ns | ms




2. 变换动画transform



3. 关键帧动画 keyframes 



4. Animation 动画