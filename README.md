UIAlertView-Block
=================

Dismiss Block for UIAlertView (useful in Tweaks)

Usage:
======

```objc
BUIAlertView *av = [[BUIAlertView alloc] initWithTitle:@"Title" message:@"Message" delegate:nil cancelButtonTitle:@"Cancel" otherButtonTitles:@"Other Button", nil];
[av showWithDismissBlock:^(NSInteger buttonIndex, NSString *buttonTitle) {
  NSLog(@"Button Index: %d | Button Title: %@",buttonIndex,buttonTitle);
}];
```
Usage in a Tweak:
=================

```objc

%hook SomeClass

-(void)executeSomething {
BUIAlertView *av = [[BUIAlertView alloc] initWithTitle:@"Execute?" message:@"Are you sure you want to execute this?" delegate:nil cancelButtonTitle:@"No" otherButtonTitles:@"Yes!", nil];
[av showWithDismissBlock:^(NSInteger buttonIndex, NSString *buttonTitle) {

  if ([buttonTitle isEqualToString:@"Yes!"]) {
    %orig; //call the original method
  }

}];
}
```

If you do this without using Blocks, you'd have to save %orig in a variable and call it from your own delegate method which needs to be added with %new...
