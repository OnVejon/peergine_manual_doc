## 7\. 使用视频传输类(PG_CLASS_Video) {#7-pg-class-video}

### 1) 预览模式 {#1}

视频传输类有三种模式：预览模式、两点模式和会议模式。预览模式用PG_ADD_VIDEO_Preview选项开启，用来显示从本地视频捕捉设备上输入的视频图像。

### 2) 两点模式 {#2}

缺省为两点模式。两点模式允许经过呼叫协商之后才建立通话。一端发起请求之后，另一端可以选择接受或拒绝，只有对端选择接受后通话才建立。发起端调用PG_METH_VIDEO_Open方法发起呼叫请求，对端接收到呼叫请求后，通过返回应答的错误码来确认接受或拒绝，错误码等于0表示接受，错误码大于0表示拒绝及其原因。

两点模式时，如果视频传输对象关联的通信组对象有多个成员，则系统选择第1个成员作为对端节点。所以，为了使通信范围更加准确，建议视频传输对象关联节点对象作为对端节点，或者关联的通信组对象始终保持只有1个成员作为对端节点。

### 3) 会议模式及视频的加入和离开 {#3}

会议模式用PG_ADD_VIDEO_Conference选项开启。调用PG_METH_VIDEO_Open打开视频会议后，缺省没有视频通话加进来，需要PG_METH_VIDEO_Join和PG_METH_VIDEO_Leave使视频加入或离开。视频加入需要经过呼叫协商，对端选择接受之后，视频才能加入到会议中。

### 4) 视频窗口调整和转移 {#4}

调用PG_METH_VIDEO_Move方法可以调整视频在窗口中显示的位置和尺寸，或者从当前的窗口转移到另一个窗口中。调用此方法时，如果只是改变了参数中的坐标参数，则调整视频在窗口中的显示位置和尺寸。如果改变了窗口的句柄，则把视频转移到另一个窗口中显示。

### 5) 拍照片 {#5}

调用PG_METH_VIDEO_Camera方法对输出的视频拍照片。Path参数指定保存照片的文件路径，照片文件必须是“.jpg”文件。

### 6) 视频录制 {#6}

调用PG_METH_VIDEO_Record方法可将视频输出录制到由Path参数指定的AVI文件中。如果调用时指定Path参数为空，则停止当前正在进行的录制操作。

如果想将视频和音频录制到同一个AVI文件中，则在开始录制视频和音频时，都给Path参数指定同一个AVI文件。请参考“[音频录制](#5)”章节。