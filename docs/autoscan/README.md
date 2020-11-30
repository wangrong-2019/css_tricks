# 图片识别扫描图

<autoscan/>

```html
<div class="autoscan-container">
  <img src="/images/timg.jpg" alt="人像图片" class="bg" />
  <div class="autoscan"></div>
</div>
```

```css
.autoscan-container {
  position: relative;
  margin: 15px 0;
}
.bg {
  width: 200px;
  display: block;
}
.autoscan {
  position: absolute;
  width: 200px;
  height: 200px;
  top: 0;
  left: 0;
  background: linear-gradient(#03a9f4, #03a9f4),
    linear-gradient(90deg, #ffffff33 1px, transparent 0, transparent 19px),
    linear-gradient(#ffffff33 1px, transparent 0, transparent 19px),
    linear-gradient(transparent, #2196f3);
  background-size: 100% 1.5%, 10% 100%, 100% 10%, 100% 100%;
  background-position: 0 0, 0 0, 0 0, 0 0;
  background-repeat: no-repeat, repeat, repeat, repeat;
  clip-path: polygon(0% 0%, 100% 0%, 100% 1.5%, 0% 1.5%);
  animation: move 1.5s linear infinite;
}
@keyframes move {
  to {
    background-position: 0 100%, 0 0, 0 0, 0 0;
    clip-path: polygon(0% 0%, 100% 0%, 100% 100%, 0% 100%);
  }
}
```
