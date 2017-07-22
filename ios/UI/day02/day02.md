#UILable
##属性
```objc
    @property(nonatomic,copy)   NSString           *text; 显示的文字

    @property(nonatomic,retain) UIFont             *font; 字体

    @property(nonatomic,retain) UIColor            *textColor; 
    文字颜色
    
    @property(nonatomic)        NSTextAlignment    textAlignment; 
    对齐模式（比如左对齐、居中对齐、右对齐） 
    
    @property(nonatomic) NSInteger numberOfLines; 
    文字行数
    
    @property(nonatomic)        NSLineBreakMode    lineBreakMode;
    //换行模式
    
    
       // 1.1 创建UILabel对象
    UILabel *label = [[UILabel alloc] init];
    
    // 1.2 设置frame
    label.frame = CGRectMake(100, 100, 202, 175);
    
    // 1.3 设置背景颜色
    label.backgroundColor = [UIColor redColor];
    
    // 1.4 设置文字
    label.text = @"da shen 11期最牛逼!!!!da shen da shen da shen da shen da shen ";
    
    // 1.5 居中
    label.textAlignment = NSTextAlignmentCenter;
    
    // 1.6 设置字体大小
    label.font = [UIFont systemFontOfSize:20.f];
    label.font = [UIFont boldSystemFontOfSize:25.f];
    label.font = [UIFont italicSystemFontOfSize:20.f];
    
    // 1.7 设置文字的颜色
    label.textColor = [UIColor whiteColor];
    
    // 1.8 设置阴影(默认是有值)
    label.shadowColor = [UIColor blackColor];
    label.shadowOffset = CGSizeMake(-2, 1);
    
    // 1.9 设置行数(0:自动换行)
    label.numberOfLines = 1;
    
    // 1.10 显示模式
    label.lineBreakMode =  NSLineBreakByTruncatingHead;
    
    /*
     NSLineBreakByWordWrapping = 0,  // 单词包裹,换行的时候会以一个单词换行
     NSLineBreakByCharWrapping,		// 字符包裹换行,换行的时候会以一个字符换行
     NSLineBreakByClipping,		// 裁剪超出的内容
     NSLineBreakByTruncatingHead,	// 一行中头部省略(注意:numberOfLines要为1): "...wxyz"
     NSLineBreakByTruncatingTail,	// 一行中尾部省略: "abcd..."
     NSLineBreakByTruncatingMiddle	// 一行中中间部省略:  "ab...yz"
     */
    
    
    // 2.0 添加到控制器的view中
    [self.view addSubview:label];


```

# UIImage
## contentMode 13种模式 解释


```objc
      // 1. 创建一个UIImageView对象
    UIImageView *imageView = [[UIImageView alloc] init];
    
    // 1.1 设置位置和尺寸
    imageView.frame = CGRectMake(100, 100, 180, 180);
    
    // 1.2 设置背景颜色
    //    imageView.backgroundColor = [UIColor purpleColor];
    
    // 1.3 设置图片
    imageView.image = [UIImage imageNamed:@"1"];
    
    /*
     
     UIViewContentModeRedraw, // 重新绘制 drawRect
     
     
     // 凡是带有Scale,图片可能会被拉伸或者压缩
     UIViewContentModeScaleToFill, // 压缩或者拉伸图片填充整个UIImageView
     
     // Aspect:适应, 会保持原有图片的宽高比
     UIViewContentModeScaleAspectFit, //压缩或者拉伸图片,保持宽高比,自适应填充
     UIViewContentModeScaleAspectFill, //压缩或者拉伸图片,保持宽高比,填充整个UIImageView
     
     // 凡是不带有Scale,图片不可能会被拉伸或者压缩
     UIViewContentModeCenter,
     UIViewContentModeTop,
     UIViewContentModeBottom,
     UIViewContentModeLeft,
     UIViewContentModeRight,
     UIViewContentModeTopLeft,
     UIViewContentModeTopRight,
     UIViewContentModeBottomLeft,
     UIViewContentModeBottomRight,
     */
    
    // 1.4 设置图片的内容模式
    imageView.contentMode = UIViewContentModeScaleAspectFill;
    
    
    // 2.把UIImageView加到控制器的view
    [self.view addSubview:imageView];
    
    // 处理超出的部分图片
    imageView.clipsToBounds =  YES;
```
##### 设置毛玻璃效果
```objc
    // 实现毛玻璃效果
    
    // 1.创建UIImageView对象
    UIImageView *imageView =[[UIImageView alloc] init];
    
    // 2.设置frame
    //    imageView.frame = CGRectMake(0, 0, self.view.frame.size.width, self.view.frame.size.height);
    imageView.frame = self.view.bounds;
    
    // 3.设置图片
    imageView.image = [UIImage imageNamed:@"1"];
    
    // 4.设置图片的模式
    imageView.contentMode = UIViewContentModeScaleToFill;
    
    // 5.设置毛玻璃
     // 5.1 创建UIToolBar对象
    UIToolbar *toolBar = [[UIToolbar alloc] init];
    toolBar.frame = imageView.bounds;
    [imageView addSubview:toolBar];
    
    // 5.2 设置toolBar的模式
    toolBar.barStyle = UIBarStyleBlack;
    

    // 6.把imageView加到控制器的View中
    [self.view addSubview:imageView];
```
# ImageView 的frame设置
### 第一种方式
```objc
      // 1.最常规的设置方式
    UIImageView *imageView = [[UIImageView alloc] init];
    imageView.frame = CGRectMake(100, 100, 267, 400);
    imageView.image = [UIImage imageNamed:@"1"];
    [self.view addSubview:imageView];
```
### 第二种方式
```objc
    // 2.根据图片的大小进行设置
    
    UIImageView *imageView = [[UIImageView alloc] init];
    // 2.1 先拿到图片对象
    UIImage *image = [UIImage imageNamed:@"1"];
    // 2.2 设置imageView的frame
    imageView.frame = CGRectMake(100, 100, image.size.width, image.size.height);
    // 2.3 添加图片
    imageView.image = image;



```

### 第三种方式
```objc
    // 3.初始化的时候直接设置
    UIImage *image = [UIImage imageNamed:@"1"];
    UIImageView *imageView = [[UIImageView alloc] initWithFrame:CGRectMake(100, 100, image.size.width, image.size.height)];
    imageView.image = image;

```

### 第四种方式
```objc
    // 4.初始化时默认设置 initWithImage:控件的尺寸===图片的尺寸
    UIImageView *imageView = [[UIImageView alloc] initWithImage:[UIImage imageNamed:@"1"]];
    // 改变UIImageView的位置
    imageView.center = CGPointMake(self.view.frame.size.width * 0.5, self.view.frame.size.height * 0.5);
    [self.view addSubview:imageView];
```
