# 分身

## 传送门分身
```
warp/warp2: <map name>,<x>,<y>,<facing>%TAB%duplicate(<label>)%TAB%<NPC Name>%TAB%<spanx>,<spany>
```
传送门分身继承目标位置。

## 商店分身
```
shop/cashshop/itemshop/pointshop/npc: -%TAB%duplicate(<label>)%TAB%<NPC Name>%TAB%<sprite id>
shop/cashshop/itemshop/pointshop/npc: <map name>,<x>,<y>,<facing>%TAB%duplicate(<label>)%TAB%<NPC Name>%TAB%<sprite id>
```

商店分身继承道具列表。

## NPC分身
```
npc: -%TAB%duplicate(<label>)%TAB%<NPC Name>%TAB%<sprite id>,<triggerX>,<triggerY>
npc: <map name>,<x>,<y>,<facing>%TAB%duplicate(<label>)%TAB%<NPC Name>%TAB%<sprite id>,<triggerX>,<triggerY>
```

NPC分身继承脚本代码。

***
其余的配置（名字、位置、朝向、精灵ID、触发区域）使用分身自己的。

说明：
* 库存商店的分身，商品库存是独立的，互不影响
* NPC是共享的，逻辑和数据都共享，比如记录在NPC身上的变量

分身的用处：
* 一份脚本，多处使用，减少数据冗余，方便维护
* 剧情或任务需要，同一个NPC，随着剧情和任务的推进，跟随玩家在不同地方出现

官方脚本大量使用，有1万多处。

甚至可以用来做特效，比如 kvm01.txt （离谱）
