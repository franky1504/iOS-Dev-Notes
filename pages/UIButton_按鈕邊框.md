# 按鈕加上邊框
由於iOS7.0之後的UI設計概念改變，按鈕格式需手動調整才能像之前一樣

* 邊框的粗細
```
okButton.layer.borderWidth = 1.0;
```

* 邊框的顏色
```
okButton.layer.borderColor = [[UIColor redColor] CGColor];
```

* 邊角的弧度
```
okButton.layer.cornerRadius = 5.0;
```
