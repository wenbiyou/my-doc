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