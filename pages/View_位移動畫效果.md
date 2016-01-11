# 可以利用移動物件，加上動畫效果，達到位移的目的
```
[UIView animateWithDuration:0.5 delay:0.0f options:UIViewAnimationOptionCurveEaseInOut animations:^{

//在animations:^{ }之間加入要做的位移詳細code，如將物件向右平移33 pixel
self.shiftView.frame = CGRectMake(self.shiftView.frame.origin.x, self.shiftView.frame.origin.y+33,
self.shiftView.frame.size.width, self.shiftView.frame.size.height);
} completion:^(BOOL finished){

//完成位移後要做的事可在completion:^{ }之間輸入
}];
```
