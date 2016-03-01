# TEXTFIELD靠右對齊 空白(SPACE)不顯示
在iOS7以後，Textfield在設定為靠右對齊時，按下空白鍵(space)並不會
即時顯示，必須等到輸入下一個字時才可以看到，雖然不會對資料造成什麼影
響，但卻有可能引起使用者的誤會

* 解決方法就是對輸入的字串做出判斷．

```
- (BOOL)textField:(UITextField *)textField shouldChangeCharactersInRange:(NSRange)range replacementString:(NSString *)string {
    // 當游標在最右端 且 輸入是空格(space)時
    if (range.location == textField.text.length && [string isEqualToString:@" "]) {
    // 自行加入空格在最後端
        textField.text = [textField.text stringByAppendingString:@"\u00a0"];
        return NO;
    }
    // 無輸入空格 不做任何動作
    return YES;
}
```
