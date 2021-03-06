# Release Notes - Windows

## 2.4.7.102 @2020.05.11
- BUG修复
    - 修复某些情况下收不到转码进度回调问题
- 其它变更
    - 调整SDK版本号命名规则

## 2.4.7.106 @2020.04.30
- BUG修复
    - 修复IM信令每次都重复发送一条问题
- 性能优化
    - 优化房间内其他人涂鸦渲染的流程性

## 2.4.6.103 @2020.04.13
- BUG修复
    - 修复上传本地文件后白板无法操作问题

## 2.4.6.95 @ 2020.04.08
- 新增回调
    - TEduBoardImageStatus 新增三个状态回调
        - TEDU_BOARD_IMAGE_STATUS_LOAD_ABORT 图片加载中断
        - TEDU_BOARD_IMAGE_STATUS_LOAD_TIMEOUT 图片加载超时
        - TEDU_BOARD_IMAGE_STATUS_LOAD_CANCEL 图片取消加载
    - onTEBRectSelected 框选工具选中回调
- 新增接口
    - TEduBoardInitParam 新增两个参数
        - progressEnable 启用加载图标
        - progressBarUrl 自定义加载图标
        - imageTimeout 图片加载超时
- BUG修复
    - 修复加载相同图片没有回调问题

## 2.4.4.82 @ 2020.03.20
- BUG修复
    - 修复传入参数含特殊符号时接口调用失败问题（单双引号及反斜杠可引发问题）
    - 修复上传文件导致白板翻页问题

## 2.4.4.78 @ 2020.03.14
- BUG修复
    - 白板中播放视频时，学生端自动播放的问题
    - 批量导入图片组时，对URL字符串长度进行限制(总长7K)，超长时同步返回空串，同时回调错误TEDU_BOARD_ERROR_DATA_TOO_LARGE
    - 去掉onGotoBoard多余回调，在一页PPT内有多个步时，只在最后一步/最前一步时才回调

## 2.4.4.73 @ 2020.03.09

- 替换内部mp4播放器为videojs
- 新增接口
    - AddImagesFile 批量导入图片到白板
    - SetHandwritingEnable 开启或关闭笔锋功能
    - IsHandwritingEnable 获取白板是否开启笔锋
- 新增回调
    - onTEBAddImagesFile 增加批量图片文件回调
- 参数变更
   - TEduBoardInitParam 的 smoothLevel 默认值变更为0
- 枚举变更
    - TEduBoardErrorCode 新增 TEDU_BOARD_ERROR_AUTH_TIMEOUT 服务鉴权超时，请务必处理此错误
    - TEduBoardWarningCode 新增 TEDU_BOARD_WARNING_IMAGESFILE_ALREADY_EXISTS
    - TEDU_BOARD_VIDEO_STATUS_PLAYING 变更为 TEDU_BOARD_VIDEO_STATUS_TIMEUPDATE

## 2.4.1.64 @ 2020.01.08

- 回调变更
    - onTEBFileUploadProgress回调参数fileId变更为path
    - onTEBFileUploadStatus回调参数fileId变更为path
- 接口变更
    - addImageElement支持添加本地图片
- 增加接口
    - 增加添加图片元素回调onTEBAddImageElement
    
## 2.4.0.60 @2019.12.06
- 增加接口支持视频播放功能
    - 添加视频文件 virtual const char *AddVideoFile(const char *url) = 0;
    - 显示或隐藏视频控制栏 virtual void ShowVideoControl(bool show) = 0;
    - 播放视频 virtual void PlayVideo() = 0;
    - 暂停视频 virtual void PauseVideo() = 0;
    - 跳转视频 virtual void SeekVideo(double time) = 0;
    - 是否同步本地视频操作到远端 virtual void SetSyncVideoStatusEnable(bool enable) = 0;
    - 定时同步视频状态到远端 virtual void StartSyncVideoStatus(uint32_t interval) = 0;
    - 停止同步视频状态 virtual void StopSyncVideoStatus() = 0;
- 增加接口支持H5页面展示功能
    - 添加H5页面 virtual const char *AddH5File(const char *url) = 0;
- 增加接口支持图片元素功能
    - 添加图片资源 virtual void AddImageElement(const char * url) = 0;

## 2.3.5.27 @2019.10.30
- IM兼容4.5.x版本
- 增加动画步数回调
- 增加获取课件缩略图接口
- 接口改动：
	- class TEduBoardList 改名为 class TEduBoardStringList
	- TEduBoardList::GetBoard 改名为 TEduBoardStringList::GetString

## 2.3.4.18 @2019.09.29
- 修复大文件上传Crash问题

## 2.3.3.48 @2019.08.15
- 支持时间戳同步机制（用于配合较大延迟的音视频方案使用）

## 2.3.2.46 @2019.08.13
- 屏蔽文件拖动事件，防止拖入文件导致页面跳转后白板无法使用问题

## 2.3.2.45 @2019.08.07
- 避免各端样式不一致，统一使用白板内置字体，删除字体设置相关接口及初始化参数
- 历史数据加载过程中禁止进行白板操作，增加非法操作枚举值
- 增加添加转码文件接口
- 增加直线样式设置接口及相应枚举值
- 增加椭圆绘制模式设置接口及相应枚举值
- 更新CEF及Chromium内核版本到76.0.3809.87

## 2.3.0.40 @2019.07.27
- 白板消息优先级调整到最高
- 修复初始化参数实验性字段为空时crash问题

## 2.3.0.36 @2019.07.12
- 更新Windows&Linux的Chromium版本到75.0.3770.100
- Windows&Linux适配新版CEF接口
- Windows&Linux离屏渲染模式下禁用JS弹窗
- Windows&Linux增加白板HTML加载失败自动重试选项
- Windows&Linux白板HTML文件上云

## 2.2.2.34 @2019.07.03
- 修复设置白板背景图接口功能异常

## 2.2.2.33 @2019.06.28
- 监测Render进程Crash并打印日志
- AddFile和AddH5PPTFile接口同步返回文件ID
- 文件上传进度回调和文件上传结果回调返回文件ID参数
- 修复某些接口参数传nullptr会Crash的问题
- 修复白板延迟显示会导致文本工具无法切换中文输入法问题

## 2.2.1.29 @2019.06.27
- 修复偶现接口调用返回nullptr问题

## 2.2.1.28 @2019.06.24
- 修复收不到白板初始化完成回调问题
- 添加和删除白板回调改为批量回调
- 增加是否启用SDK内置Loading图标的初始化参数

## 2.2.0.21 @ 2019.06.20
- 支持mp4播放
- 支持磁盘cache缓存

优化
 - 翻页接口增加参数，支持是否重置动画步数（prevBoard, nextBoard, gotoBoard）
 - 历史数据及资源加载增加loading图标
 - 白板预加载支持跨文件预加载
 - 动画PPT支持直接加载到指定页和指定步
 - 修复已知bug

新增功能
 - 新增根据文件ID获取文件信息接口getFileInfo
 - 错误事件新增历史数据同步失败和白板内部运行错误事件

## 2.1.0.16 @ 2019.06.12
- 支持设置日志文件路径

## 2.1.0.15 @ 2019.05.30
- 修复onTEBFileUploadStatus回调参数异常问题

## 2.1.0.14 @ 2019.05.29
- 支持静态PPT页面预加载
- 笔迹优化（铅笔工具曲线平滑）
- 支持禁止数据同步（不将本地数据同步到远端）
- 橡皮擦工具支持滑动擦除
- 添加的H5PPT已存在时抛出警告
- 支持独立设置每个白板宽高比
- 支持白板缩放及拖动查看

## 2.0.0.6 @ 2019.05.17
- 修复中文路径下无法初始化问题

## 2.0.0.1 @ 2019.05.15
- 新增鼠标工具类型TEDU_BOARD_TOOL_TYPE_MOUSE
- 支持设置H5背景
- 白板支持并发文件上传

## 2.0.0_RC3 @ 2019.05.10
- 支持设置文本样式及字体属性
- 初始化接口支持传入所有属性初始值
- 初始化支持设置白板宽高比
- `AddFile` 接口支持传入COS转码URL

## 2.0.0_RC2 @ 2019.05.08
1. 新增功能支持：
    - PPT动画展示
2. 新增服务：
    - PPT动画转码服务
3. 问题修复
    - 白板修复禁用CEF初始化后收不到回调问题

## 2.0.0_RC1 @ 2019.04.26
- 涂鸦（铅笔、橡皮、激光教鞭、直线、空心椭圆、空心矩形、实心椭圆、实心矩形、文本）
- 背景色、背景图
- 点选、框选、移动涂鸦、撤销、重做
- 白板缩放、移动
- 文件展示（静态：支持PPT、PDF、WORD、EXCEL）、多文件支持

        


