## 使用Storyboard
* 必須先在目標Viewcontroller初始化一個public變數

* 必須先到Storyboard中，設定要被傳遞訊息的target view id
```
Visit_dataShowViewController *detailView = [self.storyboard instantiateViewControllerWithIdentifier:@"detail"];
//傳遞參數 將visitData 傳給 detailView 的變數 DetailItem
[detailView setDetailItem:visitData];
//切換畫面
[self.navigationController pushViewController:detailView animated:YES];
```

## 使用Segue

* 必須先到Storyboard中，為segue設定id如：@"editv" 

* 當一個view中有多條segue時，就必須透過if的判斷來知道要push的是哪一個view
```
- (void)prepareForSegue:(UIStoryboardSegue *)segue sender:(id)sender {
    if ([segue.identifier isEqualToString:@"editv"]) {
    id page2 = segue.destinationViewController;

    //將值透過Storyboard Segue帶給頁面2的IdItem & edit變數
    [page2 setValue:detailItem forKey:@"IdItem"];
    [page2 setValue:@"YES" forKey:@"edit"];
    }
}
```
