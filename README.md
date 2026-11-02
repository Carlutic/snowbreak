# snowbreak — 尘白禁区 MMD 模型库

配合 [Carlutic/model-viewer](https://github.com/Carlutic/model-viewer) 的 **Snowbreak** 分类使用的模型与清单仓库。
结构对标其它模型仓库（`Snowbreak/` 缩略图目录 + `chars/` + 根目录清单 json），通过 GitHub Pages 对外提供：
网站代码里的 `snowbreakBaseUrl()` 直接指向 `https://carlutic.github.io/snowbreak/`，本地不再保存模型副本。

## 目录结构

```
snowbreak.json          # 角色清单（网站启动时读取）
skins.json              # 皮肤清单（当前为空）
Snowbreak/              # 角色缩略图（对标其它仓库的 Genshin/、HSR/、ZZZ/ 等目录）
    Bubu.png
    Longyan.png
chars/<英文名>/          # PMX 模型 + 贴图 + 作者规则文件
```

## 清单格式（snowbreak.json）

```json
[
    {
        "id": 70001,                    // 首位数字 7 = Snowbreak 分类
        "name": "Bubu",                 // ASCII 名（用于 URL slug：/bubu、查重/查找）
        "displayName": "卜卜-元气愈养",  // 可选，界面上显示的名字（可含中文）
        "weaponType": "",
        "element": "Snowbreak",
        "gender": "Female",
        "region": "",
        "rarity": 5,
        "directory": "chars/Bubu",          // 相对本仓库根目录
        "image": "Snowbreak/Bubu.png",      // 相对本仓库根目录（缩略图放 Snowbreak/）
        "pmx": "卜卜-元气愈养.pmx"           // 相对 directory
    }
]
```

约定：`id` 以 7 开头（保证路由/筛选归到 Snowbreak 分类），`name` 必须是 ASCII（slug 只保留 a-z0-9），中文名放 `displayName`。

## 添加新角色

1. 新建 `chars/<ASCII 名>/`，放入 `.pmx` 与全部贴图（文件名保持 PMX 内引用的原名，含中文也可以）。
2. 在 `snowbreak.json` 里追加上面格式的一条，`id` 顺延，`name` 用 ASCII、`displayName` 放中文全名。
3. 生成 512x512 缩略图放到 `Snowbreak/<ASCII 名>.png`，填到 `image`。
4. 推到 `main` 后等 1~2 分钟 GitHub Pages 重新发布，刷新网站即可（网站直接从 `https://carlutic.github.io/snowbreak/` 读取，不需要本地副本）。

> 当前规模：**86 个条目 + 12 个皮肤**（两批神帝宇模型，覆盖 20+ 名角色/装甲系列），
> 每个 `chars/<ASCII 名>/` 放该文件夹的主 PMX + 全部贴图；同一文件夹里的变体（新版/无裙子版/
> 无外套版/权重裙/裸足/丝袜/变身后形态等）放进 `skins.json`，站点里用左侧工具栏的「衣服」按钮切换。

## 版权与配布规则（重要，必读）

- 模型：**尘白禁区 / 神帝宇**，版权归属 **Seasun Games（COPYRIGHT ©2024）**，来源模之屋（aplaybox）官方账号配布。
- 原配布规则明确：**不允许二次配布**、不允许拆取部件挪用、不允许 18 禁 / 宗教宣传 / 违法用途、**不允许商用**；允许改造与完善物理。
- 因此：本仓库公开托管同样不构成对模型再配布的授权，公开访问/分发存在被作者或平台投诉的风险；若在意授权，请改为私有仓库或仅本地保存。
- 作者规则原文见 `chars/Bubu/README-使用规则.txt`。
