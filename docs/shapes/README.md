# shapes 布局

`shape-outside:`可以让内联元素以不规则的形状进行外部排列,需要和浮动配合使用。

## 属性

```css
/* 关键字值 */
shape-outside: none;
shape-outside: margin-box;
shape-outside: content-box;
shape-outside: border-box;
shape-outside: padding-box;
/* 函数值 */
shape-outside: circle();
shape-outside: ellipse();
shape-outside: inset(10px 10px 10px 10px);
shape-outside: polygon(10px 10px, 20px 20px, 30px 30px);

/* <url>值 */
shape-outside: url(image.png);

/* 渐变值 */
shape-outside: linear-gradient(45deg, rgba(255, 255, 255, 0) 150px, red 150px);
```

## 平行四边形布局

<shapes-parallelogram/>

```html
<div class="shape-left"></div>
<div class="shape-right"></div>
<div class="content">
  <p>
    在CSS
    Shapes布局问世之前，文字像杂志一样的任意形状的排版几乎是不可能的，一直都是用网格、盒子和直线构造。
  </p>
  <p>
    CSS
    Shapes允许我们定义文本环绕的几何形状。这些形状可以是圆、椭圆、简单或复杂的多边形，甚至是任意的图像和多彩的渐变。
  </p>
</div>
```

```css
.shape-left {
  float: left;
  width: 130px;
  height: 200px;
  shape-outside: polygon(0 0, 100% 0, 0% 100%);
}
.shape-right {
  float: right;
  width: 130px;
  height: 200px;
  shape-outside: polygon(100% 0, 100% 100%, 0 100%);
}

.content {
  display: block;
  padding: 1px;
  position: relative;
  z-index: 0;
  height: 200px;
  box-sizing: border-box;
}

.content::before {
  content: "";
  position: absolute;
  background-color: #fff;
  transform: skewX(-33deg);
  left: 50px;
  right: 50px;
  top: 0;
  bottom: 0;
  border: 1px solid #ddd;
  z-index: -1;
  box-sizing: border-box;
}
```

## 环绕iPhone X刘海效果

<shapes-bangs />

```html
<div class="bangs-box">
  <i class="liuOutside"></i>
  <i class="liuhai"></i>
  <ul class="scrollContent">
    <li>这个方法是比较简单的</li>
    <li>使用shape-outside url(image.png)语法</li>
    <li>其中'image.png'就是用来被环绕的图片</li>
    <li>环绕与否是基于计算alpha通道决定</li>
    <li>即沿着图片非透明区域环绕</li>
    <li>为了不至于列表靠的太近</li>
    <li>shape的url图片右侧</li>
    <li>刻意填充了6像素实色</li>
    <li>现在看到的齐刘海</li>
    <li>是覆盖在上面的一张图</li>
    <li>实际生效的是后面浮动的shape</li>
    <li>此功能的实现需要JS的配合</li>
    <li>主要控制margin-top值</li>
    <li>只能对内联信息进行跟随控制</li>
  </ul>
</div>
```

```js
var liuOutside = document.querySelector(".liuOutside");
var box = document.querySelector(".bangs-box");
var outside = function() {
  var scrollTop = box.scrollTop;
  liuOutside.style.marginTop = 100 + scrollTop + "px";
  liuOutside.style.shapeOutside =
    "polygon(0 0, 0 " +
    (100 + scrollTop) +
    "px, 16px " +
    (104 + scrollTop) +
    "px, 30px " +
    (116 + scrollTop) +
    "px, 30px " +
    (264 + scrollTop) +
    "px, 16px " +
    (276 + scrollTop) +
    "px, 0 " +
    (280 + scrollTop) +
    "px, 0 0)";
};
// 滚动时实时监听改变shape的形状
box.addEventListener("scroll", outside);
outside();
```

```css
.bangs-box {
  max-width: 600px;
  height: 380px;
  border: 2px solid #000;
  overflow: auto;
  margin: 20px auto 0;
  border-radius: 4px;
}
.liuOutside {
  float: left;
  width: 30px;
  height: 180px;
}
.liuhai {
  width: 24px;
  height: 180px;
  background: url("/images/liu.webp") no-repeat left center;
  margin-top: 100px;
  position: absolute;
}
.scrollContent {
  list-style: none;
  margin: 0;
  padding: 0;
}
.scrollContent li {
  border-bottom: 1px solid #ddd;
  padding: 1em;
}
```
