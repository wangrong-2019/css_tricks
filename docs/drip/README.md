# 水滴落下

<drip/>

```html
<div class="drip-container">
  <div class="drip">MAGICCSS</div>
</div>
```

```scss
.drip-container {
  height: 250px;
  overflow: hidden;
  background: #282c34;
  filter: blur(3px) contrast(10);

  .drip {
    position: relative;
    width: 485px;
    height: 105px;
    color: #fff;
    font-size: 100px;
    text-align: center;
    margin: 25px auto 0;
    border-bottom: 10px solid #fff;
    transform: skewY(5deg);

    &::before {
      position: absolute;
      content: "";
      bottom: -20px;
      width: 10px;
      height: 20px;
      border-radius: 50%;
      background: #fff;
      transform: translate(0, 0);
      animation: move 7.5s ease-in-out infinite;
    }

    &::after {
      position: absolute;
      content: "";
      left: 0;
      bottom: -20px;
      width: 10px;
      height: 20px;
      border-radius: 50%;
      background: #fff;
      transform: translate(0, 0);
      animation: move 7.5s ease-in-out 1s infinite;
    }
  }
}

@keyframes move {
  80% {
    bottom: -25px;
    transform: translate(468px, 0);
  }
  93% {
    transform: translate(468px, 3px);
    opacity: 1;
  }
  100% {
    transform: translate(468px, 150px);
    opacity: 0;
  }
}
```
