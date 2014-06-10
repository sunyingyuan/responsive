＃Respond.js
＃＃＃快速轻巧polyfill最小/最大宽度CSS3媒体查询（为IE 6-8，及更多）

  - 版权所有2011：Scott Jehl, scottjehl.com

  - MIT许可授权。
 
这个脚本的目的是提供一个快速，轻量级的（3KB精缩/ 1KB gzip压缩）的脚本来启用[响应网页设计]（http://www.alistapart.com/articles/responsive-web-design/）在浏览器中不支持CSS3媒体查询 - 尤其是Internet Explorer 8和下。它用这样一种方式，它可能会修补其他非支持的浏览器的支持，以及（在不久的更多信息）。

如果你不熟悉周围的响应网页设计的概念，你可以阅读了[这里]（http://www.alistapart.com/articles/responsive-web-design/），也[这里]（包含http:// filamentgroup.com /例子/响应 - 图像/）

[演示页]（http://scottjehl.github.io/Respond/test/test.html）（颜色改为显示媒体查询工作）


使用说明
======

1，精心打造你的CSS的最小/最大宽度媒体查询从移动（第一）适应你的布局一路攀升到桌面


<PRE>
    @媒体屏幕和（最小宽度：480PX）{
        ...样式480PX和最多去这里
    }
</PRE>

2，毕竟你的CSS的职权respond.min.js脚本（1KB分钟/ gzip压缩）（先前它运行时，更大的机会IE浏览器的用户将不会看到一个闪光的未media'd内容）

3，破解打开Internet Explorer并在喜悦拳头泵


CDN / X-域设置
======

Respond.js的工作原理是通过AJAX请求你的CSS的原始副本，所以如果你的主机你的样式表在CDN（或子域），你需要上传一个代理页面启用跨域通信。

见`cross-domain/example.html`来演示：

- 上传`cross-domain/respond-proxy.html`到外部域
- 上传`cross-domain/respond.proxy.gif`你的原始域
- 通过`<link />`元素（s）参考文件（S）：

<PRE>
< - ！外部服务器上Respond.js代理 - >
<链接的href =“htt​​p://externalcdn.com/respond-proxy.html” ID =“响应代理”相对=“响应代理” />

< - ！Respond.js重定向本地服务器上的位置 - >
<链接的href =“/路径/到/ respond.proxy.gif” ID =“响应重定向”相对=“响应重定向” />

< - ！本地服务器上Respond.js代理脚本 - >
<script src="/path/to/respond.proxy.js"> </ SCRIPT>
</预>

如果你有问题的跨域设置，确保响应，proxy.html没有附加了查询字符串。

注：非常非常感谢@ doctyper在跨域代理的贡献！


支持与注意事项
======

一些注意事项要牢记：

- 这个脚本的重点是故意很窄：只有最小宽度和最大宽度媒体查询和所有的媒体类型（屏幕，打印等）将被转换为不支持的浏览器。我想保持简单的文件大小，维护和性能，所以我故意限制支持是必不可少的构建（手机优先）响应式设计的查询。在未来，我可以返工的事情有点包括钩修补，在其他媒体查询功能 - 敬请期待！

- 浏览器的原生支持CSS3媒体查询是选择出尽可能快地运行该脚本。在测试的支持，其他所有浏览器都受到一个快速测试，以确定它们是否支持媒体查询，或不进行运行脚本之前。这个测试是现在分别包括顶部，并使用window.matchMedia polyfill这里找到：https://github.com/paulirish/matchMedia.js。如果您已经通过Modernizr的或以其他方式包括本polyfill，随时删除该部分。

- 此脚本依赖于没有其他脚本或框架（除了包含matchMedia polyfill），并针对移动传输优化（〜1kb的总文件大小分钟/ gzip格式）

- 正如你可能已经猜到，这个实现是在问候CSS的解析规则相当愚蠢的。这是一件好事，因为这允许它运行非常快，但它的松动也可能会导致意外行为。例如：如果您奉上全媒体查询，在注释中拟禁用其规则，你可能会发现，这些规则将结束在非媒体查询支持的浏览器启用。

- Respond.js不分析通过CSS的@ import引用，也不会与风格元素中的媒体查询的工作，因为这些样式不能被重新请求进行解析。

- 由于安全限制，有些浏览器可能不允许该脚本工作的文件:/ /网址（因为它使用xmlHttpRequest的）。在Web服务器上运行它。

- 如果包括MQ特定样式的CSS文件的请求
  后面的重定向，Respond.js会默默的失败。 CSS文件应
响应一个200状态。

- 目前，媒体上的链接元素的属性都支持，但前提是链接的样式表中不包含媒体查询。如果它包含的查询，媒体属性将被忽略，内部查询将正常解析。换句话说，@在CSS优先采取媒体陈述。

- 据报道，如果CSS文件编码为UTF-8字节顺序标记（BOM），他们不会与Respond.js在IE7或IE8的工作。注意到在问题＃97

- 警告：包括媒体查询中的@ font-face规则会导致IE7和IE8加载过程中挂起。要解决这个问题，在敞开的地方的@ font-face规则，作为同级其他媒体查询。

- 如果您有引用超过32个样式表，IE浏览器会抛出一个错误，'无效的过程调用或参数`。串连你的CSS和问题应该消失。

- 不支持萨斯/ SCSS源地图; `@媒体萨斯 - 调试信息'将打破respond.js。注意到问题[＃148]（https://github.com/scottjehl/Respond/issues/148）

- Internet Explorer 9的支持CSS3媒体查询，但不是框架内，当包含媒体查询的CSS是在外部文件中（这似乎是在IE9中的错误 - 见http://stackoverflow.com/questions/10316247/media-查询 - 失败 - 内 - IE9-IFRAME）。看到这犯了修复，如果你有这个问题。 https://github.com/NewSignature/Respond/commit/1c86c66075f0a2099451eb426702fc3540d2e603

- 嵌套媒体查询不支持


怎样的工作？
======
基本上，脚本循环遍历页面中引用的CSS和运行在其内容的正则表达式或两个找媒体查询和CSS及其相关的块。在Internet Explorer中，样式表的内容是无法检索其预解析状态（在IE浏览器8 - ，表示其媒体查询是从文本中删除），所以Respond.js再次请求使用Ajax的CSS文件和解析来自那里的文本响应。请确保正确配置你的CSS文件“缓存使这一重新请求实际上并没有去到服务器，打你的浏览器缓存来代替。

从那里，每个媒体查询块是通过样式元素附加到头部的顺序，以及这些风格元素都启用和禁用（阅读：追加和删除从DOM），这取决于它们的最小/最大宽度与浏览器的宽度如何比较。在样式元素的媒体属性将匹配在CSS的查询，因此它可能是“屏幕”，“投影机”，或任何你想要的。包含在CSS中的任何相对路径将通过他们的样式表的href作为前缀，所以图像路径会直接给他们正确的目的地

API的选项？
======

- respond.update（）：重新运行该解析器（有益的，如果你添加了一个样式表的页面，它需要被翻译）
- respond.mediaQueriesSupported：设置为true，如果浏览器本身支持媒体查询。
- respond.getEmValue（）：返回一个EM的像素值


替代这个脚本
======
这是不是唯一的CSS3媒体查询polyfill脚本在那里;但它可能是最快的。

如果你正在寻找更强大的CSS3媒体查询支持，你可以检查出http://code.google.com/p/css3-mediaqueries-js/。在测试中，我发现，脚本，渲染复杂的响应设计（无论是在文件大小和性能）时，会明显慢，但它确实比支持这个脚本了很多媒体的查询功能。