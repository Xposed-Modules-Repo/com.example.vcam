# android_virtual_cam

[简体中文](https://github.com/Xposed-Modules-Repo/com.example.vcam/blob/main/README.md) | [繁體中文](https://github.com/Xposed-Modules-Repo/com.example.vcam/blob/main/README_tc.md) | [English](https://github.com/Xposed-Modules-Repo/com.example.vcam/blob/main/README_en.md)

基于Xposed的虚拟摄像头

# 请勿用于任何非法用途，所有后果自负。

### 中国大陆加速地址（Gitee平台）： https://gitee.com/w2016561536/android_virtual_cam

## 支持平台：

- 安卓5.0+

## 使用方法

1. 安装此模块，并在Xposed中启用此模块，Lsposed等包含作用域的框架需要选择目标app，无需选择系统框架。
   
2. 在系统设置中，授予目标应用读取本地存储的权限，并强制结束目标应用程序。若应用程序未申请此权限，请见步骤3。
   
3. 打开目标应用，若应用未能获得读取存储的权限，则会以气泡消息提示，`Camera1`目录被重定向至应用程序私有目录`/[内部存储]/Android/data/[应用包名]/files/Camera1/`。若未提示，则默认`Camera1`目录为`/[内部存储]/DCIM/Camera1/`。若目录不存在，请手动创建。

> 注意：私有目录下的`Camera1`仅对该应用单独生效。

4. 在目标应用中打开相机预览，会以气泡消息提示“宽：……高：……”，需要根据此分辨率数据制作替换视频，放置于`Camera1`目录下，并命名为`virtual.mp4`，若打开相机并无提示消息，则无需调整视频分辨率。
   
5. 若在目标应用中拍照却显示真实图片，且出现气泡消息`发现拍照`和分辨率，则需根据此分辨率数据准备一张照片，命名为`1000.bmp`，放入`Camera1`目录下（支持其它格式改后缀为bmp）。如果拍照时无气泡消息提示，则`1000.bmp`无效。
   
6. 如果需要播放视频的声音，需在`/[内部存储]/DCIM/Camera1/`目录下创建`no-silent.jpg`文件。（全局实时生效）
   
7. 如果需要临时停用视频替换，需在`/[内部存储]/DCIM/Camera1/`目录下创建`disable.jpg`文件。（全局实时生效）

8. 如果觉得Toast消息烦，可以在`/[内部存储]/DCIM/Camera1/`目录下创建`no_toast.jpg`文件。（全局实时生效）

9. 目录重定向消息默认只显示一次，如果错过了目录重定向的Toast消息，可以在`/[内部存储]/DCIM/Camera1/`目录下创建`force_show.jpg`文件来覆盖默认设定。（全局实时生效）


## 常见问题

A1. 前置摄像头方向问题？  
Q1. 大多数情况下,替换前置摄像头的视频需要水平翻转并右旋90度，并且视频***处理后***的分辨率应与气泡消息内分辨率相同。但有时这并不需要，具体请根据实际情况判断。


Q2. 画面黑屏，相机启动失败？  
A2. 目前有些应用并不能成功替换（特别是系统相机）。或者是因为视频路径不对（是否创建了两级Camera1目录，如`./DCIM/Camera1/Camera1/virtual.mp4`，但只需要一级目录）。


Q3. 画面花屏？  
A3. 视频分辨率不对。

Q4. 画面扭曲，变形？  
A4. 请使用剪辑软件修改原视频来匹配屏幕。

Q5. 创建`disable.jpg`无效？  
A5. 如果应用版本`<=4.0`，那么`[内部存储]/DCIM/Camera1`目录下的文件对**具有访问存储权限**的应用生效，其余无权限应用应在**私有目录**下创建  
如果应用版本`>=4.1`，那么应在`[内部存储]/DCIM/Camera1`创建，无论目标应用是否具有权限。


## 反馈问题

请直接在issues中反馈，如果为BUG反馈，请附带Xposed**模块**日志信息。


## 致谢:

提供HOOK思路: https://github.com/wangwei1237/CameraHook  

H264硬解码： https://github.com/zhantong/Android-VideoToImages  

JPEG转YUV： https://blog.csdn.net/jacke121/article/details/73888732  
