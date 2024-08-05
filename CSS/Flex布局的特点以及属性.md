>弹性盒模型，响应式适应不同屏幕尺寸的页面布局，是的垂直居中和等距分布变简单。轻松实现水平和垂直方向控制和顺序控制。

![[Pasted image 20240805091819.png]]
**由父容器和子容器构成，通过主轴和交叉轴控制子容器排列**

父容器：
- display：flex 弹性布局| inline-flex行内弹性布局

- flex-direction：row（默认主轴为水平，起点在左端）|row-reverse（主轴为水平，起点在右端）|column（主轴为垂直，起点在上）|column-reverse（主轴垂直起点在下）

- flex-wrap：wrap（换行）|nowrap（默认不换行）|wrap-reverse（换行，第一行在下方）

- flex-flow：row wrap （flex-direction和flex-wrap的简写）

- justify-content（主轴对齐）：flex-start（默认从起点开始）|flex-end（终点开始）|center（居中）|space-between（两端对齐，项目间隔相等）|space-around（项目间隔相等，每个项目两侧间隔为项目间隔的一半）|space-evenly（项目间隔相等，包括起点和终点）

- align-items：（交叉轴对齐方向）center（居中）|flex-start（对齐到交叉轴起点）|stretch（默认）拉伸以适应容器|baseline（项目第一行文字基线对齐）

- align-content：（多轴对齐）center（居中对齐）|space-between|space-around|stretch（默认拉伸适应容器）|flex-start|flex-end

子容器：
- order：项目排列顺序，越小排列越靠前，默认0

- flex-grow：项目放大比例,默认0

- flex-shrink：项目缩小比例，默认1（容器宽度<元素总宽度时如何收缩），如果所有项⽬的flex-shrink属性都为1，当空间不⾜时，都将等⽐例缩⼩。 如果⼀个项⽬的flex-shrink属性为0，其他项⽬都为1，则空间不⾜时，前者不缩⼩。

- flex-basis：分配多余空间前占据主轴空间，默认auto。

- flex（等分剩余空间）：相当于flex-grow：1 flex-shrink：1和flex-basis：0%（优先使⽤这个属性，⽽不是单独写三个分离的属性，因为浏览器会推算相关值。）
  flex: 1 = flex: 1 1 0% 
  flex: 2 = flex: 2 1 0% 
  flex: auto = flex: 1 1 auto 
  flex: none = flex: 0 0 auto，常⽤于固定尺⼨不伸缩

- aline-self：默认auto集成父元素的align-items属性（单个的item，可以覆盖父元素）

**常用案例**
- 垂直居中：
  flex-direction：row/column
  align-items:center
- 水平居中
  flex-direction：row/column
  justify-content：center
  
