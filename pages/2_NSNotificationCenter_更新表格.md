# NSNotification

假如我想要在user按下“儲存“，跳回rootview中的表格中顯示，就必須做到
table reload，這時就可以使用NSNotificationCenter，在完成儲存動作時
* (1)通知rootview
```
[[NSNotificationCenter defaultCenter] postNotificationName:@"refresh" object:self];
```

* (2)rootview收到refresh，呼叫ReloadDataFunction:來進行下一步
```
//也可以在object:nil 加上參數做傳送
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(ReloadDataFunction:) name:@"refresh" object:nil];
```
* (3)做reload動作    
```
- (void)ReloadDataFunction:(NSNotification *)notification {
    [table reloadData];
    //...
}
```
