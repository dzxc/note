# UILable
### UILabe 属性

### UI控件响应事件移除拖线连接

#### 第一步

![第一步](images/Snip20170722_9.png)

#### 第二步

![第二步](images/Snip20170722_11.png)

### UI控件响应事件拖线连接的三种方式

#### 第一种

![第一种](images/Snip20170722_13.png)

#### 第二种

![第二种](images/Snip20170722_12.png)

#### 第三种

![第三种](images/Snip20170722_14.png)

### 可连线的UI控件直接拖到ControlView 的空白处，弹出创建方法对话框

![](images/Snip20170722_16.png)

### 注意

* 只有sendevent事件的对象才能连线方法
* 继承自UIControl对象的才能连线
* 一个控件可以对应多个事件 
* 一个控件也可以对应多个个属性，但尽量不要这么做

### 连线常见错误

####注意事项:
   1.凡是继承UIControl的类产生的对象,都能够实现点击
   2.如果不是继承UIControl的类产生的对象,都能不够实现点击
 
   经典的错误:
   一.错误一:
     描述: 
     reason: '[<MainViewController 0x7fd133746de0> setValue:forUndefinedKey:]: this class is not key value coding-compliant for the key testLabel.'
     原因: 有多余的连线
     解决: 删除多余的联系
 
  二.错误二
     描述:
     reason: '-[MainViewController clickRedBtn:]: unrecognized selector sent to instance 0x7f7f9254bee0'
     原因:在控制器中找不到对应的方法
     解决:  (一) 增加对应的方法  
           (二)删除多余的连线

---
# UIView

### 



