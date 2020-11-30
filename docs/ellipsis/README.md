# 文本省略

## 单行文字

<ellipsis-single/>

```scss
// 注意宽度是必须的
.article-container {
  width: 500px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```

## 多行文字

<ellipsis-multiple/>

```scss
.article-container {
  display: -webkit-box;
  word-break: break-all;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 4; //需要显示的行数
  overflow: hidden;
  text-overflow: ellipsis;
}
```

## float 特性实现多行文本截断

<ellipsis-float/>

```scss
.text-wrap {
  height: 60px;
  line-height: 20px;
  overflow: hidden;
}
.text-wrap .text {
  float: right;
  margin-left: -5px;
  width: 100%;
  word-break:break-all;
}
.text-wrap::before {
  float: left;
  width: 5px;
  content: '';
  height: 60px;
}
.text-wrap::after {
  float: right;
  content: "...";
  height: 20px;
  line-height: 20px;
  padding-right: 5px;
  text-align: right;
  width: 3em;
  margin-left: -3em;
  position: relative;
  left: 100%;
  top: -20px;
  /* 显示更好的效果 */
  background: -webkit-gradient(linear, left top, right top, from(rgba(255, 255, 255, 0)), to(white), color-stop(50%, white));
  background: -moz-linear-gradient(to right, rgba(255, 255, 255, 0), white 50%, white);
  background: -o-linear-gradient(to right, rgba(255, 255, 255, 0), white 50%, white);
  background: -ms-linear-gradient(to right, rgba(255, 255, 255, 0), white 50%, white);
  background: linear-gradient(to right, rgba(255, 255, 255, 0), white 50%, white);
}

```

## Checked伪类实现展开与隐藏切换

<ellipsis-switch/>

```html
<div class="ellipsis-container">
    <input type="checkbox" name="toggle" id="toggle" style="display: none;">
    <div class="text-wrap">
      <div class="text">吾尝终日而思矣，不如须臾之所学也...</div>
    </div>
    <label for="toggle" class="button pulse"></label>
  </div>
```

```scss
button{
  &::after {
    content: "显示更多";
  }
}
input[name="toggle"]:checked {
  & + div {
    height: auto;
    &::after {
      display: none;
    }
  }
   & ~ label {
    &::after {
      content: "收起文本";
    }
  }
}
```