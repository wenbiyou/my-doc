- 进程定义：
  * 一个进程就是一个程序的运行实例。
  * 启动一个程序时，操作系统会为该程序创建一块内存，用来存放代码、运行中的数据和一个执行任务的主线程的运行环境。
- 进程中任意一线程执行出错，都会导致整个进程崩溃
- 线程之间共享进程中的数据
- 一个进程关闭后，操作系统会回收进程所占用的内存
- 进程之间的内容相互隔离
  * 一个进程崩溃，不会影响其他进程
  * 进程之间通过IPC机制进行通信

单进程浏览器时代问题
- 不稳定
  * 插件的意外崩溃会引起整个浏览器的崩溃
  * 复杂的JavaScript代码引起渲染引擎模块的崩溃
- 不流畅
  * 渲染模块、javaScript执行环境、插件都运行在同一线程中
  * 无限循环的脚本
  * 内存泄漏
- 不安全
  * C/C++编写的插件可以获取操作系统的任意资源
  * 页面脚本可通过浏览器的漏洞来获取系统权限

多进程浏览器时代

早期多进程架构
Chrome页面运行在单独的渲染进程中，页面的插件运行在单独的插件进程中，进程之间通过IPC机制进行通信。
- 解决不稳定
  * 进程相互隔离，页面或插件崩溃，仅影响当前的页面进程或插件进程。
- 解决不流畅
  * javaScript 运行在渲染进程中，js阻塞也只影响当前的渲染页面，不会影响浏览器和其他页面。
  * 当关闭一个页面，整个渲染进程也被关闭，该进程所占用的内存都会被系统回收，解决了浏览器的内存泄漏问题。
- 解决安全问题
  * 使用安全沙箱（不能在你的硬盘上写入任何数据，也不能在敏感位置读取任何数据，保证了恶意程序无法突破沙箱去获取系统权限）

目前多进程架构
1个浏览器主线程、1个GPU进程、1个网络进程、多个渲染进程和多个插件进程
- 浏览器进程
  * 界面显示、用户交互、子进程管理、存储功能
- 渲染进程
  * 将HTML、CSS、JavaScript转化为网页
  * 排版引擎Blink和JavaScript引擎V8都运行在渲染进程中
  * 运行在沙箱模式下
  * Chrome会为每个Tab标签创建一个渲染进程
- GPU进程
  * 使用GPU初衷是为了实现3D CSS效果，
  * Chrome的UI界面都采用GPU绘制，使得GPU成为浏览器普遍的需求
- 网络进程
  * 页面网络资源加载
- 插件进程
  * 负责插件的运行
  * 插件易崩溃，通过插件进程来隔离
- 问题
  * 更高的资源占用 （每个进程都会包含公共基础结构的副本，如JavaScript运行环境）
  * 更复杂的体系架构

未来面向服务的架构
- 原来的各种模块会被重构成独立的服务，每个服务都可以在独立的进程中运行，访问服务必须使用定义好的接口，通过IPC通信，构建一个更内聚、松耦合、易于维护和扩展的系统






