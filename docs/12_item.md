# 道具数据库(item_db)字段说明

## Id
物品编号。

这个编号一般从`500`开始，目前最大到`1100006`，如果是自己新加物品，建议找一个空闲段来添加，以名未来和官方的冲突。
需要明确的一点是，不管找什么样的空闲段，都是有冲突风险的，我们只能找一个尽量偏僻的段来添加，以减少冲突的可能性。

配置示例
```yml
Id: 501
```

## AegisName
服务器内部使用的物品名称。

该名称会在脚本和查找中使用，因此不能使用空格。如果有空格，一般用下划线代替。

比如 `Red Potion` 会被写成 `Red_Potion`。
在脚本中引用示例：
```c
// 以下两行代码效果相同
getitem 501,1;
getitem Red_Potion,1;
```

配置示例
```yml
AegisName: Red_Potion
```

## Name
GM命令和脚本命令输出时使用的名称。

物品名称是否汉化不取决于这个字段，而是取决于客户端的`iteminfo.lub`文件。这个Name字段的作用主要就是在服务端脚本和指令中使用。
比如当使用`@idsearch 物品名称`指令来企图查询这个物品的编号或其他信息时，指令里面带的物品名称就必须等于item_db里面的这个Name字段，否则rathena找不到这个物品。

GM命令示例：
```
@idsearch 红色药水
@idsearch Red Potion
```

配置示例
```yml
Name: Red Potion
```

## Type
物品类型。

| 类型 | 说明 | 举例 |
| --- | --- | --- |
| `Healing` | 治疗类物品 | 红色药水/赤色药水/黄色药水 |
| `Usable` | 使用类物品 | 神秘箱子(使用后随机取得一项物品) |
| `Etc` | 其他物品 | 金币袋子/银币袋子/铜币袋子/家畜血/迷思力币 |
| `Armor` | 防具（盔甲/鞋子/头饰/披肩/装饰品） | 战士长靴 |
| `Weapon` | 武器 | 勇士的击刺长剑 |
| `Card` | 卡片 | 波利卡片/绿棉虫卡片/疯兔卡片 |
| `PetEgg` | 宠物蛋 | 野玫瑰蛋 |
| `PetArmor` | 宠物装备 | 鸭娃娃的星星按钮 |
| `Ammo` | 弹药(箭矢/子弹) | 毒箭矢/银色子弹 |
| `DelayConsume` | 延迟消耗物品（用于`itemskill`）。使用`itemskill`的物品在选择目标后被消耗。任何其他命令都不会消耗该物品。可用这个特性实现“不会被消耗的苍蝇翅膀” | 物理修改许可证/魔法修改许可证 |
| `ShadowGear` | 影子装备 | 横冲直撞的暗影盔甲/天空吹影武器 |
| `Cash` | 另一种延迟消耗物品，需要用户确认后才能使用 | 开发团队宝箱/运营团队宝箱/夏天之夜宝箱 |

配置示例
```yml
Type: Healing
```

## SubType
物品子类型。

武器子类型：
| 类型 | 说明 |
| --- | --- |
| `Fist` | 拳刃 |
| `Dagger` | 匕首 |
| `1hSword` | 单手剑 |
| `2hSword` | 双手剑 |
| `1hSpear` | 单手枪 |
| `2hSpear` | 双手枪 |
| `1hAxe` | 单手斧 |
| `2hAxe` | 双手斧 |
| `Mace` | 镰刀 |
| `Staff` | 法杖 |
| `Bow` | 弓 |
| `Knuckle` | 拳套 |
| `Musical` | 乐器 |
| `Whip` | 鞭子 |
| `Book` | 书 |
| `Katar` | 卡塔尔 |
| `Revolver` | 手枪 |
| `Rifle` | 狙击枪 |
| `Gatling` | 加特林 |
| `Shotgun` | 霰弹枪 |
| `Grenade` | 手榴弹 |
| `Huuma` | 胡玛 |
| `2hStaff` | 双手法杖 |

弹药子类型：
| 类型 | 说明 |
| --- | --- |
| `Arrow` | 箭矢 |
| `Dagger` | 短刀 |
| `Bullet` | 子弹 |
| `Shell` | 贝壳 |
| `Grenade` | 手榴弹 |
| `Shuriken` | 飞镖（手里剑） |
| `Kunai` | 钉头锤 |
| `CannonBall` | 炮弹 |
| `ThrowWeapon` | 投掷武器 |

卡片子类型：
| 类型 | 说明 |
| --- | --- |
| `Normal` | 普通卡片（默认） |
| `Enchant` | 附魔卡片 |

配置示例
```yml
SubType: 1hSword
```

## Buy
购买价格。

如果NPC商店在配置时没有指定购买价格，就会使用这里的值。
如果不配置，默认是`Sell`价格的2倍。

配置示例
```yml
Buy: 100
```

## Sell
出售价格。

也就是卖给NPC此物品时玩家能拿到的钱，如果不配置，默认是`Buy`价格的一半。

配置示例
```yml
Sell: 50
```

## Weight
物品重量。

这里填写1的话，表示物品重量是0.1（比如箭矢），这里填写10的话，才表示重量是1。

配置示例
```yml
Weight: 10
```

## Attack
武器的攻击力。

配置示例
```yml
Attack: 50
```

## MagicAttack
武器的魔法攻击力。（复兴后才有）

配置示例
```yml
MagicAttack: 50
```

## Defense
防具的防御力。

配置示例
```yml
Defense: 100
```

## Range
武器的攻击范围。

配置示例
```yml
Range: 1
```

## Slots
装备的卡槽数量。

配置示例
```yml
Slots: 1
```

## Jobs
可装备的职业。

| 职业 | 说明 |
| --- | --- |
| `All` | 所有职业 |
| `Novice` | 初心者 |
| `SuperNovice` | 超级初心者 |
| `Swordman` | 剑士   |
| `Wizard`   | 魔法师 |
| `Thief`    | 盗贼   |
| `Merchant` | 商人   |
| `Archer`   | 弓箭手 |
| `Ninja`    | 忍者   |
| `Acolyte`  | 侍僧   |
| `Alchemist` | 炼金术士 |
| `Assassin` | 刺客 |
| `BardDancer` | 吟游诗人/舞者 |
| `Blacksmith` | 铁匠 |
| `Crusader` | 十字军 |
| `Gunslinger` | 枪手 |
| `Hunter` | 猎人 |
| `KagerouOboro` | 狂战士/影舞者 |
| `Knight` | 骑士 |
| `Mage` | 法师 |
| `Monk` | 武僧 |
| `Priest` | 牧师 |
| `Rebellion` | 反叛者 |
| `Rogue` | 流氓 |
| `Sage` | 贤者 |
| `SoulLinker` | 灵魂链接者 |
| `StarGladiator` | 星灵斗士 |
| `Summoner` | 召唤师 |
| `Taekwon` | 泰坤 |

配置示例
```yml
# 示例一，所有职业可装备
Jobs:
  All: true

# 示例二，只有初心者和超级初心者可装备
Jobs:
  Novice: true
  SuperNovice: true

# 示例三，铁匠和骑士可装备
Jobs:
  Blacksmith: true
  Knight: true
```

## Classes
可装备的职业类型。

| 类型 | 说明 |
| --- | --- |
| `All` | 所有职业 |
| `Normal` | 普通职业（不含 宝宝职业/进阶职业/三转职业）|
| `Upper` | 进阶职业 (不含 进阶三转职业) |
| `Baby` | 宝宝职业 (不含 三转宝宝职业) |
| `Third` | 三转职业 (不含 进阶三转职业和三转宝宝职业) |
| `Third_Upper` | 进阶三转职业 |
| `Third_Baby` | 三转宝宝职业 |
| `Fourth` | 四转职业 |
| `All_Upper` | 所有进阶职业 |
| `All_Baby` | 所有宝宝职业 |
| `All_Third` | 所有三转职业 |

配置示例
```yml
# 示例一，所有职业可用
Classes:
  All: true

# 示例二，普通职业可用
Classes:
  Normal: true

# 示例三，普通职业和进阶职业可用
Classes:
  Normal: true
  Upper: true
```

## Gender
可装备的性别。

| 类型 | 说明 |
| --- | --- |
| `Female` | 女性 |
| `Male` | 男性 |
| `Both` | 男女都可 |

配置示例
```yml
Gender: Both
```

## Locations
装备的穿戴位置。

| 类型 | 说明 |
| --- | --- |
| `Head_Top` | 头饰上 |
| `Head_Mid` | 头饰中 |
| `Head_Low` | 头饰下 |
| `Armor` | 盔甲 |
| `Right_Hand` | 武器 |
| `Left_Hand` | 盾牌 |
| `Garment` | 披肩 |
| `Shoes` | 鞋子 |
| `Right_Accessory` | 右侧饰品 |
| `Left_Accessory` | 左侧饰品 |
| `Costume_Head_Top` | 时装-头饰上 |
| `Costume_Head_Mid` | 时装-头饰中 |
| `Costume_Head_Low` | 时装-头饰下 |
| `Costume_Garment` | 时装-披肩 |
| `Ammo` | 弹药/箭矢 |
| `Shadow_Armor` | 影子装备-盔甲 |
| `Shadow_Weapon` | 影子装备-武器 |
| `Shadow_Shield` | 影子装备-盾牌 |
| `Shadow_Shoes` | 影子装备-鞋子 |
| `Shadow_Right_Accessory` | 影子装备-右侧饰品(耳环) |
| `Shadow_Left_Accessory` | 影子装备-左侧饰品(吊坠) |
| `Both_Hand` | 武器+盾牌 |
| `Both_Accessory` | 左侧饰品+右侧饰品 |

配置示例
```yml
# 示例一，武器和盾牌位可装备
Locations:
  Both_Hand: true

# 示例二，盾牌位可装备
Locations:
  Left_Hand: true

# 示例三：头饰中、下（哥布林面具 2297）
Locations:
  Head_Low: true
  Head_Mid: true
```

## WeaponLevel
武器的等级。

| 值 | 说明 |
| --- | --- |
| `1` | 一级武器 |
| `2` | 二级武器 |
| `3` | 三级武器 |
| `4` | 四级武器 |

配置示例
```yml
WeaponLevel: 1
```

## EquipLevelMin
可装备的最低基础等级。

配置示例
```yml
EquipLevelMin: 10
```

## EquipLevelMax
可装备的最高基础等级。

配置示例
```yml
EquipLevelMax: 90
```

## Refineable
是否可精炼。

| 值 | 说明 |
| --- | --- |
| `true` | 可精炼 |
| `false` | 不可精炼 |

配置示例
```yml
Refineable: true
```

## Gradable
是否可 Grade 升阶。

配置示例
```yml
Gradable: true
```

## View
对于普通物品，为该物品定义一个替换的外观编号。

## AliasName
物品的别名。

这里填另一个物品的 `AegisName`，会使得该物品在视觉上看起来像另一个物品，而无需更改客户端数据。

## Flags
物品标记。

| 值 | 说明 |
| --- | --- |
| `BuyingStore` | 是否可以在个人商店中出售 |
| `DeadBranch` | 是否为枯树枝类物品 |
| `Container` | 是否为随机宝箱类物品 |
| `UniqueId` | 是否为唯一堆叠 |
| `BindOnEquip` | 是否装备后绑定 |
| `DropAnnounce` | 是否掉落时有特殊广播 |
| `NoConsume` | 使用后是否不消耗 |
| `DropEffect` | 是否掉落时有特殊效果 |

配置示例
```yml
# 单个标记
Flags:
  BuyingStore: true

# 多个标记
Flags:
  DeadBranch: true
  Container: true
  UniqueId: true
  BindOnEquip: true
  DropAnnounce: true
  NoConsume: true
  DropEffect: true
```

## Delay
物品的使用延迟。

| 值 | 说明 |
| --- | --- |
| `Duration` | 延迟的持续时间（秒） |
| `Status` | 用于跟踪延迟的状态名 |

配置示例
```yml
Delay:
  Duration: 5000
  Status: Reuse_Limit_F
```

## Stack
物品的堆叠数量。

| 值 | 说明 |
| --- | --- |
| `Amount` | 最大堆叠数量 |
| `Inventory` | 堆叠配置是否应用于背包 |
| `Cart` | 堆叠配置是否应用于购物车 |
| `Storage` | 堆叠配置是否应用于仓库 |
| `GuildStorage` | 堆叠配置是否应用于公会仓库 |

配置示例
```yml
Stack:
  Amount: 100
  Inventory: true
  Cart: true
  Storage: true
  GuildStorage: true
```

## NoUse
什么情况下物品无法使用。

| 值 | 说明 |
| --- | --- |
| `Override` | 继承道具组的该条配置 |
| `Sitting` | 坐下时无法使用 |

配置示例
```yml
NoUse:
  Sitting: true
```

## Trade
交易限制。

| 值 | 说明 |
| --- | --- |
| `Override` | 继承道具组的该条配置 |
| `NoDrop` | 不可丢弃 |
| `NoTrade` | 不可交易 |
| `TradePartner` | 可交易给伴侣 |
| `NoSell` | 不可出售 |
| `NoCart` | 不可放入购物车 |
| `NoStorage` | 不可放入仓库 |
| `NoGuildStorage` | 不可放入公会仓库 |
| `NoMail` | 不可放入邮件 |
| `NoAuction` | 不可放入拍卖行 |

配置示例
```yml
Trade:
  NoDrop: true
  NoTrade: true
  TradePartner: true
  NoSell: true
  NoCart: true
  NoStorage: true
  NoGuildStorage: true
  NoMail: true
  NoAuction: true
```

## Script
使用或装备物品时执行的脚本。

配置示例
```yml
# 红色药水
Script: |
  itemheal rand(45,65),0;

# 蓝色药水
Script: |
  itemheal 0,rand(40,60);
```


## EquipScript
当一件装备被穿戴时，将会执行的脚本代码。注意：不是所有的加成效果在这里都能生效。

配置示例
```yml
EquipScript: |
  sc_start SC_SUMMER,INFINITE_TICK,0;
```

## UnEquipScript
当一件装备被脱下时，将会执行的脚本代码。注意：不是所有的加成效果在这里都能生效。

配置示例
```yml
UnEquipScript: |
  sc_end SC_HIDING;
```
