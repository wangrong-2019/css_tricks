# 阴影技巧

## 投影背景 / 背景动画

<shadow-shadow1/>

```html
<div class="shadow"></div>
```

```css
.shadow {
  position: relative;
  width: 250px;
  height: 250px;
  border: 1px solid #333;
  box-sizing: border-box;
  margin: 20px;
  float: left;
  overflow: hidden;
  &::before {
    content: "";
    position: absolute;
    width: 50px;
    height: 50px;
    top: -50px;
    left: -50px;
    box-shadow: 50px 50px, 150px 50px, 250px 50px, 50px 100px, 150px 100px, 250px
        100px, 50px 150px, 150px 150px, 250px 150px, 50px 200px, 150px 200px, 250px
        200px, 50px 250px, 150px 250px, 250px 250px;
    animation: move 3s infinite linear;
  }
}

@keyframes move {
  25% {
    transform: translate(50px);
    color: coral;
    box-shadow: 50px 50px, 150px 50px, 250px 50px, 50px 100px, 150px 100px, 250px
        100px, 50px 150px, 150px 150px, 250px 150px, 50px 200px, 150px 200px, 250px
        200px, 50px 250px, 150px 250px, 250px 250px;
  }
  50% {
    transform: translate(0px);
    color: brown;
    border-radius: 0;
    box-shadow: 50px 50px, 150px 50px, 250px 50px, 100px 100px, 200px 100px, 300px
        100px, 50px 150px, 150px 150px, 250px 150px, 100px 200px, 200px 200px, 300px
        200px, 50px 250px, 150px 250px, 250px 250px;
  }
  75% {
    transform: translate(0px);
    color: teal;
    border-radius: 50%;
    box-shadow: 50px 50px, 150px 50px, 250px 50px, 100px 100px, 200px 100px, 300px
        100px, 50px 150px, 150px 150px, 250px 150px, 100px 200px, 200px 200px, 300px
        200px, 50px 250px, 150px 250px, 250px 250px;
  }
  100% {
    border-radius: 0%;
    box-shadow: 50px 50px, 150px 50px, 250px 50px, 50px 100px, 150px 100px, 250px
        100px, 50px 150px, 150px 150px, 250px 150px, 50px 200px, 150px 200px, 250px
        200px, 50px 250px, 150px 250px, 250px 250px;
  }
}
```

## 立体投影

<shadow-shadow2/>

```html
<div>Txt Shadow</div>
<div class="left">TxT Long Shadow</div>
```

```css
@function makelongrightshadow($color) {
  $val: 0px 0px $color;
  @for $i from 1 through 50 {
    $color: fade-out(desaturate($color, 1%), 0.02);
    $val: #{$val}, #{$i * 0.5}px #{$i * 0.5}px #{$color};
  }
  @return $val;
}

@function makelongleftshadow($color) {
  $val: 0px 0px $color;
  @for $i from 1 through 50 {
    $color: fade-out(desaturate($color, 1%), 0.02);
    $val: #{$val}, -#{$i * 0.5}px #{$i * 0.5}px #{$color};
  }
  @return $val;
}

div {
  text-align: center;
  font-size: 50px;
  line-height: 1.5;
  text-shadow: makelongrightshadow(hsla(14, 100%, 30%, 1));
  color: hsl(14, 100%, 60%);
}

.left {
  text-shadow: makelongleftshadow(hsla(231, 50%, 30%, 1));
  color: hsl(231, 50%, 60%);
}
```

## 长投影

<shadow-shadow3/>

```html
<div class="shadow3"></div>
```

```css
.shadow3 {
  position: relative;
  width: 100px;
  height: 100px;
  background: #ddd;
  margin: 10px auto 80px;
}

.shadow3::before,
.shadow3::after {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

.shadow3::before {
  transform-origin: 0 50%;
  transform: translate(100%, 0) skewY(45deg) scaleX(0.6);
  background: linear-gradient(90deg, rgba(0, 0, 0, 0.3), transparent);
  animation: shadowMoveY 2s infinite linear alternate;
}

.shadow3::after {
  transform-origin: 0 0;
  transform: translate(0%, 100%) skewX(45deg) scaleY(0.6);
  background: linear-gradient(180deg, rgba(0, 0, 0, 0.3), transparent);
  animation: shadowMoveX 2s infinite linear alternate;
}
@keyframes shadowMoveX {
  to {
    transform: translate(0%, 100%) skewX(50deg) scaleY(0.6);
  }
}

@keyframes shadowMoveY {
  to {
    transform: translate(100%, 0) skewY(40deg) scaleX(0.6);
  }
}
```

## 彩色投影

<shadow-shadow4/>

```html
<div class="container">
  <div class="avator"></div>
  <p>bulr shadow</p>
</div>
```

```scss
$img: "https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1505822443&di=941986df9c6514d5d43eaba4aa938347&imgtype=jpg&er=1&src=http%3A%2F%2Fimg.qqtouxiang8.net%2Fuploads%2Fallimg%2Fc150313%2F142623130563050-922006.jpg";

@import url(https://fonts.googleapis.com/css?family=Righteous);

.container {
  width: 200px;
  margin: 20px auto;
}

.avator {
  position: relative;
  width: 200px;
  height: 200px;
  border-radius: 50%;
  background: url($img) no-repeat center center;
  background-size: 100% 100%;

  &::after {
    content: "";
    position: absolute;
    top: 10%;
    left: 0%;
    width: 100%;
    height: 100%;
    background: inherit;
    background-size: 100% 100%;
    border-radius: 50%;
    transform: scale(0.95);
    filter: blur(10px) brightness(80%) opacity(0.8);
    z-index: -1;
  }
}

p {
  margin-top: 30px;
  text-align: center;
  font-size: 28px;
  font-family: Righteous;
}
```

## 霓虹氖灯文字效果

<shadow-shadow5/>

```html
<div class="shadow5-container">
  <p class="pink">PINK</p>
  <p class="orange">Box-Shadow</p>
</div>
```

```scss
@import url("https://fonts.googleapis.com/css?family=Lobster");
.shadow5-container {
  display: flex;
  justify-content: space-around;
  background: #282c34;
  margin: 10px auto;
  border-radius: 6px;
}
p {
  font-family: "Lobster";
  text-align: center;
  font-size: 50px;
  line-height: 60px;
  color: #fff;
  cursor: pointer;
  text-align: center;
  &:hover {
    color: #fff;
  }
}

.pink {
  filter: brightness(110%);
  text-shadow: 0 0 5px #fff, 0 0 10px #fff, 0 0 15px #fff, 0 0 20px #e91e63,
    0 0 35px #e91e63, 0 0 40px #e91e63, 0 0 50px #e91e63, 0 0 75px #e91e63;
  animation: pink 1.5s ease-in-out infinite alternate;
}

.orange {
  color: #ff5722;
}

.orange:hover {
  animation: orange 1.5s ease-in-out infinite alternate;
}
@keyframes pink {
  to {
    text-shadow: 0 0 10px #fff, 0 0 20px #fff, 0 0 30px #fff, 0 0 40px #e91e63,
      0 0 70px #e91e63, 0 0 80px #e91e63, 0 0 100px #e91e63, 0 0 150px #e91e63;
  }
}

@keyframes orange {
  to {
    text-shadow: 0 0 10px #fff, 0 0 20px #fff, 0 0 30px #fff, 0 0 40px #ff5722,
      0 0 70px #ff5722, 0 0 80px #ff5722, 0 0 100px #ff5722, 0 0 150px #ff5722;
  }
  from {
    filter: brightness(110%);
    text-shadow: 0 0 5px #fff, 0 0 10px #fff, 0 0 15px #fff, 0 0 20px #ff5722,
      0 0 35px #ff5722, 0 0 40px #ff5722, 0 0 50px #ff5722, 0 0 75px #ff5722;
  }
}
```

## 阴影灯光 show

<shadow-shadow6/>

```html
<div class="shadow6">
  <div class="shadow-text">BOX-SHADOW<br />LIGHTS</div>
</div>
```

``` scss
@import url("https://fonts.googleapis.com/css?family=Lobster");

.shadow6 {
    perspective: 500px;
    background: #282c34;
    height: 180px;
    position: relative;
}

.shadow-text {
    position: absolute;
    left: 38%;
    top: 50px;
    color: #fff;
    font-family: "Lobster", sans-serif;
    font-size: 40px;
    line-height: 1;
    transform: translate(-40px) rotateX(25deg) rotateY(20deg) rotateZ(-3deg);
    position: absolute;
    animation: changeColor 3s linear infinite alternate;
}

@keyframes changeColor {
    0% {
        text-shadow: -6px 4px 0px #e91e63;
    }
    10% {
        text-shadow: 4px -6px 0px #00ff0a;
    }
    20% {
        text-shadow: -9px 4px 0px #0b3cff;
    }
    30% {
        text-shadow: 4px -6px 0px #ffe926;
    }
    40% {
        text-shadow: -8px 4px 0px #f19000;
    }
    50% {
        text-shadow: 4px 5px 0px #e9a48b;
    }
    60% {
        text-shadow: -6px 4px 0px #e9eced;
    }
    70% {
        text-shadow: 4px 7px 0px #e028ff;
    }
    80% {
        text-shadow: -9px -4px 0px #5af4e5;
    }
    90% {
        text-shadow: 4px -6px 0px #3c59f8;
    }
    100% {
        color: #000;
        transform: translate(-40px) rotateX(15deg) rotateY(10deg) rotateZ(-5deg);
        text-shadow: -9px 4px 0px #d7d7d7;
    }
}
```
