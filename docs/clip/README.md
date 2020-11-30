# clip 裁剪

## 属性

`clip:rect(top ,right,bottom,left)`

`top：` 矩形上长对应父元素上长的距离(上长就是矩形上边的长)

`right：` 矩形右宽对应父元素左宽的距离(右宽就是矩形右边的宽)

`bottom:`矩形下长对应父元素上长的距离

`left：`矩形左宽对应父元素左宽的距离

<img src="/images/clip.png">

## 蛇形边框

<clip/>

```html
<div class="snakelike-border"></div>
```

```scss
.snakelike-border {
  position: relative;
  width: 190px;
  height: 190px;
  background-color: #7ec699;
  &::before,
  &::after {
    position: absolute;
    left: -5px;
    right: -5px;
    top: -5px;
    bottom: -5px;
    border: 5px solid;
    content: "";
    animation: move 5s linear infinite;
  }
  &::before {
    border-color: #f66;
  }
  &::after {
    border-color: #66f;
    animation-delay: -2.5s;
  }
}
@keyframes move {
  0%,
  100% {
    clip: rect(0 200px 5px 0);
  }
  25% {
    clip: rect(0 200px 200px 195px);
  }
  50% {
    clip: rect(195px 200px 200px 0);
  }
  75% {
    clip: rect(0 5px 200px 0);
  }
}
```
