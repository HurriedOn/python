# Anaconda3工具包中Python常用配置及报错解决办法

### 安装pip包报错

##### 报错信息：
```py
Traceback (most recent call last):
  File "d:\ProgramData\Anaconda3\lib\site-packages\pip\compat\__init__.py", line 73, in console_to_str
    return s.decode(sys.__stdout__.encoding)
UnicodeDecodeError: 'utf-8' codec can't decode byte 0xa1 in position 95: invalid start byte
```

##### 解决办法：

修改73行代码： 

注意报错的是 line 73

```py
if sys.version_info >= (3,):
    def console_to_str(s):
        try:
            return s.decode(sys.__stdout__.encoding)
        except UnicodeDecodeError:
            return s.decode('utf_8')
```

修改为：
```py
if sys.version_info >= (3,):
    def console_to_str(s):
        try:
            return s.decode('cp936')
        except UnicodeDecodeError:
            return s.decode('utf_8')
```

### pyinstaller 打包时报错

环境：

* Win10
* Python3.6.4(Anaconda最新版)
* PyInstaller: 3.3.1

运行 pyinstaller -F -w -i manage.ico main.py 错误信息：

```py
'utf-8' codec can't decode byte 0xce in position 122: invalid continuation....
```

#### 解决方法：CMD中输入
```py
CHCP 65001
```
