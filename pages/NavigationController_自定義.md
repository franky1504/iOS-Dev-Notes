# 自訂Navigationbar (導航列) 的背景和文字Color
```
//設置NavigationBar背景颜色
[[UINavigationBar appearance] setBarTintColor:[UIColor redColor]];

//設置NavigationBar 中間title的顏色
[[UINavigationBar appearance] setTitleTextAttributes:@{NSForegroundColorAttributeName:[UIColor whiteColor]}];

//設置NavigationBar的背景為nav_bg.png這張圖
UIImage *navigationBar = [UIImage imageNamed:@"UINavigationBar"];
[[UINavigationBar appearance] setBackgroundImage:navigationBar forBarMetrics:UIBarMetricsDefault];

//initWithTitle後面的@""不填入東西
UIBarButtonItem *item = [[UIBarButtonItem alloc] initWithTitle:@"" style:UIBarButtonItemStylePlain target:nil action:nil];
self.navigationItem.backBarButtonItem = item;
```
