# 粘性球分享

带有融合粘滞效果的分享小交互

<gooeyShare/>

```html
<svg width="0" height="0">
  <defs>
    <filter id="goo">
      <feGaussianBlur
        in="SourceGraphic"
        stdDeviation="10"
        result="blur"
      ></feGaussianBlur>
      <feColorMatrix
        in="blur"
        mode="matrix"
        result="goo"
        values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 19 -9"
      ></feColorMatrix>
      <feComposite in="SourceGraphic" in2="goo" operator="atop"></feComposite>
    </filter>
  </defs>
</svg>
<input type="checkbox" id="share" />
<div class="target">
  <label class="share" for="share">分享</label>
  <span class="icon-share-weibo">
    <img src="/images/weibo.png" />
  </span>
  <span class="icon-share-wechat">
    <img src="/images/wechat.png" />
  </span>
  <span class="icon-share-qq">
    <img src="/images/qq.png" />
  </span>
</div>
```

```css
svg {
  position: absolute;
}
.target {
  height: 120px;
  max-width: 200px;
  filter: url("#goo");
  text-align: center;
  position: relative;
}
.share {
  display: block;
  width: 64px;
  line-height: 64px;
  background-color: #cd0000;
  color: #fff;
  border-radius: 50%;
  margin: auto;
  cursor: pointer;
  position: relative;
  z-index: 1;
}
[type="checkbox"] {
  position: absolute;
  clip: rect(0 0 0 0);
}
[class*="icon-share-"] {
  position: absolute;
  width: 48px;
  height: 48px;
  background-color: #cd0000;
  border-radius: 50%;
  transition: transform 0.5s;
  top: 8px;
  left: 0;
  right: 0;
  margin: auto;
  cursor: pointer;
  -ms-transform: scale(0.5);
  transform: scale(0.5);
}
[class*="icon-share-"] > img {
  display: block;
  width: 20px;
  height: 20px;
  margin: 14px auto;
}
:checked + .target .icon-share-weibo {
  -ms-transform: scale(1) translate(-70px, 60px);
  transform: scale(1) translate(-70px, 60px);
}
:checked + .target .icon-share-wechat {
  -ms-transform: scale(1) translate(0, 75px);
  transform: scale(1) translate(0, 75px);
}
:checked + .target .icon-share-qq {
  -ms-transform: scale(1) translate(70px, 60px);
  transform: scale(1) translate(70px, 60px);
}
:checked + .target .share {
  animation: jello 1s;
}
@keyframes jello {
  from,
  11.1%,
  to {
    transform: none;
  }
  22.2% {
    transform: skewX(-12.5deg) skewY(-12.5deg);
  }
  33.3% {
    transform: skewX(6.25deg) skewY(6.25deg);
  }
  44.4% {
    transform: skewX(-3.125deg) skewY(-3.125deg);
  }
  55.5% {
    transform: skewX(1.5625deg) skewY(1.5625deg);
  }
  66.6% {
    transform: skewX(-0.78125deg) skewY(-0.78125deg);
  }
  77.7% {
    transform: skewX(0.390625deg) skewY(0.390625deg);
  }
  88.8% {
    transform: skewX(-0.1953125deg) skewY(-0.1953125deg);
  }
}
```
