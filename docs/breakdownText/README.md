# 显示器故障文本模拟

<breakdownText/>

```html
<div class="text-container">
  <div class="text" data-text="ERROR">ERROR</div>
</div>
```

```scss
.text-container {
  margin: 20px 0;
  height: 200px;
  background-color: #282c34;
  display: flex;
  justify-content: center;
  align-items: center;
}
.text {
  position: relative;
  font-weight: bold;
  font-size: 100px;
  color: #fff;
  &::before,
  &::after {
    overflow: hidden;
    position: absolute;
    top: 0;
    background-color: #282c34;
    clip: rect(0, 900px, 0, 0);
    color: #fff;
    content: attr(data-text);
    animation: shake 3s linear infinite alternate-reverse;
  }
  &::before {
    left: -2px;
    text-shadow: 1px 0 #09f;
  }
  &::after {
    left: 2px;
    text-shadow: -1px 0 #f66;
    animation-duration: 2s;
  }
}
@keyframes shake {
  $steps: 20;
  @for $i from 0 through $steps {
    #{percentage($i * (1 / $steps))} {
      clip: rect(random(100) + px, 9999px, random(100) + px, 0);
    }
  }
}
```
