## 8\. 使用白板共享类(PG_CLASS_Board) {#8-pg-class-board}

### 1) 设置绘制图形的参数 {#1}

调用PG_METH_BOARD_Shape方法可设置绘图的参数，包括图案类型、线条宽度、线条颜色和线条样式。在一个节点上绘图时，通信组内的其他节点上会实时显示。

### 2) 设置绘制不同图形时的鼠标光标 {#2}

调用PG_METH_BOARD_Cursor方法可设置图案类型下的鼠标光标，让用户可以直观地知道当前的绘图状态。

### 3) 实现橡皮功能 {#3}

白板共享类没有专门的橡皮功能，但可以用绘制线条的方法来实现橡皮。设置线条的颜色与背景颜色相同、设置较宽的线条宽度、设置橡皮形状的鼠标光标，绘制这样的线条时就等同于橡皮的效果。

### 4) 保存和载入文件 {#4}

调用 PG_METH_BOARD_Save方法把当前白板的内容保存到指定的图片文件。调用PG_METH_BOARD_Load方法把指定图片文件的内容装入到白板中。这里的图片文件必须是“.png”文件。