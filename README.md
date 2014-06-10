1.响应式布局开发流程：

    最好是从最小的屏幕向大屏幕渐进式开发
    响应式布局“移动优先”的思想使它很适宜采纳最简洁、最有效和最具语义的代码
    
2.视口调试工具：

    chrome插件：Windows Resizer
    Firefox插件：Firesizer
    
3.响应式布局网站欣赏：

    http://www.yixieshi.com/web/11120.html
    
4.设计网站的原则：“内容优先”

5.流式布局（媒体查询的默契配合）：

    百分比（控制布局） + em（控制字体）
    
6.固定像素宽度转换百分比宽度公式：

    目标元素宽度 / 上下文元素宽度 = 百分比宽度
    
7.设置自适应图片（响应式图片）p60 ：

    除了在客户端设置外
    还可能用到服务器端编程（实现Adaptive Images解决方案需要Apache 2、PHP 5.x和GD库）
    
8.弥补老版本浏览器缺陷的腻子脚本Modernizr

    Modernizr文件夹
    modernizr.js
    
9.HTML5样板文件：

    html5-boilerplate-4.3.0文件夹
    如果时间紧迫，但却需要一个好的项目起点，可以考虑HTML样板文件（http://html5boilerplate.com/）。样板文件时一个预先做好的融合了“最佳实践”HTML文件，包含一些基本样坏死（normalize.css 重置css样式，保证每个浏览器表现都一样）、polyfill和一些必要的工具如
    Modernizr。它还包含一个自动合并CSS和JS文件、自动删除注释以生成生产环境代码的构建工具。
    
10.css3特效前缀

    prefix-free文件夹
    prefixfree.min.js
    
