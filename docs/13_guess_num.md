# 猜数游戏

每次点击NPC时，NPC会在1~10之间随机一个数，
玩家花10 Zeny猜一个数，如果猜对了，会奖励100 Zeny

# strcharinfo
```
strcharinfo(<type>{,<char_id>})
```
此函数将返回调用角色的名称、派对名称或公会名称。 它返回的内容由类型决定。

| 值 | 描述 |
| --- | --- |
| 0 | 角色的名字 |
| 1 | 他们所在的队伍的名称（如果有） |
| 2 | 他们所在公会的名称（如果有） |
| 3 | 角色所在地图的名称 |

如果角色不是任何队伍或公会的成员，则在请求该信息时将返回一个空字符串。

# if
这是基本的条件语句命令，也是该脚本语言中唯一可用的命令。

条件可以是任何表达式。 所有导致非零值的表达式都将被视为`真`，包括负值。 结果为零的所有表达式都被视为`假`。
| 表达式 | 真值 |
| --- | --- |
| 1 | 真 |
| 0 | 假 |
| -1 | 真 |

如果表达式的结果为`真`，则将执行其后面代码块里的代码。 否则，会继续判定后面的 `else if` 或 `else` 语句，如果没有则跳过。

```c
// 最简单的形式
if (<condition>) {
	<statement>
}

if (Zeny < 100) {
	mes "您的 Zeny 不足100";
	close;
}

// 带有else的形式
if (<condition>) {
	<statement>
} else {
	<statement>
}

if (Zeny < 100) {
	mes "您的 Zeny 不足100";
	close;
} else {
	mes "您有足够的 Zeny";
	close;
}

// 带有else if的形式
if (<condition>) {
	<statement>
} else if (<condition>) {
	<statement>
} else {
	<statement>
}

if (Zeny < 100) {
	mes "您的 Zeny 不足100";
	close;
} else if Zeny < 1000 {
	mes "您的 Zeny 不足1000";
	close;
} else if Zeny < 10000 {
	mes "您的 Zeny 不足10000";
	close;
} else {
	mes "您真是富的流油呢";
	close;
}
```

# Zeny
这是个预定义的变量，表示玩家身上的Zeny数量。
可以通过该变量获取玩家身上的 Zeny 数量，并进行修改。

> 在游戏内可通过 `@zeny <金币数量>` 指令修改身上的 Zeny，以方便测试。

```c
mes "您的 Zeny 数量是：" + Zeny;

// 直接设置 Zeny 的值为1000
Zeny = 1000;

// 增加 Zeny 的值为1000
Zeny += 1000;

// 减少 Zeny 的值为1000
Zeny -= 1000;
```

# rand
```
rand(<number>{,<number>});
```
返回随机数。
* 如果填一个参数，返回 `[0, number)` 之间的随机数。
* 如果填两个参数，返回 `[number1, number2]` 之间的随机数。

```c
rand(10) 可能返回 0、1、2、3、4、5、6、7、8 或 9
rand(0,9) 可能返回 0、1、2、3、4、5、6、7、8 或 9
rand(2,5) 可能返回 2、3、4 或 5
```

# input
```
input(<variable>{,<min>{,<max>}})
```
会在客户端弹出一个输入框，玩家输入数字或字符串后，可以在脚本内引用玩家输入的值。