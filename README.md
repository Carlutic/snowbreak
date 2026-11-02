# snowbreak — 尘白禁区 MMD 模型库

配合 [Carlutic/model-viewer](https://github.com/Carlutic/model-viewer) 的 **Snowbreak** 分类使用的模型与清单仓库。
目录结构与网站端的 `res/snowbreak/` 完全一致：本地开发时把这些文件放进 `model-viewer/res/snowbreak/`；
线上部署时把本仓库发布到 GitHub Pages / 对象存储，并让 `src/config.ts` 里的 `snowbreakBaseUrl()` 指向它即可。

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
        "name": "Bubu",                 // 英文名（用于 URL slug：/bubu）
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

约定：`id` 以 7 开头（保证路由/筛选归到 Snowbreak 分类），`name` 用英文（slug 生成只保留 a-z0-9）。

## 添加新角色

1. 新建 `chars/<英文名>/`，放入 `.pmx` 与全部贴图（文件名保持 PMX 内引用的原名，含中文也可以）。
2. 在 `snowbreak.json` 里追加上面格式的一条，`id` 用 70002、70003……
3. 生成 512x512 缩略图放到 `Snowbreak/<英文名>.png`，填到 `image`。
4. 本地把整个目录同步到 `model-viewer/res/snowbreak/` 后刷新网站即可（dev server 会自动拷贝新文件）。

## 版权与配布规则（重要，必读）

- 模型：**尘白禁区 / 神帝宇**，版权归属 **Seasun Games（COPYRIGHT ©2024）**，来源模之屋（aplaybox）官方账号配布。
- 原配布规则明确：**不允许二次配布**、不允许拆取部件挪用、不允许 18 禁 / 宗教宣传 / 违法用途、**不允许商用**；允许改造与完善物理。
- 因此：本仓库即使公开，也不构成对模型再配布的授权。**建议把本仓库设为私有，或仅本地保存**；若公开托管，风险自负，且可能被作者/平台投诉下架。
- 作者规则原文见 `chars/Bubu/README-使用规则.txt`。
