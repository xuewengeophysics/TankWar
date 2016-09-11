## 基本原理

* 游戏开始创建敌人的实例和一个玩家实例，使用重绘与多线程让坦克和子弹再在界面中移动，敌方坦克随机移动和发射子弹。 玩家坦克由方向键控制方向，ctrl键发射子弹，使用简单的碰撞检测方法来实现子弹，坦克和墙壁之间的撞击。

## 游戏截图
![](http://i.imgur.com/t9EjUTU.jpg?1)

## 游戏功能

### 游戏控制：

* 可以开始、暂停、继续、退出游戏

### 游戏设置：

* 可以设置游戏的一些参数：包括我的坦克的生命条数，敌人坦克的总数量，同一时间敌人的坦克的最多数量

### 游戏特点：

* 坦克（包括我的坦克和敌人坦克）可以上、下、左、右、左上、左下、右上、右下八个方向移动，坦克不会出界（游戏窗口）。

* 坦克可以随机发射，敌人坦克间断的发射，间断时间在1-2秒之间随机，我的坦克发射由人为按键控制发射。

* 敌人坦克可以随机移动，发射，改变方向，敌人坦克之间不会相撞，当敌人坦克预测到以现在的方向继续移动会撞击到自己的队友时（我的坦克除外，它可以撞击我的坦克），它会立即改变方向。

* 窗口左上角会显示当前的游戏信息，包括我的坦克剩余命数，敌人坦克剩余命数，杀死敌人数量

##  游戏实现

### 确定对象
* 确定这个游戏有哪些对象，应该抽象出来那些类型。 坦克类（这可以作为基类型，分别派生出敌人坦克和我的坦克）、子弹类、爆炸类、还有一个控制游戏的类，游戏引擎类。

### 绘画
* 本游戏呈现的是动态的画面，所谓的动态画面就是一副副的图片连续播放，而且之间间隔时间必须足够短，才能使人的视觉感觉是连贯的。所以这里要用到重绘，坦克要重绘，子弹也要重绘，所有要出现在游戏画面的对象就必须不停的进行重绘。

* java里面的component是一个具有图形表示能力的对象，它是所有可视化对象的基类，它有一个方法repaint()，这个方法就是重绘组件的。

* 重写游戏引擎类的update（）方法，在update（）方法里，把所有需要绘画的对象绘画一遍，调用的时候还是要调用repaint()方法。

* 使用多线程来执行绘画。