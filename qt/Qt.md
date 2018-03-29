## Qt学习: 状态栏

---

Qt提供了一个QStatusBar类来实现状态栏。

Qt具有一个相当成熟的GUI框架的实现——这一点感觉比Swing要强一些——Qt似乎对GUI的开发做了很多设计，比如QMainWindow类里面就有一个statusBar()函数，用于实现状态栏的调用。类似menuBar()函数，如果不存在状态栏，该函数会自动创建一个，如果已经创建则会返回这个状态栏的指针。如果你要替换掉已经存在的状态栏，需要使用QMainWindow的setStatusBar()函数。

在Qt里面，状态栏显示的信息有三种类型：临时信息、一般信息和永久信息。其中，临时信息指临时显示的信息，比如QAction的提示等，也可以设置自己的临时信息，比如程序启动之后显示Ready，一段时间后自动消失——这个功能可以使用QStatusBar的showMessage()函数来实现；一般信息可以用来显示页码之类的；永久信息是不会消失的信息，比如可以在状态栏提示用户Caps Lock键被按下之类。

QStatusBar继承自QWidget，因此它可以添加其他的QWidget。
