
# 未解决的题目
239 滑动窗口最大值

# 问题
- C++中stack，queue 是容器么？

栈是容器适配器，底层可以使用不同的容器。默认的底层容器是deque。

- 我们使用的stack，queue是属于那个版本的STL？
- 我们使用的STL中stack，queue是如何实现的？
- stack，queue 提供迭代器来遍历空间么？


# leetcode 报错
## AddressSanitizer:DEADLYSIGNAL
- (高频)越界，数组引用超越了左右边界
- 无限递归，代码无法正常结束返回
- (高频)函数入参及出参返回处理错误

# 数据结构
## 二叉树
### 分类
- **满二叉树**：全部填满了。
- **完全二叉树**：除了最底层没填满，而且最底层的节点都在左边。
- **二叉搜索树**：左子树的值小于根节点，右子树的值大于根节点。
- **平衡二叉搜索树（AVL）**：空树或者左右两个子树的高度差不超过1，而且左右子树都是平衡二叉树。
### 存储方式
链式存储：用指针
顺序存储：用数组

### 遍历方式
- 深度优先：前中后序，一般用递归，栈
- 广度优先：层次遍历，一般用队列

### 注意事项
- C++中map、set、multimap，multiset的底层实现都是平衡二叉搜索树，所以map、set的增删操作时间时间复杂度是logn
- unordered_set unordered_map底层是哈希表。

## 堆
- 堆是一棵完全二叉树，树中每个结点的值都不小于（或不大于）其左右孩子的值。 如果父亲结点是大于等于左右孩子就是大顶堆，小于等于左右孩子就是小顶堆。


## 栈和队列
- 栈和队列是STL（C++标准库）里面的两个数据结构。
- 栈是以底层容器完成其所有的工作，对外提供统一的接口，底层容器是可插拔的（也就是说我们可以控制使用哪种容器来实现栈的功能）。
- STL中栈往往不被归类为容器，而被归类为container adapter（容器适配器）。


在SGI STL里，栈和队列的底层是deque。

### 栈和队列的函数
stack
- push、pop、empty

queue
- back、front、pop、size、empty

### 优先级队列
- 实际上是一个堆。
- 缺省情况下priority_queue利用max-heap（大顶堆）完成对元素的排序，这个大顶堆是以vector为表现形式的complete binary tree（完全二叉树）。

## 哈希结构
- 基于哈希表：unordered_set、unordered_map
- 基于红黑树：set、mutliset、map、multimap
- 当我们要使用集合来解决哈希问题的时候，优先使用unordered_set，因为它的查询和增删效率是最优的，如果需要集合是有序的，那么就用set，如果要求不仅有序还要有重复数据的话，那么就用multiset。


## 数据类型
- 最大的数字
```cpp
int result = INT32_MAX;
```

## 链表
- 通常要定义虚拟头指针 dummyNode，指向头节点，方便处理头节点。
- 在链表位置i前，删除或者添加元素，需要定位到i-1的位置。
- 如果题目给的是index从0开始，那头指针就设置为dummy_node，然后做index--循环，头指针就能定位到第i个位置前一个元素。
- 如果是输出第i个位置的元素，那么头指针设置为dummy_node->next。

## 哈希表
```
unordered_map<int, int> cnt;

auto it = cnt.find(fruits[left]);
                --it->second;
                if (it->second == 0) {
                    cnt.erase(it);
                }
                ++left;

```
- find函数、erase函数、size 函数
- 哈希表可以直接对还没存在的键赋值。
- 哈希表遍历

```cpp
unordered_map<int,int> pp;
pp[1]++;
pp[2] = 3;

for(const auto& p:pp){ //const
    cout<<p.first<<endl;
}

```

## vector
- vector的底层实现是array，严格来讲vector是容器，不是数组。
- 有Push_back pop_back, 没有push_front
- 需要insert(pos, number);  这里的pos是指针！比如nums.begin()
- 数组初始化：vector<int> res (n,0);
- 遍历可以用下标
- 判断是否为空vector.empty()


## 数组
- 定义
```cpp
int record[26] = {0};
```

## 字符串
- 添加元素 push_back
- 删除元素 pop_back
- 获取尾部元素 back
- 获取长度 size
- 获取子字符串 ：从位置0开始，取出两个元素。
- 把str转成longlong stoll()
- 逆转顺序 reverse
```cpp
reverse (result.begin(), result.end());
```

```cpp
string a  = 'abc';
cout<<a.substr(0,2);
```

- resize 重新设置字符串长度
```cpp
stiring a ='123';
a.resize(2);
//输出为12
```


## 二维数组

- 取出行和列的数值
```cpp
a[0][1] = 1; //表示第0行第一个元素
int rows = array.size(), columns = array[0].size();
```


# 算法
## 递归
- 确定递归函数的参数和返回值： 确定哪些参数是递归的过程中需要处理的，那么就在递归函数里加上这个参数， 并且还要明确每次递归的返回值是什么进而确定递归函数的返回类型。
- 确定终止条件： 写完了递归算法, 运行的时候，经常会遇到栈溢出的错误，就是没写终止条件或者终止条件写的不对，操作系统也是用一个栈的结构来保存每一层递归的信息，如果递归没有终止，操作系统的内存栈必然就会溢出。
- 确定单层递归的逻辑： 确定每一层递归需要处理的信息。在这里也就会重复调用自己来实现递归的过程。

## 滑动窗口
- 需要思考返回的值在代码的哪一段进行计算，是在while内，还是在while的前面或者后面。什么时候符合条件，什么时候对返回的值进行计算。
- 最大滑窗是在迭代右移右边界的过程中更新结果（904 水果成篮），而最小滑窗是在迭代右移左边界的过程中更新结果（209 长度最小的子数组）。
https://www.cnblogs.com/huansky/p/13488234.html
- 数组或者字符串都可以用这个方法，题干通常会写最xxx的连续区间

- 问题209：长度最小的连续子数组

## 二分法
- 当需要遍历的时候，可以考虑使用二分法缩小搜索范围。
- 处理数组、字符串


## 排序
- vector的排序方式
```cpp
sort(nums.begin(), nums.end());
```

# 注意事项
- 删除元素前判断 元素所在的数据结构是否为空
- 添加 或者 遍历 元素要注意会不会溢出

## 定义
- 非严格递增序列：指的就是整个序列是从小到大的，但是里边会有一些数字会在它本身周围有重复。

## 冒号的使用
[参考链接](https://blog.csdn.net/weixin_41194129/article/details/109642051?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-109642051-blog-100737875.235%5Ev39%5Epc_relevant_yljh&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-109642051-blog-100737875.235%5Ev39%5Epc_relevant_yljh&utm_relevant_index=2)

## 下划线
- 跟python里的使用不一样，python里单下划线表示保护变量，双下划线表示私有变量。
- 在C++里建议不要用下划线开头的变量名字。

## 指针
- 一个指向 C++ 类的指针与指向结构的指针类似，访问指向类的指针的成员，需要使用成员访问运算符 ->。
- 类的对象的公共数据成员可以使用直接成员访问运算符 . 来访问。
- & 是取地址的符号
- 指针里面存的是地址，指针是一个变量，其值为另一个变量的地址，即，内存位置的直接地址。

```cpp
int a = 123;
int *p = &a;
cout<<*p;
//输出结果是123。
```

## const 
[参考链接](https://www.cnblogs.com/wintergrass/archive/2011/04/15/2015020.html)

## auto
[参考链接](https://blog.csdn.net/WLFIGHTER/article/details/50412761)
