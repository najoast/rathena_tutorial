
-------------------------
# mes

```c
mes "Hello,world!";
```

注意：默认是没有关闭或next按钮的，必须用 `close/next` 命令创建。如果不创建这些按钮，客户端就什么也做不了了，只能重启客户端，所以时刻记得加上这些按钮很重要。

### 颜色
* ^RGB 16 进制
* 用完记得还原
* 非英文字符要留空格，否则可能解析出错
* 可以 uTools 里的颜色插件来预览颜色

```c
mes "This is ^FF0000 red ^000000 and this is ^00FF00 green, ^000000 so.";
```

### 多行
```c
//一行代码显示三行
mes "Line 1", "Line 2", "Line 3";
```

### 导航
2011-10-10 之后的客户端才可以用导航链接。

语法：

```xml
<NAVI>显示名字<INFO>地图名,x,y,0,000,标记</INFO></NAVI>
```
`标记` 参数可以是：
* 0：不打开导航窗口（默认）。
* 1：打开导航窗口。

下面的示例将使 [Tool Shop] 文本可点击并开始导航。
单击时转到艾伯塔省的 (98,154)。

```c
mes "你去过<NAVI>[工具店]<INFO>alberta,98,154,0,000,0</INFO></NAVI>了吗?";
```

### 道具

格式：

```xml
<ITEM>显示名字<INFO>道具ID</INFO></ITEM>
```

* 显示名字是玩家看到的名字，可以填任意值。
* 道具ID是`item_db.yml`里的Id字段。决定了点击后显示的道具信息。


示例：
```c
mes "你消耗过<ITEM>红色药水<INFO>501</INFO></ITEM>吗?";
```

### 超链接
同样，您可以创建指向在新窗口中启动的网站的链接：

```xml
<URL>显示名字<INFO>http://www.example.com/</INFO></URL>";
```
