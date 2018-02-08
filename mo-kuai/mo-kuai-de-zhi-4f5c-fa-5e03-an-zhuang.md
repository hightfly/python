# 模块制作 {#模块制作}

### &lt;1&gt;定义自己的模块

在Python中，每个Python文件都可以作为一个模块，模块的名字就是文件的名字。

比如有这样一个文件Test.py，在Test.py中定义了函数add

```
    def add(a,b):
        return a+b
```

### &lt;2&gt;调用自己定义的模块

那么在其他文件中就可以先import test，然后通过test.add\(a,b\)来调用了，当然也可以通过from test import add来引入

```
    import Test
    result = Test.add(11,22)
    print(result)
```

## &lt;3&gt;测试模块 {#测试模块}

Test.py: 模块

```
def add(a, b): # 模块中的函数
    return a+b


def main(): # 测试模块中函数是否正确
    ret = add(10, 20)
    print('a+b = %d'%ret)

if __name__ == '__main__': # 测试入口函数。只有开发者进行测试时执行，发布之后，不会执行
    main()
```

## &lt;3&gt;导出指定模块中的元素 {#测试模块}

可以通过`__all__`变量，导出指定模块中的元素

如：

```
#如果一个模块中有__all__变量，那么也就意味着这个变量中的元素，不会被from xxx import * 时导入
__all__=['add', 'Person', 'test1']

def add(a, b):
    return a+b

class Person(object):
    def test(self):
        pass
def test1():
    pass

def test2():
    pass

def main():
    ret = add(10, 20)
    print('a+b = %d'%ret)

if __name__ == '__main__':
    main()
```

注意事项：

如果使用from xxx import \* 导入模块中的所有元素时，此时\_\_all\_\_ 变量就会生效。

如果 import Test 直接导入模块，此时\_\_all\_\_ 变量就不再生效



## &lt;3&gt;发布模块 {#测试模块}


