### 列表旋转

给定一个列表，求旋转K位的新列表。比如1,2,3,4,5,向右旋转2,则新列表为4,5,1,2,3

## 方法

1. 拷贝法。根据K可以计算出i位置旋转后的位置，即i -> (i + k) % n, n 为列表长度
new一个相同长度的空列表，然后逐一拷贝即可。

2. 三步翻转法。即reverse(l, 0, k - 1), reverse(l, k, n - 1), reverse(l)即可。
具体讲解[三步翻转法](https://github.com/mefoo/The-Art-Of-Programming-By-July/blob/master/ebook/zh/01.01.md)

3. 循环交换法。

不难看出，字符串长度为n，若向右移动k， 则每个元素的位置可以根据计算算出，即i -> (i + k) % n。完美洗牌中引入了 圈的概念，将这个圈引入到字符串旋转中。比如0,1,2,3,4,5, 右旋转2，则变成4,5,0,1,2,3,即

0->2->4->0 (步数为k)

1->3->5->1

共两圈。

而0,1,2,3,4,5,6 右移3，变成4,5,6,0,1,2,3,即

0->3->6->2->5->1->4->0

只有一圈。

### 元素移动

给定一个列表，如1,2,3,4,5,和它的一个子列表，如2,3,求子列表移动k位形成的新列表。
比如右移两位，则变成1,4,5,2,3。

## 方法
    以右移为例:
	1. 求子列表长度len == 2
	2. 将子列表向右扩展k == 2位，变成2,3,4,5
	3. 将子列表左移len == 2位，变成4,5,2,3
	4. 和剩下的子列表合并，变成1,4,5,2,3

再比如1,2,3,4,5, 将4左移两位:
	1. 求子列表长度len == 1
	1. 将子列表向左扩展k == 2 位，变成2,3,4
	2. 将子列表右移len == 1位， 变成4,2,3
	3. 和剩下的子列表合并， 变成1,4,2,3,5

### demo