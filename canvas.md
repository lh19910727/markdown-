# canvas

标签（空格分隔）： 未分类

---

 -

 - toDataURL()方法可以导出在cnavas元素上绘制的图像 eg：var imgurl=drawing.toDataURL('img/png')
  默认图像的编码为png格式；
 - 填st充fillStyle 描边strokeStyle是canvas两种基本绘图操作。这两个属性的值可以是字符串、渐变对象、模式对象，而且他们的默认值都是‘#000000’如果为他们指定表示颜色的字符串，可以使用css中指定颜色值得任何格式
 - 矩形绘制：有关方法：fillRect()、strokeRect()、clearRect()这三种方法都接受4个参数x轴坐标、y轴坐标、宽度、高度单位都是像素R；
 - strokeRect()方法在画布上绘制的矩形会通过指定的颜色描边，描边颜色通过strokeStyle属性设置；fillRect（）方法为矩形填充指定的颜色，颜色通过fillStyle属性指定；
 - lineWidth属性设置描边线条的宽度，
 - lineCap属性可以控制线条末端的形状是平头（butt）、圆头（round）、方头（square）
 - lineJoin属性可以控制线条相交的方式是圆交（round）、斜交（bevel）、斜接（miter）
 - 绘制路径：beginPath()方法表示开始绘制新路径     
 - arc（X,Y,radius，startAngel，endAngel，counterclockwise）
 - arcTo（x1,y1,x2,y2,radius)
 - bezierCurveTo(c1x,c1y,c2x,c2y,x,y)
 - lineTo(x,y)
 - moveTo(x,y)
 - quadraticCurveTo(cx,cy,x,y);
 - rect(x,y,width,height);
closePath()绘制一条连接到起点的线条fill（）表示
绘制完成后用fillStyle去填充；stroke（）表示绘制完成后使用strokeStyle去描边；clip（）在路径上创建一个剪切区域；
 - 绘制文本：fillText（）strokeText（）这两个方法都接受4个参数：要绘制的文本字符串，x轴坐标，y轴坐标，可选的最大像素宽度；这两个方法都接受以下3个属性为基础：
     - font：表示文本样式大小及字体，用css中指定的字体格式来指定；
     - textAlign：表示文本对齐方式
     - textBaseline：表示文本的基线；
 - 变换：
     - rotate（angle）围绕原点旋转图像angle弧度；
     - scale（scalex，scaley)缩放图像，x轴方向乘以scalex，y轴方向乘以scaley，默认值都是1；
     - translate（x,y):将坐标原点移动到（x，y）执行这个变换后坐标（0，0)会变成之前由（x，y）表示的点；
     - transform（m1-1,m1-2,m2-1,m2-2,dx,dy)直接修改变换矩阵
     - setTransform（m1-1,m1-2,m2-1,m2-2,dx,dy)将变换矩阵重置为默认默认状态；然后调用transform（）
     - 
 - save（）方法：调用这个方法使之前所有的设置都会进入一个栈结构，得以妥善保管；然后可以对上下文进行其他修改，等想要回到之前保存的设置时可以调用restore（）方法，在保存设置的栈结构中向前返回一级，恢复之前的状态，，连续使用save（）方法可以把更多设置保存到栈结构中，之后在连续调用restore（）则可以一级一级返回；（需要注意的是save（）方法保存的只是绘图上下文的设置和变换，不会保存内容；
 - drawImage()绘制图像可接受三个参数：传入一个HTML<img>元素，以及绘制该图像起点的x，y坐标；
 - toDateURL()方法获取图像；
 - 阴影：
    - shadowColor：用css颜色格式表示阴影颜色默认为黑色；
    - shadowOffsetX：形状或路径x轴方向的阴影偏移量，默认为0；
    - shadowOffsetY：形状或路径y轴方向的偏移量，默认为0；
    - shadowBlur：模糊的像素数，默认为0，即为不模糊；
    - 这些属性都可以通过context对象来进行修改。只要在绘制前设置适当的值就能自动产生阴影；
 - 渐变：canvasGradient实例表示渐变；要创建一个新的线性渐变可以调用creatLinearGradient（）方法，这个方法接受4个参数：起点x轴坐标，起点y轴坐标，终点x轴坐标，终点y轴坐标；调用这个方法后他就会创建一个指定大小的渐变并返回cnavasGradient对象的实例；
 - 创建渐变对象后下一步就是使用addColorStop（）方法来指定色标。这个方法接受两个参数：色标位置和css颜色值。色标位置是一个0~1之间的数字；
 - createRadialGradient()方法创建径e向渐变，接受6个参数前三个是起点圆的圆心x轴y轴坐标及半径，后三个参数为终点圆的圆心坐标x，y及半径;
 - 模式：其实就是重复的图像，可以用来填充或者描边图形。创建一个新模式可以调用creatPattern（）方法并传入两个参数：一个HTML<img>元素和一个表示如何重复图像的字符串与css中background属性值相同包括‘repeat’、‘repeat-x’、‘repeat-y’、‘no-repeat’；
 - 使用图像数据：getImageData（）取得原始图像数据，这个方法接受4个参数：要取得数据画面的x轴，y轴坐标，及该区域像素宽度和高度；
    - 返回值是一个对象每个对象都有三个属性：width、height、和data;其中data是数组，每一个像素用4个值来保存，分别表示红、绿、蓝和透明度值



 
 


 

 