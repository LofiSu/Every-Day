![[7cc2096471e079b621d8d2727960dfa3.mp4]]

>之前我只知道用JS监听事件实现顶部广告栏，今天复习CSS定位才发现sticky一行代码就解决了！

## 效果演示：
![[20240804-0324-49.1277556.mp4]]
### 代码：
```html
  <style>
      body {
        margin: 0;
      }
      .wrapper {
        height: 60px;
        background-color: rgba(250, 250, 250, 0.7);
        position: sticky;//粘性定位
        top: 0;//当用户滚动页面时，当满足指定的偏移位置元素会变为固定定位，直到其滚动容器达到定义的阈值。
        color: rgba(0, 0, 0, 0.7);
        text-align: center;//文字居中，其实这个可以不要
        display: flex; /* 使用 Flexbox布局 */
        justify-content: center; /* 水平居中 */
        align-items: center;/* 垂直居中 */
      }
      .back{
        height: 200px;
        background-color: rgba(154, 226, 233, 0.7);
      }
      .box1 {
        height: 100px;
        width: 100vw;
        background: #f9d9d9;
        position: sticky;//粘性定位
        top: 0;//元素在static和fixed之间切换
        display: flex;//flex布局
        justify-content: center;//水平居中
        align-items: center;//垂直居中
        color: rgba(0, 0, 0, 0.8);
      }
      .box2{
        height: 10000px;
      }
    </style>
  </head>
  <body>
    <div class="back">
      <div class="wrapper">
        <header>大疆商城App 立即下载 ×</header>
      </div>
    </div>
    <div class="box1">
      <header>DJI    光影夏日  好礼相至   (搜索icon)（个人信息icon）</header>
    </div>
    <div class="box2">
         <header>这里是商品信息   商品信息</header>
    </div>
  </body>
```
**顺便复习一下css五种定位方式吧**
1. **`static`**：
    
    - **默认值**。元素按照正常的文档流进行定位，不会受到 `top`、`right`、`bottom` 或 `left` 属性的影响。
    - 元素会在页面中按照顺序依次排列。
2. **`relative`**：
    
    - 元素相对于其正常位置进行定位。
    - 可以使用 `top`、`right`、`bottom` 和 `left` 属性来移动元素，但它仍然占据原始空间。原始空间保留，其他元素不会占据它的位置。
    - 示例：`position: relative; top: 10px;` 会使元素从其正常位置向下移动 10 像素。
3. **`absolute`**：
    
    - 元素相对于最近的已定位的祖先元素进行定位（如果祖先元素没有定位，则相对于初始包含块，即浏览器窗口）。
    - 使用 `top`、`right`、`bottom` 和 `left` 属性进行精确定位。
    - 元素脱离文档流，其他元素会占据它原来的位置。
    - 示例：`position: absolute; top: 50px; left: 100px;` 会使元素相对于最近的已定位祖先元素的左上角移动。
4. **`fixed`**：
    
    - 元素相对于浏览器窗口进行定位，不会随着页面滚动而移动。
    - 使用 `top`、`right`、`bottom` 和 `left` 属性进行精确定位。
    - 元素脱离文档流，其他元素会占据它原来的位置。
    - 示例：`position: fixed; top: 0; right: 0;` 会将元素固定在浏览器窗口的右上角。
5. **`sticky`**：
    
    - 元素在正常文档流中（`static`）和固定定位（`fixed`）之间切换，具体取决于滚动位置。
    - 它是相对于最近的滚动祖先元素进行定位。
    - 当用户滚动页面时，如果满足指定的偏移位置（通过 `top`、`right`、`bottom`、`left` 属性设置），元素会变为固定定位，直到其滚动容器达到定义的阈值。
    - 示例：`position: sticky; top: 20px;` 会使元素在其父容器的顶部距离 20 像素时变为固定定位。

**总结：**

- `static`: 默认定位，不脱离文档流。
- `relative`: 相对定位，移动元素但保留原始空间。
- `absolute`: 绝对定位，相对于最近的已定位祖先元素，脱离文档流。
- `fixed`: 固定定位，相对于浏览器窗口，脱离文档流。
- `sticky`: 粘性定位，在 `static` 和 `fixed` 之间切换。

**再复习一下Flex布局**
### Flexbox 的基本概念

#### 1. Flex 容器和 Flex 项目

- **Flex 容器**（Flex Container）：使用 `display: flex` 或 `display: inline-flex` 创建的容器。
- **Flex 项目**（Flex Items）：Flex 容器内的直接子元素。

#### 2. 主轴和交叉轴

- **主轴**（Main Axis）：Flex 容器的主轴默认是水平的，可以通过 `flex-direction` 改变方向。
- **交叉轴**（Cross Axis）：垂直于主轴的轴。

### Flex 容器的属性

1. **display**
    
    - `flex`：定义一个块级 Flex 容器。
    - `inline-flex`：定义一个内联级 Flex 容器。
2. **flex-direction**
    
    - 决定主轴的方向。
    - 取值：`row`（默认值，水平，从左到右）、`row-reverse`（水平，从右到左）、`column`（垂直，从上到下）、`column-reverse`（垂直，从下到上）。
3. **flex-wrap**
    
    - 决定 Flex 项目是否换行。
    - 取值：`nowrap`（默认值，不换行）、`wrap`（换行）、`wrap-reverse`（换行，反方向）。
4. **justify-content**
    
    - 决定项目在主轴上的对齐方式。
    - 取值：`flex-start`（默认值，起始对齐）、`flex-end`（结束对齐）、`center`（居中对齐）、`space-between`（两端对齐，项目之间的间隔相等）、`space-around`（项目两侧的间隔相等）、`space-evenly`（项目之间和项目与边框的间隔相等）。
5. **align-items**
    
    - 决定项目在交叉轴上的对齐方式。
    - 取值：`flex-start`（起始对齐）、`flex-end`（结束对齐）、`center`（居中对齐）、`baseline`（基线对齐）、`stretch`（默认值，拉伸对齐）。
6. **align-content**
    
    - 决定多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。
    - 取值：`flex-start`、`flex-end`、`center`、`space-between`、`space-around`、`stretch`（默认值）。

### Flex 项目的属性

1. **order**
    
    - 决定项目的排列顺序，默认值为 0，可以是负值。
2. **flex-grow**
    
    - 决定项目的放大比例，默认值为 0，表示如果有多余空间也不放大。
3. **flex-shrink**
    
    - 决定项目的缩小比例，默认值为 1，表示如果空间不足，该项目将缩小。
4. **flex-basis**
    
    - 决定项目的初始大小，默认值为 `auto`。
5. **align-self**
    
    - 允许单个项目有与其他项目不一样的对齐方式，可覆盖 `align-items` 属性。
    - 取值：`auto`（默认值，继承 `align-items` 的值）、`flex-start`、`flex-end`、`center`、`baseline`、`stretch`。