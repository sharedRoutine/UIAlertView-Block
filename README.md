UIAlertView-Block
=================

Dismiss Block for UIAlertView (useful in Tweaks)

Usage:
=====

```objc
BUIAlertView *av = [[BUIAlertView alloc] initWithTitle:@"Title" message:@"Message" delegate:nil cancelButtonTitle:@"Cancel" otherButtonTitles:@"Other Button", nil];
[av showWithDismissBlock:^(NSInteger buttonIndex, NSString *buttonTitle) {
  NSLog(@"Button Index: %d | Button Title: %@",buttonIndex,buttonTitle);
}];
```
