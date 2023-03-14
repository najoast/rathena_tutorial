```
<map name>{,<x>{,<y>{,<xs>{,<ys>}}}}%TAB%monster%TAB%<monster name>{,<monster level>}%TAB%<mob id>,<amount>{,<delay1>{,<delay2>{,<event>{,<mob size>{,<mob ai>}}}}}

<地图名>{,<X坐标>{,<Y坐标>{,<X半径>{,<Y半径>}}}}%TAB%monster%TAB%<怪物名字>{,<怪物等级>}%TAB%<怪物ID>,<数量>{,<延迟1>{,<延迟2>{,<事件>{,<怪物大小>{,<怪物AI>}}}}}
```

# 生成位置
* `map name` 是怪物生成的地图名称
* `x` 和 `y` 是怪物生成的坐标，如果x和y都是0，怪物将在全地图随机生成
* `xs` 和 `ys` 是刷怪区域的X和Y方向的半径，如果xs和ys都是0，怪物将固定在x和y的位置生成
* 以上参数限定的区域只是刷怪时的初始区域，怪物一旦生成，就会在全地图随机移动

# 名字和等级
* `monster name` 是怪物在屏幕上的名字，与它们在其他地方的名字没有任何关系
* `monster level` 是怪物的等级，如果不指定，怪物将使用mob_db.txt里配置的等级。例如：`波利,50`会生成一个名为波利且等级为50的怪物
* 如果`monster name`为`--ja--`，则使用 `mob_db.txt` 的“日文名称”字段，（在 rAthena 中，它实际上包含一个英文名称）如果它是“--en--”， 它是怪物数据库中的“英文名称”（其中包含用于使用 GM 命令召唤怪物的大写名称）

# 怪物ID和数量
* `mob id` 标识了要生成的怪物在“mob_db.txt”怪物数据库中的记录
* 数量是执行此命令时将产生的怪物数量，它受“battle_athena.conf”中的产生率影响

# 重生延迟
* `delay1` 和 `delay2` 控制怪物重生延迟 - 第一个是固定的基础重生时间，第二个是基础时间之上的随机变化。 两个值都以毫秒为单位给出（1000 = 1 秒）。 请注意，服务器还强制执行 5 秒的最小重生延迟

# 事件
事件是当怪物被杀死时要执行的脚本事件。 

事件必须以`NPCName::OnEventName`的形式执行，事件名称标签应以“On”开头。 对于所有事件，如果 NPC 是触摸 NPC，触发脚本的玩家必须在“触发”范围内才能使事件生效。

示例：
```c
monster "prontera",123,42,"Poringz0rd",2341,23,"Master::OnThisMobDeath";

amatsu,13,152,4	script	Master	767,{
	mes "Hi there";
	close;

OnThisMobDeath:
	announce "Hey, " + strcharinfo(0) + " just killed a Poringz0rd!",bc_blue|bc_all;
	end;
}
```
Each time you kill one, that announce will appear in blue to everyone.

# 怪物大小和 AI
* `mob size` 是怪物的尺寸
* `mob ai` 是怪物的AI(人工智能)类型

```
<mob size> 可以是：
	Size_Small	(0) // 尺码_小号
	Size_Medium	(1) // 尺寸_中号
	Size_Large	(2) // 尺码_大号

<mob ai> 可以是：
	AI_NONE		(0)		(默认)
	AI_ATTACK	(1)		(攻击/友好)
	AI_SPHERE	(2)		(炼金技能)
	AI_FLORA	(3)		(炼金技能)
	AI_ZANZOU	(4)		(阳炎/奥博罗技能)
	AI_LEGION	(5)		(世拉技能)
	AI_FAW		(6)		(机械技能)
```

可以在地图上以 `SC_BOSSMAPINFO` 状态检测到使用“boss_monster”而不是“monster”生成的怪物。
