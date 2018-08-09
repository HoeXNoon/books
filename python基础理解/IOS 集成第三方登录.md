```
IOS 集成第三方登录
     我使用的是友盟上集成的第三方登录功能，一共使用了三个应用的登录授权，QQ、微信、新浪微博。由于第三方登录授权成功后，需要跳转到一个新的界面，所以这里需要在项目里设置第三方登录的SSO授权。就是必须安装了相关的手机客户端后，才能使用第三方登录，在使用第三方登录时，我们需要先判断一下用户手机上是否已经安装了对应的应用。

一、集成SSO授权

    这里集成SSO授权的方法我就不详细讲解了，因为还涉及到注册第三方平台帐号这些琐屑的事。下面我给一个友盟上集成SSO授权的地址，文档说明都是很详细的

地址:http://dev.umeng.com/social/ios/detail-share#6  如果你中途遇到任何问题，都可以在这里留言，接下去我主要是贴代码和实现效果截图。

二、第三方登录实现代码

这里首先需要实现功能的ViewController中引入对应的库

#import "UMSocial.h"

#import "WXApi.h" 

#import <TencentOpenApi/QQApiInterface.h> 

#import "WeiboSDK.h"

下面的方法就是就是上面代码中UIImageView  *shareButton绑定的手势，这里为什么要使用UIImageView,

因为我代码布局中 shareButton的宽度和高度没有固定，是根据屏幕的宽度来计算的，如果使用UIButton就会出现

贴的图片的大小不会随着动态计算出的高宽而缩放  1 //公用的跳转用户资料详情页面

 
```



```
//公用的跳转用户资料详情页面
-(void)thirdSDKLogin:(UITapGestureRecognizer *)sender

{
    UIImageView *view=(UIImageView *)sender.self.view;
    if (view.tag==123456 ) {
        //判断微信客户端是否安装
        if ([WXApi isWXAppInstalled]) {
            NSString *platformName = [UMSocialSnsPlatformManager getSnsPlatformString:UMSocialSnsTypeWechatSession];
            
            UMSocialSnsPlatform *snsPlatform = [UMSocialSnsPlatformManager getSocialPlatformWithName:UMShareToWechatSession];
            
            snsPlatform.loginClickHandler(self,[UMSocialControllerService defaultControllerService],YES,^(UMSocialResponseEntity *response){
                
                NSLog(@"login response is %@",response);
                
                //获取微博用户名、uid、token等
                
                if (response.responseCode == UMSResponseCodeSuccess) {
                    
                    UMSocialAccountEntity *snsAccount = [[UMSocialAccountManager socialAccountDictionary] valueForKey:platformName];
                    
                    NSLog(@"username is %@, uid is %@, token is %@,iconUrl is %@",snsAccount.userName,snsAccount.usid,snsAccount.accessToken,snsAccount.iconURL);
                    
                }
                
            });
        }
        else
        {
            showMessage(@"请先安装微信客户端。");
            return;
        }

    }
     else if(view.tag==123457)
     {
         //判断qq客户端是否安装
         if ([QQApiInterface isQQInstalled]) {
             NSString *platformName = [UMSocialSnsPlatformManager getSnsPlatformString:UMSocialSnsTypeMobileQQ];
             
             UMSocialSnsPlatform *snsPlatform = [UMSocialSnsPlatformManager getSocialPlatformWithName:UMShareToQQ];
             
             snsPlatform.loginClickHandler(self,[UMSocialControllerService defaultControllerService],YES,^(UMSocialResponseEntity *response){
                 
                 NSLog(@"login response is %@",response);
                 
                 //获取微博用户名、uid、token等
                 
                 if (response.responseCode == UMSResponseCodeSuccess) {
                     
                     UMSocialAccountEntity *snsAccount = [[UMSocialAccountManager socialAccountDictionary] valueForKey:platformName];
                   NSLog(@"username is %@, uid is %@, token is %@,iconUrl is %@",snsAccount.userName,snsAccount.usid,snsAccount.accessToken,snsAccount.iconURL);
                     
                 }
                 
             });
         }
         else{
             showMessage(@"请先安装qq客户端。");
             return;
         }
     }
     else
     {
         
         //判断sina客户端是否安装
         if ([WeiboSDK isCanShareInWeiboAPP])
             
         {
             /*新浪登录第三方登录授权*/
             NSString *platformName = [UMSocialSnsPlatformManager getSnsPlatformString:UMSocialSnsTypeSina];
             UMSocialSnsPlatform *snsPlatform = [UMSocialSnsPlatformManager getSocialPlatformWithName:UMShareToSina];
             
             snsPlatform.loginClickHandler(self,[UMSocialControllerService defaultControllerService],YES,^(UMSocialResponseEntity *response){
                 
                 NSLog(@"response is %@",response);
                 
                 if (response.responseCode == UMSResponseCodeSuccess) {
                     
                     UMSocialAccountEntity *snsAccount = [[UMSocialAccountManager socialAccountDictionary] valueForKey:platformName];
                     
                     NSLog(@"=========%@",snsAccount.accessToken);
                     
                 }
                 
             });

             
         }
         
         else
             
         {
             
             showMessage(@"请先安装新浪微博客户端。");
             return;
             
             
         }
     }
}
```

