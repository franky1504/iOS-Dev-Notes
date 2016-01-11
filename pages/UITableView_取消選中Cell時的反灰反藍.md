## 有時候點擊table的cell背景會被反白成藍色或是灰色，這是可以取消的
```
- (void)tableView:(UITableView *)tableView didSelectRowAtIndexPath:(NSIndexPath *)indexPath {
    // 取消反白狀態
    [tableView deselectRowAtIndexPath:indexPath animated:NO];
}
```
