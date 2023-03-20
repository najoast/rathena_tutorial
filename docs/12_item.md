# 道具数据库(item_db)字段说明

## Id
物品编号。

这个编号一般从`500`开始，目前最大到`1100006`，如果是自己新加物品，建议找一个空闲段来添加，以名未来和官方的冲突。
需要明确的一点是，不管找什么样的空闲段，都是有冲突风险的，我们只能找一个尽量偏僻的段来添加，以减少冲突的可能性。

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

## Name
GM命令和脚本命令输出时使用的名称。

物品名称是否汉化不取决于这个字段，而是取决于客户端的`iteminfo.lub`文件。这个Name字段的作用主要就是在服务端脚本和指令中使用。

比如当使用`@idsearch 物品名称`指令来企图查询这个物品的编号或其他信息时，指令里面带的物品名称就必须等于item_db里面的这个Name字段，否则rathena找不到这个物品。

示例：
```
@idsearch 红色药水
@idsearch Red Potion
```

## Type
物品类型。

| 类型 | 说明 | 举例 |
| --- | --- | --- |
| Healing | 治疗类物品 | 红色药水/赤色药水/黄色药水 |
| Usable | 使用类物品 | 神秘箱子(使用后随机取得一项物品) |
| Etc | 其他物品 | 金币袋子/银币袋子/铜币袋子/家畜血/迷思力币 |
| Armor | 防具（盔甲/鞋子/头饰/披肩/装饰品） | 战士长靴 |
| Weapon | 武器 | 勇士的击刺长剑 |
| Card | 卡片 | 波利卡片/绿棉虫卡片/疯兔卡片 |
| PetEgg | 宠物蛋 | 野玫瑰蛋 |
| PetArmor | 宠物装备 | 鸭娃娃的星星按钮 |
| Ammo | 弹药(箭矢/子弹) | 毒箭矢/银色子弹 |
| DelayConsume | 延迟消耗物品（用于`itemskill`）。使用`itemskill`的物品在选择目标后被消耗。任何其他命令都不会消耗该物品。可用这个特性实现“不会被消耗的苍蝇翅膀” | 物理修改许可证/魔法修改许可证 |
| ShadowGear | 影子装备 | 横冲直撞的暗影盔甲/天空吹影武器 |
| Cash | 另一种延迟消耗物品，需要用户确认后才能使用 | 开发团队宝箱/运营团队宝箱/夏天之夜宝箱 |

## SubType
物品子类型。

武器子类型：
| 类型 | 说明 |
| --- | --- |
| Fist | 拳刃 |
| Dagger | 匕首 |
| 1hSword | 单手剑 |
| 2hSword | 双手剑 |
| 1hSpear | 单手枪 |
| 2hSpear | 双手枪 |
| 1hAxe | 单手斧 |
| 2hAxe | 双手斧 |
| Mace | 镰刀 |
| Staff | 法杖 |
| Bow | 弓 |
| Knuckle | 拳套 |
| Musical | 乐器 |
| Whip | 鞭子 |
| Book | 书 |
| Katar | 卡塔尔 |
| Revolver | 手枪 |
| Rifle | 狙击枪 |
| Gatling | 加特林 |
| Shotgun | 霰弹枪 |
| Grenade | 手榴弹 |
| Huuma | 胡玛 |
| 2hStaff | 双手法杖 |

弹药子类型：
| 类型 | 说明 |
| --- | --- |
| Arrow | 箭矢 |
| Dagger | 短刀 |
| Bullet | 子弹 |
| Shell | 贝壳 |
| Grenade | 手榴弹 |
| Shuriken | 飞镖（手里剑） |
| Kunai | 钉头锤 |
| CannonBall | 炮弹 |
| ThrowWeapon | 投掷武器 |

卡片子类型：
| 类型 | 说明 |
| --- | --- |
| Normal | 普通卡片（默认） |
| Enchant | 附魔卡片 |

## Buy
购买价格。

如果NPC商店在配置时没有指定购买价格，就会使用这里的值。
如果不配置，默认是`Sell`价格的2倍。

## Sell
出售价格。

也就是卖给NPC此物品时玩家能拿到的钱，如果不配置，默认是`Buy`价格的一半。

## Weight
物品重量。

这里填写1的话，表示物品重量是0.1（比如箭矢），这里填写10的话，才表示重量是1。

## Attack
武器的攻击力。

## MagicAttack
武器的魔法攻击力。（复兴后才有）

## Defense
防具的防御力。

## Range
武器的攻击范围。

## Slots
装备的卡槽数量。

## Jobs
可装备的职业。

| 职业 | 说明 |
| --- | --- |
| All | 所有职业 |
| Novice | 初心者 |
| SuperNovice | 超级初心者 |
| Swordman | 剑士   |
| Wizard   | 魔法师 |
| Thief    | 盗贼   |
| Merchant | 商人   |
| Archer   | 弓箭手 |
| Ninja    | 忍者   |
| Acolyte  | 侍僧   |
| Alchemist | 炼金术士 |
| Assassin | 刺客 |
| BardDancer | 吟游诗人/舞者 |
| Blacksmith | 铁匠 |
| Crusader | 十字军 |
| Gunslinger | 枪手 |
| Hunter | 猎人 |
| KagerouOboro | 狂战士/影舞者 |
| Knight | 骑士 |
| Mage | 法师 |
| Monk | 武僧 |
| Priest | 牧师 |
| Rebellion | 反叛者 |
| Rogue | 流氓 |
| Sage | 贤者 |
| SoulLinker | 灵魂链接者 |
| StarGladiator | 星灵斗士 |
| Summoner | 召唤师 |
| Taekwon | 泰坤 |

## Classes
可装备的职业种类（一转/二转等等）。

All         - Applies to all classes.
Normal      - Normal classes (no Baby/Transcendent/Third classes).
Upper       - Transcedent classes (no Transcedent-Third classes).
Baby        - Baby classes (no Third-Baby classes).
Third       - Third classes (no Transcedent-Third or Third-Baby classes).
Third_Upper - Transcedent-Third classes.
Third_Baby  - Third-Baby classes.
Fourth      - Fourth classes.
All_Upper   - All Transcedent classes
All_Baby    - All baby classes
All_Third   - Applies to all Third classes.

| 类型 | 说明 |
| --- | --- |
| All | 所有职业 |
| Normal | 普通职业（不含 `小孩/二转/三转`） |
| Upper | 高级职业（不含 `三转`） |
| Baby | 小孩职业（不含`三转小孩`）|
| Third | 三转职业 |
| Third_Upper | 第三转转职职业 |
| Third_Baby | 第三转转生职业 |
| Fourth | 第四转职业 |
| All_Upper | 所有转职职业 |
| All_Baby | 所有转生职业 |
| All_Third | 所有第三转职业 |