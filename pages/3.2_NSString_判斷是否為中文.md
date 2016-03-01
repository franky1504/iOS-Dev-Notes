# 判斷字串是否為中文

```
- (BOOL)isChinese:(NSString *)unknownStr {
    NSRange range = NSMakeRange(0,1);
    NSString *subString = [unknownStr substringWithRange:range];
    const char *cString = [subString UTF8String];

    if (strlen(cString) == 3) {
        return YES;
    } else {
        return NO;
    }
}
```
