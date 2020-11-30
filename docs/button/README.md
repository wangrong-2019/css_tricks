# 按钮特效

撩人的按钮特效

### 特效

<buttonTemp/>

### HTML

```html
<div class="button sliding">滑箱</div>
<div class="button jelly">果冻</div>
<div class="button pulse">脉冲</div>
<div class="button flash">闪光</div>
<div class="button bubble">气泡</div>
```

### CSS

``` css
.button {
  display: inline-block;
  line-height: 1;
  white-space: nowrap;
  outline: none;
  border: none;
  color: white;
  position: relative;
  background-color: #7ec699;
  z-index: 1;
  -webkit-appearance: none;
  text-align: center;
  box-sizing: border-box;
  outline: none;
  margin: 6px 8px 4px 0;
  transition: 0.1s;
  font-weight: 500;
  -moz-user-select: none;
  -webkit-user-select: none;
  -ms-user-select: none;
  padding: 12px 20px;
  font-size: 14px;
}

/* 滑箱效果 */
.sliding::before {
  content: "";
  z-index: -1;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: #9acd32;
  transform-origin: center bottom;
  transform: scaleY(0);
  transition: transform 0.4s ease-in-out;
}

.sliding:hover::before {
  transform-origin: center top;
  transform: scaleY(1);
}

/* 果冻效果 */
.jelly:hover {
  animation: jelly 0.5s;
}

@keyframes jelly {
  0%,
  100% {
    transform: scale(1, 1);
  }

  25%,
  75% {
    transform: scale(0.9, 1.1);
  }

  50% {
    transform: scale(1.1, 0.9);
  }
}

/* 脉冲效果 */
.pulse::before {
  content: "";
  position: absolute;
  z-index: -1;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  border: 4px solid #7ec699;
  transform: scale(1);
  transform-origin: center;
}

.pulse:hover::before {
  transition: all 0.75s ease-out;
  border: 1px solid#e6f7ff;
  transform: scale(1.25);
  opacity: 0;
}

/* 闪光效果 */
.flash {
  overflow: hidden;
  top: 18px;
  --shine-width: 1.25em;
}

.flash::after {
  content: "";
  z-index: -1;
  position: absolute;
  background: #9acd32;
  /* 核心代码：位置一步步调整 */
  top: -50%;
  left: 0%;
  bottom: -50%;
  width: 1.25em;
  transform: translate3d(-200%, 0, 0) rotate(35deg);
}

.flash:hover::after {
  transition: transform 0.5s ease-in-out;
  transform: translate3d(500%, 0, 0) rotate(35deg);
}
/* 气泡效果 从中间向四周扩散 */
.bubble_01 {
  top: 18px;
  overflow: hidden;
}

.bubble_01::before {
  z-index: -1;
  content: "";
  position: absolute;
  top: 50%;
  left: 50%;
  width: 1em;
  height: 1em;
  border-radius: 50%;
  background-color: #9acd32;
  transform-origin: center;
  transform: translate3d(-50%, -50%, 0) scale(0, 0);
  transition: transform 0.45s ease-in-out;
}

.bubble_01:hover::before {
  transform: translate3d(-50%, -50%, 0) scale(15, 15);
}

/* 气泡效果 从左上角向右下角扩散 */
.bubble_02 {
  top: 18px;
  overflow: hidden;
}
.bubble_02::before {
  z-index: -1;
  content: "";
  position: absolute;
  width: 1em;
  height: 1em;
  border-radius: 50%;
  background-color: #9acd32;
  /* 变化位置的代码 */
  top: 0;
  left: 0;
  transform-origin: center;
  transform: scale3d(0, 0, 0);
  transition: transform 0.45s ease-in-out;
}

.bubble_02:hover::before {
  transform: scale3d(15, 15, 15);
}
```
