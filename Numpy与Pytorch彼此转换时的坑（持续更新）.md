# Numpy与Pytorch学习时的坑（持续更新）

## 前言

​		最近使用 Numpy包与Pytorch写神经网络时，经常需要两者彼此转换，故用此笔记记录码代码时踩（菜）过的坑，网上有人说：

> ```
> Pytorch 又被称为 GPU 版的 Numpy，二者的许多功能都有良好的一一对应。
> ```

​	但在使用时还是得多多注意，一个不留神就陷入到了 *<u>一根烟一杯酒，一个Bug找一宿</u>* 的地步。

## 1、torch与numpy转换：

### 1.1、numpy ——> torch

​		使用  `torch.from_numpy()` 转换，需要注意，**两者共享内存**。例子如下：

```python
import torch
import numpy as np

a = np.array([1,2,3])
b = torch.from_numpy(a)
np.add(a, 1, out=a)
print('转换后a', a)
print('转换后b', b)

# 显示

转换后a [2 3 4]
转换后b tensor([2, 3, 4], dtype=torch.int32)

```

### 1.2、torch——> numpy

​		使用 `.numpy()` 转换，同样，**两者共享内存**。例子如下：

```python
import torch
import numpy as np

a = torch.zeros((2, 3), dtype=torch.float)
c = a.numpy()
np.add(c, 1, out=c)
print('a:', a)
print('c：', c)

# 结果

a: tensor([[1., 1., 1.],
           [1., 1., 1.]])
c： [[1. 1. 1.]
 	[1. 1. 1.]]
```

​		需要注意的是，如果将程序中的 `np.add(c, 1, out=c)` 改成 `c = c + 1` 会发现两者貌似不共享内存了，其实不然，原因是后者相当于改变了 c 的存储地址。可以使用 `id(c)` 发现c的内存位置变了。

## 2、numpy.repeat() 与torch.repeat() 的区别

