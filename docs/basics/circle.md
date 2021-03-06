# 圆 Circle

![circle](../images/basics/circle.jpg)

圆是非常优美的图形，没有棱角。从远处看，太阳、月亮都是一个圆。

从一个特定的点出发，距离相同的点的集合便构成了一个圆。如果在3维空间中，这个相同的定义便成为了球的定义，球的任意一个横切面又都是一个圆，非常迷人的特性。

## 圆的定义 Definition

在pyleap中，圆是一个基本图形，圆的基本属性有

| 属性名 | 属性说明    | 属性类型 |
| ------ | ----------- | -------- |
| x      | 圆心的x坐标 | 数字     |
| y      | 圆心的y坐标 | 数字     |
| r      | 圆的半径    | 数字     |
| color  | 圆的颜色    | 数字     |

## 圆类的的定义 Class Circle

```python
class Circle(Shape):
    """ 基本图形：圆 Circle """

    def __init__(self, x=100, y=100, r=30, color="orange"):
        """
        圆心： x、y,    默认为100, 100
        半径： r，     默认为30
        颜色： color,  默认为 "orange"
        """
```

注意的是，Circle第一个字母是大写，在`python`中，我们往往将类的第一个字母大写，用来区分变量和函数。

基于上面的定义，和Python语言的特性，我们可以选取特定的属性，来定义我们的圆，下面的定义都是合法的

```python
from pyleap import *        # 导入pyleap

c1 = Circle(x=100, y=100, r=30, color="red")    # 完整参数
c2 = Circle(200, 100, 40, "yellow")             # 简单参数
c3 = Circle(300, 100, color="blue")             # 部分参数

@repeat # 重复执行下面的函数
def draw(dt):
    window.clear() # 窗口清空
    c1.draw()
    c2.draw()
    c3.draw()


run()  # 运行起来
```

从左到右依次是c1、c2、c3

![circle](../images/basics/c1.png)

## 空心圆和实心圆

下面2个圆，他们的半径和颜色一样，但是它们展示出来的效果不同。

![circle](../images/basics/c2.png)

他们分别是使用不同的方法来绘制出来的：`draw()`和`stroke()`

 ```python
 from pyleap import *

c1 = Circle(100, 100, 50)
c2 = Circle(220, 100, 50)

@repeat
def draw(dt):
    window.clear()
    c1.draw()   # 第一个圆
    c2.stroke() # 第二个圆

run()  
 ```

## 线条粗细

再看这两个圆，同样是使用`stroke()`方法绘制出来，两个圆的线条粗细不同

![circle](../images/basics/c3.png)

这是通过设置线条粗细`line_width`来设定线条的宽度，当然，这个属性只对`stroke`方法有作用。

```python
from pyleap import *

c1 = Circle(100, 100, 50)
c2 = Circle(220, 100, 50)
c2.line_width = 5 # 设置线条粗细

@repeat # 重复执行下面的函数
def draw(dt):
    window.clear()
    c1.stroke()
    c2.stroke()

run()
```

## 更多实例 Examples

绘制一个圆，圆心位置为（100，100），半径为50，颜色为红色("red")

```python
from pyleap import *

c1 = Circle(x=100, y=100, r=50, color="red")

@repeat     # 等同于 repeat(draw)
def draw(dt):
    window.clear()
    c1.draw()

run()
```

绘制一个空心的圆，线条的粗细为5（像素），圆心位置为（200，200），半径为60，颜色为绿色("green")

```python
from pyleap import *

c2 = Circle()
c2.x = 200
c2.y = 200
c2.r = 60
c2.color = "green"
c2.line_width = 5

@repeat
def draw(dt):
    window.clear()
    c2.stroke()

run()
```