# python学习资源

---

  廖雪峰官网：https://www.liaoxuefeng.com/  
  
  腾讯课堂：https://ke.qq.com/course/162814
  
  中文文档：http://python.usyiyi.cn/translate/python_352/library/index.html

## 环境准备
Miniconda ： https://conda.io/miniconda.html  <br/>

Anaconda 镜像:https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/
```base
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
```
## 03：[Python函数](./docs/function.md)

## 04：[Python面向对象](./docs/class.md)

## [Qt Designer](./qt/designer.md)

## [Qt note](./qt/Qt.md)

## python3写好的.py文件如何打包成exe

可用一句命令打包：pyinstaller -F -w -i manage.ico app.py

-F：打包为单文件

-w：Windows程序，不显示命令行窗口

-i：是程序图标，app.py是你要打包的py文件

另外需要pywin32。

安装方法：先跑pip install pywin32再跑pip install pyinstaller即可。

打包完成后若出现：This application failed to start because it could not find or load the Qt platform plugin "windows" 

解决方法：拷贝pyqt安装目录中搜索platform文件夹，整个复制到打包的exe目录



拷贝pyqt安装目录中搜索platform文件夹，整个复制到打包的exe目录

## PyQt教程
https://zhuanlan.zhihu.com/xdbcb8

## PyQt5小项目

https://github.com/892768447/PyQt

https://github.com/HuberTRoy/MusicBox

## Qt 实战

https://blog.csdn.net/liang19890820/article/details/50277095

## pyqt下QTableWidget使用方法小结
https://blog.csdn.net/vah101/article/details/6215066

```py
#根据内容改变列宽，用户与程序不能改变列宽
self.table.horizontalHeader().setSectionResizeMode(QtWidgets.QHeaderView.ResizeToContents)

#根据空间，自动改变列宽，用户与程序不能改变列宽
self.table.horizontalHeader().setSectionResizeMode(QtWidgets.QHeaderView.Stretch)
```

```py
# 合并单元格 第1行6列，下合并3右和并2格
self.table.setSpan(0,5,3,2)

#设置指定单元格不可编辑  第1行第3列
item0 = QtWidgets.QTableWidgetItem()
item0.setFlags( QtCore.Qt.ItemIsEnabled)
self.table.setItem(0, 3, item0)
```
## python工具
```py
python -m pyqtgraph.examples
```
## [python 中遇到的bug](./bug.md)
