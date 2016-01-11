# 收起TextField的方法
## 觸控螢幕收
```
- (void)touchesBegan:(NSSet *)touches withEvent:(UIEvent *)event {
    if (![textfield isExclusiveTouch]) {
        [textfield resignFirstResponder];
    }
}
```

## 點擊RETURN收
```
– (BOOL)textFieldShouldReturn:(UITextField *)textField {
    [textField resignFirstResponder];
    return YES;
}
```
