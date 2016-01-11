## 以特定字元為基準作分割：
```
//以 "/" 來分割字串
NSArray* date = [@"10/04/2011″ componentsSeparatedByString: @"/"];
//分割結果為 {10,04,2011}
//objectAtIndex: 0 ＝ 10
NSString* day = [date objectAtIndex: 0];
```
