# clip-path 转场动画

`clip-path:` 就是裁剪路径，使用 SVG 或形状定义一个 HTML 元素的可见区域的方法。
:::tip
注意: IE 浏览器不支持，且低版本 webkit 内核浏览器需要添加-webkit-前缀
:::

## 基本图形

- 矩形： inset(top,right,bottom,left round border-radius)，例如：inset(2px 5px 4px 5px round 4px)；
- 圆： circle(半径 at 圆心位置 X 圆心位置 Y)，例如：circle(30% at 150px 120px);
- 椭圆: ellipse(X 轴半径 Y 轴半径 at 中心位置 X 中心位置 Y)，例如：ellipse(45% 30% at 50% 50%);

<clipPath-basic/>

```css
.inset {
  animation: inset 0.6s;
}

@keyframes inset {
  0% {
    clip-path: inset(50% round 10% 50%);
  }
  100% {
    clip-path: inset(0% round 0);
  }
}

.circle {
  animation: circle 0.6s;
}

@keyframes circle {
  0% {
    clip-path: circle(0% at 50% 50%);
  }
  100% {
    clip-path: circle(80% at 50% 50%);
  }
}

.ellipse {
  animation: ellipse 0.6s;
}

@keyframes ellipse {
  0% {
    clip-path: ellipse(0% 0% at 50% 50%);
  }
  100% {
    clip-path: ellipse(90% 80% at 50% 50%);
  }
}
```

## 自定义图形

<clipPath-polygon/>

```css
.sanjiao { /*三角形*/
  animation: sanjiao 0.6s;
}
@keyframes sanjiao {
  0% {
    clip-path: polygon(50% 50%, 49% 51%, 51% 51%);
  }
  100% {
    clip-path: polygon(50% -100%, -100% 200%, 200% 200%);
  }
}
.lingxing { /*菱形*/
  animation: lingxing 0.6s;
}
@keyframes lingxing {
  0% {
    clip-path: polygon(50% 50%, 50% 50%, 50% 50%, 50% 50%);
  }
  100% {
    clip-path: polygon(50% -50%, 150% 50%, 50% 150%, -50% 50%);
  }
}
.shizixing { /*十字星*/
  animation: shizixing 0.6s;
}
@keyframes shizixing {
  0% {
    clip-path: polygon(
      50% 20%, 50% 50%, 20% 50%, 50% 50%,
      50% 80%, 50% 50%, 80% 50%, 50% 50%
    );
  }
  100% {
    clip-path: polygon(
      50% 0%, 0% 0%, 0% 50%, 0% 100%,
      50% 100%, 100% 100%, 100% 50%, 100% 0%
    );
  }
}
.shanxing { /*扇形展开*/
  animation: shanxing 0.6s linear;
}
@keyframes shanxing {
  0% {
    clip-path: polygon(50% 100%, 50% 0%, 0% 0%, 100% 0%, 50% 0%);
  }
  50% {
    clip-path: polygon(50% 100%, 0% 0%, 0% 0%, 100% 0%, 100% 0%);
  }
  100% {
    clip-path: polygon(50% 100%, 0% 100%, 0% 0%, 100% 0%, 100% 100%);
  }
}
.wujiaoxing { /*五角星扩展*/
  mask: url(/images/star.svg) no-repeat center;
  mask-size: 380% 380%; /* Safari没有这个类似“初始化”的东西居然无效 */
  animation: wujiaoxing 1s both;
}
@keyframes wujiaoxing {
  from {
    mask-size: 0 0;
  }
  to {
    mask-size: 380% 380%;
  }
}
.aixing { /*爱心放大*/
  mask: url(/images/heart.svg) no-repeat center;
  mask-size: 200% 300%;    
  animation: aixing 1s both;
}
@keyframes aixing {
  from { mask-size: 0 0; }
  to   { mask-size: 250% 350%; }
}
```

## 平铺图形

<clipPath-tile/>

```scss
.largen { /*圆点放大*/
   mask: radial-gradient(#000 calc(1% * var(--largen)), transparent calc(1% * var(--largen)));
    mask-size: 30px 30px;
    animation: largen .6s;
}
@keyframes largen {
  @for $i from 0 through 100 {
    #{$i}% {--largen:#{$i}}
  }
}

.bevell { /*三角斜切*/
  mask: linear-gradient(135deg, #000 calc(1% * var(--bevell)), transparent calc(1% * var(--bevell)));
    mask-size: 30px 30px;
    animation: bevell .6s;
}
@keyframes bevell {
  @for $i from 0 through 100 {
    #{$i}% {--bevell:#{$i}}
  }
}

.window { /*百叶窗*/
    mask: linear-gradient(to right, #000 calc(1% * var(--window)), transparent calc(1% * var(--window)));
    mask-size: 20px;
    animation: window .6s;
}
@keyframes window {
  @for $i from 0 through 100 {
    #{$i}% {--window:#{$i}}
  }
}

.rotate { /*车轮转动*/
    mask: conic-gradient(#000 calc(1% * var(--rotate)), transparent calc(1% * var(--rotate)));
    mask-size: 30px 30px;
    animation: rotate .6s;
}
@keyframes rotate {
  @for $i from 0 through 100 {
    #{$i}% {--rotate:#{$i}}
  }
}
```

:::tip
[species-in-pieces.com](http://species-in-pieces.com "species-in-pieces.com") 是世界一家知名的宣传濒危动物保护网站，主要使用clip-path polygon实现了30个动物及30种变换。
:::