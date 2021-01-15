## 什么是DOM
- 从页面视角看，DOM是生成页面最基础的数据结构
- 从JavaScript视角看，DOM提供给JavaScript操作的接口
- 从安全视角看，DOM过滤了一些不安全的内容

## DOM树是如何生成
  - HTML解析器：
    - HTML字节流 =》DOM结构
    - 网络进程加载多少数据，HTML解析器便解析多少数据
  - 字节流转换位DOM的三阶段
    - 通过分词器将字节流转换为Token
    - 将Token解析为DOM节点，并将DOM节点添加到DOM树中 【2、3一起进行】

## JavaScript是如何影响DOM生成的
- 执行到javaScript标签时，暂停整个DOM的解析，执行javaScript代码
- chrome浏览器优化 =》预解析操作
- javaScript线程阻塞DOM
  - 使用CDN加速javaScript加载
  - 压缩javaScript文件的体积
  - 如果javaScript没有操作DOM,可异步加载该JavaScript脚本【async、defer】
