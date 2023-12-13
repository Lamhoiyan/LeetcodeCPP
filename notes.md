

# 数据结构
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
- 获取子字符串 ：从位置0开始，取出两个元素。
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

