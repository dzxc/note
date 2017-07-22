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
