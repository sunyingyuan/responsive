#jQuery的响应菜单插件
了一个插件，可将您的网站的导航到一个下拉（<'select>'）当浏览器是手机的宽度。

##Options
可用于插件的选项列表如下。
它们的默认值旁边的自己的名字出现，并可用值下面的描述。

###combine[true]
多个导航列表转换成手机一个下拉
[true/false]

###groupPageText ['Main']
任何'<li>'元素'<ul> / <ol>'目前被转换到'<optgroup>'。
由于'<optgroup>'是不可选的，一个"dummy"的<option>加在该组的顶配'<li>'的值。
此选项设置的文本"dummy"<option>
['string']

###nested[true]
这变成了<optgroup> on和off
[true/false]

###prependTo ['body']
设置为菜单被放入容器元素。
['CSS选择器']

###switchWidth [480]
设置宽度（以像素为单位），在该网站的menu（s）将变更为<select>

###topOptionText [“Select a page”]
设置第一个<option>`的显示文本。
此设置为NULL会阻止它显示
['string'/null]

##用法
该插件可以像任何其他jQuery插件：

$（'CSS选择器'）mobileMenu（{option:value, option:value}）;
