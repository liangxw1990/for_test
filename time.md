
参考书籍:《编写高质量代码：改善Python程序的91个建议》，建议32。

`report`函数需要传入当前时间并作一些处理。


1. 错误的传参方式：

    ```python
    import time
    def report(when=time.time()):
        print(when)
        
    report()
    time.sleep(3)
    report()
    ```
    输出：  
    1550637953.259046  
    1550637953.259046

    > `time.time()`的类型为`float`。  
    首次调用时，默认参数会进行计算，再次调用时不会再进行计算。

2. 正确的传参方式：

    ```python
    import time
    def report(when=time.time):
        print(when())
        
    report()
    time.sleep(3)
    report()
    ```

    输出：  
    1550637949.7783394  
    1550637952.7793248

    > 默认参数为`time.time`函数对象，函数内部每次都会执行`when()`计算当前时间。
