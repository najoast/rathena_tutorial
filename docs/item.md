# 道具配置的组成
道具的配置由两部分组成：
1. 服务端配置：除外观外的所有道具属性，包括ID、类别、功能、价格、掉落等
2. 客户端配置：道具的外观，包括名称、图标、描述等

## 服务端配置
服务端配置根据功能分布在以下几个文件内：
| 文件 | 说明 |
| --- | --- |
| `item_db.yml` | 入口文件，无实际道具配置 |
| `item_db_equip.yml` | 装备道具配置 |
| `item_db_usable.yml` | 消耗品道具配置 |
| `item_db_etc.yml` | 其他道具配置 |

拿红色药水为例，其配置如下：
```yml
  - Id: 501
    AegisName: Red_Potion
    Name: Red Potion
    Type: Healing
    Buy: 10
    Weight: 70
    Script: |
      itemheal rand(45,65),0;
```

关于每个字段的意义，在[这篇文档](https://github.com/najoast/rathena_script_commands/blob/master/doc/item_db.md)里有完整的描述。

## 客户端配置

### 道具基础配置
客户端配置在 `data\iteminfo.lub` 文件内，是一个 Lua 表。

格式如下：
```lua
	[501] = {
		unidentifiedDisplayName = "红色药水", -- 未鉴定时的名称
		unidentifiedResourceName = "弧埃器记", -- 未鉴定时的图标
		unidentifiedDescriptionName = { -- 未鉴定时的描述
			"将红色药草捣碎，制成的体力恢复剂。",
			"恢复^00008845～65^000000的HP",
			"依^000088(VITx2)%^000000增加恢复量",
			"^ffffff_^000000",
			"重量：7"
		},
		identifiedDisplayName = "红色药水", -- 已鉴定时的名称
		identifiedResourceName = "弧埃器记", -- 已鉴定时的图标
		identifiedDescriptionName = { -- 已鉴定时的描述
			"将红色药草捣碎，制成的体力恢复剂。",
			"恢复^00008845～65^000000的HP",
			"依^000088(VITx2)%^000000增加恢复量",
			"^ffffff_^000000",
			"重量：7"
		},
		slotCount = 0, -- 孔的数量
		ClassNum = 0
	}
```

说明：
不同的端，其配置文件并不一定是 `data\iteminfo.lub`，可以在DIFF客户端时修改这个文件的路径。
比如在 Pandas 里，该文件的路径为 `data\iteminfo_true.lub`。

### 道具图档

| 路径 | 格式 | 说明 |
| --- | --- | --- |
| `data\texture\蜡历牢磐其捞胶\collection` | bmp | 游戏里面鼠标右键显示描述时的图片 |
| `data\texture\蜡历牢磐其捞胶\item` | bmp | 游戏里面背包窗口中看到的小图片 |
| `data\sprite\酒捞袍` | spr | 游戏里面当拖拽物品，或者物品掉在地上时候的样子 |
| `data\sprite\酒捞袍` | act | act文件和spr文件是配套的，act文件用来记录对应的spr文件的动画序列 |

