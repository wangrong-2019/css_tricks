# 色彩的流动

-----------------

<colorFlow/>

```html
<h3 class="flow-slogon">颜色的流动与色调变化</h3>
```

```css
.flow-slogon {
    font-size: 70px;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-image: linear-gradient(to right, red, yellow, lime, aqua, blue, fuchsia);
    animation: hue 5s linear infinite;
}
@keyframes hue {
    from { filter: hue-rotate(0deg); }
    to { filter: hue-rotate(360deg); }
}
```
