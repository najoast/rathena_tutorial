# 添加自定义道具

# 道具设计

| 道具ID | 道具名 | 类型 | 可用职业 | 功能 | 重量 |
| --- | --- | --- | --- | --- | --- |
| 30000 | 全栈药水 | 消耗品 | 全部 | 恢复所有生命值和魔法值 | 2 |
| 30001 | 初心者药水 | 消耗品 | 初心者 | 恢复所有生命值和魔法值 | 1 |
| 30002 | 随机药水 | 消耗品 | 全部 | 随机恢复50~100点生命值和魔法值 | 1 |
| 30003 | 解毒药水 | 消耗品 | 全部 |  解除中毒状态 | 1 |

# 添加步骤
1. 服务端 item_db 里添加数据
2. 客户端 iteminfo.lua 里添加数据

注：为了减轻工作量，可以找一个类似的道具复制一份，再在此基础上修改。

# 测试用到的GM命令或道具

### 修改HP和SP
```
@heal {<hp> {<sp>}}

恢复指定量的HP和SP。
如果没有给出参数，角色将被完全治愈。
```

### 加中毒状态
使用 `679` 这个道具，可以加中毒状态。道具描述上没写，但通过查代码发现其是可以加中毒状态的。

### 修改职业
```
@jobchange <job name>
@jobchange <job ID>
```

# 代码
## 服务端 (item_db_usable.yml)
```yml
  - Id: 30000
    AegisName: Fullstack_Potion
    Name: Fullstack Potion
    Type: Healing
    Buy: 100
    Weight: 20
    Script: |
      percentheal 100,100;
  - Id: 30001
    AegisName: Novice_Potion1
    Name: Novice Potion1
    Type: Healing
    Buy: 100
    Weight: 10
    Jobs:
      Novice: true
    Script: |
      percentheal 100,100;
  - Id: 30002
    AegisName: Random_Potion
    Name: Random Potion
    Type: Healing
    Buy: 100
    Weight: 10
    Script: |
      itemheal rand(50,100),rand(50,100);
  - Id: 30003
    AegisName: Antidote_Potion
    Name: Antidote Potion
    Type: Healing
    Buy: 100
    Weight: 10
    Script: |
      sc_end SC_POISON;
```

## 客户端 (iteminfo_true.lub)
```lua
[30000] = {
		unidentifiedDisplayName = "全栈药水",
		unidentifiedResourceName = "弧埃器记",
		unidentifiedDescriptionName = {
			"将全栈药草捣碎，制成的体力恢复剂。",
			"恢复所有生命值和魔法值",
			"^ffffff_^000000",
			"重量：1"
		},
		identifiedDisplayName = "全栈药水",
		identifiedResourceName = "弧埃器记",
		identifiedDescriptionName = {
 			"将全栈药草捣碎，制成的体力恢复剂。",
			"恢复所有生命值和魔法值",
			"^ffffff_^000000",
			"重量：2"
		},
		slotCount = 0,
		ClassNum = 0
	},
	[30001] = {
		unidentifiedDisplayName = "初心者药水",
		unidentifiedResourceName = "林全器记",
		unidentifiedDescriptionName = {
			"将初心者药草捣碎，制成的体力恢复剂。",
			"恢复所有生命值和魔法值",
			"^ffffff_^000000",
			"重量：1"
		},
		identifiedDisplayName = "初心者药水",
		identifiedResourceName = "林全器记",
		identifiedDescriptionName = {
 			"将初心者药草捣碎，制成的体力恢复剂。",
			"恢复所有生命值和魔法值",
			"^ffffff_^000000",
			"重量：1"
		},
		slotCount = 0,
		ClassNum = 0
	},
	[30002] = {
		unidentifiedDisplayName = "随机药水",
		unidentifiedResourceName = "畴鄂器记",
		unidentifiedDescriptionName = {
			"将随机药草捣碎，制成的体力恢复剂。",
			"随机恢复50~100点生命值和魔法值",
			"^ffffff_^000000",
			"重量：1"
		},
		identifiedDisplayName = "随机药水",
		identifiedResourceName = "畴鄂器记",
		identifiedDescriptionName = {
 			"将随机药草捣碎，制成的体力恢复剂。",
			"随机恢复50~100点生命值和魔法值",
			"^ffffff_^000000",
			"重量：1"
		},
		slotCount = 0,
		ClassNum = 0
	},
	[30003] = {
		unidentifiedDisplayName = "解毒药水",
		unidentifiedResourceName = "檬废倾宏",
		unidentifiedDescriptionName = {
			"将解毒药草捣碎，制成的体力恢复剂。",
			"解除中毒状态",
			"^ffffff_^000000",
			"重量：1"
		},
		identifiedDisplayName = "解毒药水",
		identifiedResourceName = "檬废倾宏",
		identifiedDescriptionName = {
 			"将解毒药草捣碎，制成的体力恢复剂。",
			"解除中毒状态",
			"^ffffff_^000000",
			"重量：1"
		},
		slotCount = 0,
		ClassNum = 0
	},
```
