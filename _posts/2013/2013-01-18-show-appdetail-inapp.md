---
layout: post
title: 使用SKStoreProductViewController显示Appstore内App详情(iOS6)
categories:
- iOS
tags:
- iOS
- 开发
---


=== 使用SKStoreProductViewController显示Appstore内App详情(iOS6)

iOS新增了一个StoreKit，其中提供了一个可以在程序内显示Appstore中的App详情界面的ViewController。对于推荐自家应用非常友好，可以在这个界面直接点击下载，不需要再跳到Appstore了。

```
- (void)presentAppStoreForID:(NSNumber *)appStoreID inView:(UIView *)view withDelegate:	(id<SKStoreProductViewControllerDelegate>)delegate withURL:(NSURL *)appStoreURL
{
    if(NSClassFromString(@"SKStoreProductViewController"))
    {
        
        SKStoreProductViewController *storeController = [[SKStoreProductViewController alloc] init];
        storeController.delegate = delegate;
        
        NSDictionary *productParameters = @{ SKStoreProductParameterITunesItemIdentifier : appStoreID };
        
        
        [storeController loadProductWithParameters:productParameters completionBlock:^(BOOL result, NSError *error)
         {
             if (result)
             {
                 [self presentViewController:storeController animated:YES completion:nil];
             }
             else
             {
                 //Warning
             }
         }];
    }
    else
    {
        [[UIApplication sharedApplication] openURL:appStoreURL];
    }
}
```
