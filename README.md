# 虚拟摄像头 virtual camera  

## 具体的使用方法(English version is below)：  
1、安装xposed框架（xposed，edxposed，lsposed等均可，不确定虚拟框架能否使用，已经确定VMOS可用，应用转生不可用）  
2、安装模块，启用模块，lsposed等包含定义域的框架需要选勾目标app，但无需选勾系统框架。  
3、将需要替换的视频命名为virtual.mp4，放在/sdcard/DCIM/Camera1/目录下。（前置摄像头需要水平翻转后右旋90°保存，拦截onPreviewFrame需要匹配分辨率）  
4、若需要拦截拍照事件，请在/sdcard/DCIM/Camera1/目录下放置 1000.bmp 用于替换，（前置摄像头需要水平翻转后右旋90°保存，需要匹配分辨率）  
5、**在系统设置中授予目标应用访问存储的权限。**   
6、强制结束目标应用/重启手机。  

## Camera2接口HOOK有问题，需要停用？  
在/sdcard/DCIM/Camera1/下创建disable.jpg，以停用此项HOOK  

## 如何获得分辨率？？(仅拦截onPreviewFrame和拍照需要)
在目标应用中打开摄像头，可在弹出的toast消息里看见。  

### 开源地址：https://github.com/w2016561536/android_virtual_cam   

## Detailed usage :  
1. Install Xposed framework (Xposed, Lsposed, Edxposed are supported, I'm not sure whether virtual Xposed framework works).  
2. Install this moudle. enable it in Xposed. Framework which has a scope list need to choose target app, but needn't to choose system framework.  
3. Create virtual.mp4 and put it under /sdcard/DCIM/Camera1/ ,(if use front camera ,image should be Flip horizontal and right rotation 90 degrees, if you want to hook onPreviewFrame ,the resolution should be matched)  
4. If you wants to hook image capture event, you should create 1000.bmp under /sdcard/DCIM/Camera1/ for replace. (if use front camera ,image should be Flip horizontal and right rotation 90 degrees, the resolution should be matched)  
5. **authorize the target app to access local storage in system.**  
6. Reboot your phone or shutdown target app.  

## bugs with camera2 api, need to disable it?  
create disable.jpg under /sdcard/DCIM/Camera1/ to disable this method hook.  

## how to get resolution ??(only hook onPreviewFrame and image capture need it)?  
open camera in target app, and you can find resolution in toast message.  

### open source repo link : https://github.com/w2016561536/android_virtual_cam  

### 有bug、疑问请直接在issue中提出(bug, question can be raised in issue)  

# 请勿用于违法用途，后果自负！！！  
# DO NOT USE FOR ANY ILLEAGLE INTENTION!!YOU NEED TO TAKE ALL RESPONSIBILITY AND CONSEQUENCE!!"  
