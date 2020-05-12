基础库1.6.0开始支持

## 返回值

### 属性
- src  音频地址，用于直接播放
- startTime 开始播放的位置
- autoplay 是否自动开始播放
- loop 是否循环播放
- obeyMuteSwitch 是否遵循系统静音开关，默认true。设置false，用户打开静音开关也能继续发出声音。2.3.0 开始此参数不生效。
- duration 当前音频长度
- currentTime 播放位置
- paused 是否暂停或停止
- buffered 音频缓冲的时间点

### 方法
- InnerAudioContext.play() 播放
- InnerAudioContext.pause() 暂停
- InnerAudioContext.stop() 停止
- InnerAudioContext.seek(position) 跳转到指定位置
- InnerAudioContext.destory() 销毁当前实例
- InnerAudioContext.onCanplay() 监听音频进入可播放状态的事件
- InnerAudioContext.offCanplay() 取消监听音频进入可播放状态的事件
- InnerAudioContext.onPlay() 监听音频播放事件
- InnerAudioContext.offPlay() 取消监听音频播放事件
- InnerAudioContext.onPause() 监听音频暂停事件
- InnerAudioContext.offPause() 取消监听音频暂停事件
- InnerAudioContext.onStop() 监听影片停止事件
- InnerAudioContext.onEnded() 监听音频自然播放至结束的事件