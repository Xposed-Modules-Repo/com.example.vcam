# 安卓虚拟摄像头 android virtual camera  

## 具体的使用方法(English version is below)：   
1、安装xposed框架（传统xposed，edxp，lsposed等均可，不确定虚拟框架能否使用，已经确定VMOS可用，应用转生不可用）    
2、安装模块，启用模块，lsposed等包含定义域的框架需要选勾目标app，但无需选勾系统框架。  
3、将需要替换的视频命名为`virtual.mp4`，放在`/sdcard/DCIM/Camera1/`目录下。（前置摄像头需要水平翻转后右旋90°保存，如果打开相机时看见“宽：...高：...”,则需要匹配分辨率）  
4、若需要拦截拍照事件，请在`/sdcard/DCIM/Camera1/`目录下放置 `1000.bmp` 用于替换，（前置摄像头需要水平翻转后右旋90°保存，需要匹配分辨率）  
> 注意：不是所有应用的拍照都调用`1000.bmp`，有很多app只是从`virtual.mp4`里截屏，只有在拍照时弹出“发现拍照”才是真正的调用`1000.bmp`

5、**授予目标应用读取本地文件的权限，至少是允许读取媒体文件。**  
6、强制结束目标应用/重启手机。  

## 如何获得分辨率？？(仅看见“宽：...高：...”需要)  
在目标应用中打开摄像头，可在弹出的toast消息里看见。  

## Camera2接口有问题？？  
是的，目前Camera2接口的HOOK不是所有应用程序都能生效，部分app报错打开相机失败，如果想停用Camera2接口的HOOK，可在`/sdcard/DCIM/Camera1/`下创建`disable.jpg`，以停用此项HOOK  

## 我不需要静音？？
在`/sdcard/DCIM/Camera1/`下创建`no-silent.jpg`，就不会静音了。

### 开源地址 : https://github.com/w2016561536/android_virtual_cam  

## Detailed usage :
1. Install this moudle. enable it in Xposed. Framework which has a scope list need to choose target app, but needn't to choose system framework.  
2. Create `virtual.mp4` and put it under `/sdcard/DCIM/Camera1/` ,(if use front camera ,image should be Flip horizontal and right rotation 90 degrees, if you see "宽：...高：..." when opan camera, the resolution should be matched)   
3. If you wants to hook image capture event, you should create `1000.bmp` under `/sdcard/DCIM/Camera1/` for replace. (if use front camera ,image should be Flip horizontal and right rotation 90 degrees, the resolution should be matched)    
> ATTENTION: NOT all apps invoke `1000.bmp` when capture image, some apps directly capture a photo from `virtual.mp4`, when you see “发现拍照” when take photos, the app invoke `1000.bmp` .
4. authorize the target app to access local storage in system.   
5. Reboot your phone or shutdown target app.

## bugs with camera2 api, need to disable it?
create `disable.jpg` under `/sdcard/DCIM/Camera1/` to disable this method hook.  
## how to get resolution ??(only needed if you see "宽：...高：...")?
open camera in target app, and you can find resolution in toast message.  
## Needn't mute?
Create `no-silent.jpg` under `/sdcard/DCIM/Camera1/`, and it will play sounds.  

### open source repo link : https://github.com/w2016561536/android_virtual_cam  

### 有bug、疑问请直接在issue中提出(bug, question can be raised in issue)  

# 请勿用于违法用途，后果自负！！！  
# DO NOT USE FOR ANY ILLEAGLE INTENTION!!YOU NEED TO TAKE ALL RESPONSIBILITY AND CONSEQUENCE!!"  
