# 定义
```
<map name>,<x>,<y>,<facing>%TAB%script%TAB%<NPC Name>%TAB%<sprite id>,{<code>}
<map name>,<x>,<y>,<facing>%TAB%script%TAB%<NPC Name>%TAB%<sprite id>,<triggerX>,<triggerY>,{<code>}

地图,X坐标,Y坐标,朝向  script  NPC名字  精灵ID,{代码}
地图,X坐标,Y坐标,朝向  script  NPC名字  精灵ID,触发半径X,触发半径Y,{代码}
```

# 触发
NPC 通过点击它们和/或在它们的触发区域中行走来触发。

# 朝向
```
     0
  1  |  7
   \ | /
2 -------- 6
   / | \
  3  |  5
     4
```

# 精灵ID
* 精灵图片ID
    * 推荐在这里查 https://dotalux.com/ro/npclist/
    * 自己查客户端方法：
        * 用SPR_Conview打开data\sprite\npc目录里的.spr文件
        * 用文本编辑器打开data\luafiles514\lua files\datainfo\JobIdentity.lub文件，搜spr的文件名，找到精灵ID
* 预定义的常量
    * 在代码 src\map\npc.hpp 里，比如：
        * JT_HIDDEN_NPC = 111, 不可见的 NPC，但仍可点击，在制作 3D 地形的可点击对象时很有用。
        * JT_FAKENPC = -1, 不可见且不可点击的NPC，常用于浮动NPC。
        * JT_4_F_JOB_BLACKSMITH = 726, 上节课我们使用过。
    * 常量定义和客户端名是相同的，所以写脚本时也可以直接填对应精灵的文件名的全大写形式。
* 怪物ID
    * https://rockragnarok.com/edda/?module=monster
    * https://ratemyserver.net/index.php?page=mob_db

'-1' Sprite ID 将使 NPC 不可见（且不可点击）。 '111' Sprite ID 将创建一个没有 Sprite 的 NPC，但仍可点击，如果您想制作 3D 地形的可点击对象，这将很有用。

# 触发区域
TriggerX 和 triggerY（如果给定）将定义一个区域，以 NPC 为中心并在 X 的每个方向上跨越 triggerX 单元格，在 Y 的每个方向上跨越 triggerY 单元格。走进该区域将触发 NPC。 如果 NPC 代码中没有 'OnTouch:' 特殊标签，则执行将从脚本的开头开始，否则，将从 'OnTouch:' 标签开始。 怪物也可以触发 NPC，尽管在这种情况下使用标签“OnTouchNPC：”。

# 相关链接
* 官方文档：https://github.com/najoast/rathena_script_commands/blob/master/manual/3.top-level-commands.md#define-an-npc-object
* SPR Conview 工具下载：https://ratemyserver.net/index.php?page=download_tool
* 本视频示例代码：https://github.com/najoast/rathena_tutorial/blob/ba91c92537c3e97c66df4228d7b328f6b4c6bfb2/src/8_npc.ras
