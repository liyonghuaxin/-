2019-05-09
1. 根据类名，获取已存在的controller
``` objc , obj-c
- (UIViewController *)getActivityViewController:(NSString *)controllerName {
    
    UIViewController *topVC = [UIApplication sharedApplication].keyWindow.rootViewController;
    
    while (topVC.presentedViewController) {
        topVC = topVC.presentedViewController;
        if ([[topVC.class description] isEqualToString:@"UINavigationController"]) {
            UINavigationController *navi = (UINavigationController *)topVC;
            if (navi && navi.viewControllers && navi.viewControllers.count > 0) {
                NSInteger count = navi.viewControllers.count;
                for (NSInteger i=count-1; i>=0; i--) {
                    UIViewController *controller = [navi.viewControllers objectAtIndex:i];
                    if ([[controller.class description] isEqualToString:controllerName]) {
                        return controller;
                    }
                }
            }
        }
    }
    
    return nil;
    
}
```
