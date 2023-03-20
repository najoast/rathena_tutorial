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
