# resize 调整尺寸

## 属性

`resize: none | both | horizontal | vertical;`

| 值 | 描述 |
| ---- | ---- |
| none | 用户无法调整元素的尺寸。 |
|both | 用户可调整元素的高度和宽度。 |
| horizontal | 用户可调整元素的宽度。|
| vertical | 用户可调整元素的高度。 |

## 拉伸分栏

<stretching/>

```html
<div class="stretching-column">
    <div class="left">
    <div class="resize-bar"></div>
    <div class="resize-line"></div>
    <div class="resize-text">resize属性指定一个元素是否是由用户调整大小的。</div>
    </div>
    <div class="right">
        如果希望此属性生效，需要设置对象的overflow属性，值可以是auto,hidden或scroll。
    </div>
</div>
```

```scss
.stretching-column {
  overflow: hidden;
  border: 1px solid #2c3e50;
  width: 600px;
  height: 300px;
  line-height: 20px;
  font-size: 16px;
  .left {
    overflow: hidden;
    float: left;
    position: relative;
    height: 100%;
  }
  .right {
    overflow: hidden;
    padding: 10px;
    height: 100%;
    background-color: #f0f0f0;
    word-break: break-all;
  }
}
.resize-bar {
  overflow: scroll;
  width: 200px;
  height: 100%;
  opacity: 0;
  resize: horizontal;
  &::-webkit-scrollbar {
    width: 200px;
    height: 100%;
  }
  &:hover,
  &:active {
    & ~ .resize-line {
      border-left: 1px dashed #2c3e50;
    }
  }
}
.resize-line {
  position: absolute;
  right: 0;
  top: 0;
  bottom: 0;
  border-left: 1px solid #ccc;
  border-right: 2px solid #f0f0f0;
  pointer-events: none;
}
.resize-text {
  overflow-x: hidden;
  position: absolute;
  left: 0;
  right: 5px;
  top: 0;
  bottom: 0;
  padding: 10px;
  word-break: break-all;
}
```
