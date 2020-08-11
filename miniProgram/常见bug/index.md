## button 宽度设置无效问题？
  <button style="width: 100%">hello</button>

## 授权地理位置被拒绝后，重新拉起地理位置授权弹窗
```js
    // 位置授权弹窗
    wx.showModal({
      content: '检测到您没打开此小程序的定位权限，是否去设置打开？',
      confirmText: "确认",
      cancelText: "取消",
      success: function (res) {
        if (res.confirm) {
          wx.openSetting();
        }
      }
    })
```

## textarea 层级始终在弹窗上面

```html
  <view class="patient__textarea">
    <view wx:if="{{visibleConsume || visibleNorm || visiblePopupConsume}}" class="textarea_class">
    {{patientDesc ? patientDesc : '请简要介绍相关情况，便于护士了解症状，感谢您的配合'}}
    </view>
    <textarea wx:else class="textarea_class" value="{{commonParams.patientSymptom}}" placeholder="请简要介绍相关情况，便于护士了解症状，感谢您的配合" auto-height bindblur="bindPatientSymptoon" />
  </view>
```

## textarea 滚动错位


## rich-text 中设置图片大小问题
将富文本中的html中<img /> 设置width: 100%;
```js
    switchContent(data) {
      let swContent = data.content.replace(/<img/gi, "<img style='width:100%;height:auto!important;max-height:100%;width:100%;'");
      return swContent;
    }
```
## 视频组件
- video 与 swiper 一起使用
  1. 滑动时video pause第二次后不能暂停？
    pause定时器延迟
  2. 滑动时会改变video的进度条？
    enable-progress-gesture => false [关闭控制进度的手势]


## 获取access_token
  https://api.weixin.qq.com/cgi-bin/token?grant_type=client_credential&appid=APPID&secret=APPSECRET
## 获取小程序提审次数
  https://api.weixin.qq.com/wxa/queryquota?access_token=xx
