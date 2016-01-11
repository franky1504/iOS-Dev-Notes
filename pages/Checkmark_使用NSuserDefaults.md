* Checkmark可在Tableview cell的最右側顯示勾勾，代表使用者選取此列，我們可以把結果記錄在NSUserDefaults供之後使用

* 生成key0.key1....keyN
```
- (NSString *)getKeyForIndex:(int)index {
    return [NSString stringWithFormat:@"KEY%d",index];
}
```
* 讀取keyN的BOOL值，是YES則回傳YES，NO則回傳NO
```
- (BOOL) getCheckedForIndex:(int)index {
    if([[[NSUserDefaults standardUserDefaults] valueForKey:[self getKeyForIndex:index]] boolValue]==YES) {
        return YES;
    } else {
        return NO;
    }
}
```
* 初始化key的值
```
- (void) checkedCellAtIndex:(int)index {
    BOOL boolChecked = [self getCheckedForIndex:index];
    [[NSUserDefaults standardUserDefaults] setValue:[NSNumber numberWithBool:!boolChecked] forKey:[self getKeyForIndex:index]];
    [[NSUserDefaults standardUserDefaults] synchronize];
}
```
* TABLE有幾列
```
- (NSInteger)tableView:(UITableView *)tableView numberOfRowsInSection:(NSInteger)section {
    return [DataArray count];
}
```
* 初始化CELL的TITLE，一開始key都是NO，所以Checkmark為None
```
- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath {
    static NSString *subviewCells = @"Cells";
    UITableViewCell *cell = [tableView dequeueReusableCellWithIdentifier:subviewCells];
    if (cell == nil) {
    cell = [[UITableViewCell alloc] initWithStyle:UITableViewCellStyleDefault reuseIdentifier:subviewCells];
    }

    cell.textLabel.text = [DataArray objectAtIndex:indexPath.row];
    if([self getCheckedForIndex:indexPath.row]==YES) {
        cell.accessoryType = UITableViewCellAccessoryCheckmark;
    } else {
        cell.accessoryType = UITableViewCellAccessoryNone;
    }

    return cell;
}
```
* 點擊CELL後要做什麼
```
- (void)tableView:(UITableView *)tableView didSelectRowAtIndexPath:(NSIndexPath *)indexPath {
    [tableView deselectRowAtIndexPath:indexPath animated:NO];

    UITableViewCell *cell = [tableView cellForRowAtIndexPath:indexPath];

    //key從NO變YES，Checkmark出現
    [self checkedCellAtIndex:indexPath.row];

    if([self getCheckedForIndex:indexPath.row]==YES) {
        cell.accessoryType = UITableViewCellAccessoryCheckmark;
    } else {
        cell.accessoryType = UITableViewCellAccessoryNone;
    }
}
```
