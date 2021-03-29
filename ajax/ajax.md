## 什么是ajax
- Ajax是一种异步请求数据的web技术
- Ajax 提升用户体验，改善页面性能

## Ajax的原理
- 浏览器 -> XMLHttpRequest -> 服务器
- 浏览器让xhr向服务器要点数据
- 浏览器接着去干其他事
- xhr去向服务器请求数据
- 服务器返回数据给xhr
- xhr通知浏览器数据要回来了
- 浏览器收到xhr的数据渲染页面
(浏览器 -> 服务器)

## Ajax的实现
- 创建XMLHttpRequest对象
```js
var xhr = null
if (window.XMLHttpRequest) {
  xhr = new XMLHttpRequest()
} else {
  xhr = new ActiveXObject('icrosoft.XMLHTTP')
}

```

- 向服务器发送请求
```js
// xhr.open(methods, url, async)
// send(string)

xhr.open("POST", "test.html", true)
xhr.setRequestHeader('content-type', 'application/x-www-form-urlencode')
xhr.send("id=123&name=zs")

```

- 服务器响应处理

1. 以responseText获取字符串形式的数据
2. 以responseXML获取XML形式的数据
3. status
4. statusText

```js
// 同步处理
xhr.open("GET", "info.txt", false)
xhr.send()
xhr.responseText

// 异步处理
xhr.onreadstatechange= function() {
  if (xhr.readystate == 4 && xhr.status == 200) {
    xhr.responseText
  }
}

```

## GET&POST请求的差别
- get 请求参数拼接在url上, send()不用值
- post 请求参数放在请求体上，send('id=123') 需要键值对， 需要设置请求头 setRequesetHeader() 


## readyState
- 0 未初始化，未调用open()
- 1 启动，调用open(),但未调用send()
- 2 发送，调用send(),但未返回数据
- 3 接收，已返回部分数据，但未完全返回
- 4 完成，已返回全部数据，并可以在客户端使用

## status
- 1xx  接收的请求正在处理
- 2xx  请求正常，处理完成
- 3xx  需要附加操作，才能完成请求
- 4xx  服务器无法处理请求
- 5xx  服务器处理请求出错

## JQuery的ajax
```js
$.ajax({
  url: "",
  type: "GET",
  contentType: "",
  async: true,
  data: {},
  dataType: "",
  success: function(res) {}
})

```
