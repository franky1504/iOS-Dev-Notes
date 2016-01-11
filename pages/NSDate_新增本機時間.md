# 新增本機時間

* 取得手機的時間
```
NSDate *date = [NSDate date];
```

* 時間格式設定 YYYY-MM-dd
```
NSDateFormatter *dateform = [[NSDateFormatter alloc] init];
[dateform setDateFormat:@"YYYY-MM-dd"];
```

* 並且可以根據需求，轉換成string
```
NSString *dateString = [dateform stringFromDate:date];
* 或是date type使用
NSDate *dateDate = [dateform dateFromString:dateString]; 
```