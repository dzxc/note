##### 自定义控件补充点
```objc
    /**
     * 注意: 创建对象用[[xxx alloc]init]方法和[[xxx alloc]initWithFrame]:方法都会调用initWithFrame:
     */
    - (instancetype)initWithFrame:(CGRect)frame{
        if (self =[super initWithFrame:frame]) {
            [self setUp];
        }
        return self;
    }
    // 展示xib
    
    // 方式一

    UIView *carView = [[[NSBundle mainBundle] loadNibNamed:@"CarView" owner:nil options:nil] firstObject];
    carView.frame = CGRectMake(0, 100, 200, 50);
    //    carView.clipsToBounds = YES;
    [self.view addSubview:carView];
    
    // 方式二
    //    UINib *nib = [UINib nibWithNibName:@"CarView" bundle:nil];
    //    UIView *carView = [[nib instantiateWithOwner:nil options:nil] firstObject];
    //
    //    [self.view addSubview:carView];
```