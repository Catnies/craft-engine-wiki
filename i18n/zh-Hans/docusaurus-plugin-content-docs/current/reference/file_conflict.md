---
title: ⚔️ 文件冲突
id: file_conflict
---

## 简介

在合并多个资源包时，我们经常会遇到文件冲突，例如 pack.png、sounds.json 等。将它们手动配置到单个文件中会非常繁琐。因此，插件提供了一个冲突处理器，让你能自定义解决冲突的方案。当插件检测到冲突文件时，它会查找第一个符合条件的解决方案。如果没有找到合适的解决方案，插件将在控制台向用户发出警告。

:::info
冲突处理器的配置位于 `config.yml` 文件中的 `resource-pack.duplicated-files-handler` 部分。
:::

:::warning
本插件不支持着色器的合并，因为这被认为是不稳定的功能。
:::

```yaml
duplicated-files-handler:
  # 解决物品模型冲突
  - term:
      type: any_of
      terms:
        - type: parent_path_suffix
          suffix: "minecraft/items" # 1.21.4+
        - type: parent_path_suffix
          suffix: "minecraft/models/item" # 1.20-1.21.3
    resolution:
      type: merge_json
      deeply: true
  # 解决 pack.mcmeta 冲突
  - term:
      type: exact
      path: "pack.mcmeta"
    resolution:
      type: merge_pack_mcmeta
      description: "<gray>CraftEngine资源包"
  # 解决 pack.png 冲突
  - term:
      type: exact
      path: "pack.png"
    resolution:
      type: retain_matching
      term:
        type: contains
        path: "resources/default/resourcepack"
  # 解决 sounds.json 冲突
  - term:
      type: filename
      name: "sounds.json"
    resolution:
      type: merge_json
      deeply: false
```

:::tip
你可以简单理解为：**term** 决定了文件如何被识别为冲突，而 **resolution** 则决定了如何处理这些冲突文件。以下是一些可用的匹配方法和解决方案：
:::

## 匹配规则

### 与

所有条件都必须满足。

```yaml
type: all_of
terms:
  - type: xxx1
    aaa: bbb
  - type: xxx2
    ccc: ddd
```

### 或

满足任意条件即可。

```yaml
type: any_of
terms:
  - type: xxx1
    aaa: bbb
  - type: xxx2
    ccc: ddd
```

### 非

对当前条件的结果值。

```yaml
type: inverted
term:
  type: xxx
```

### 文件名匹配

匹配文件名

```yaml
type: filename
name: "sounds.json"
```

### 绝对路径匹配

匹配以 assets 文件夹同级目录为根目录的绝对路径

```yaml
type: exact
path: "assets/minecraft/lang/zh_cn.json"

type: exact
path: "pack.mcmeta"
```

### 父目录路径前后缀匹配

检测路径是否具有特定的前缀或后缀

```yaml
type: parent_path_prefix 
path: "assets/minecraft"

type: parent_path_suffix
path: "minecraft/models/item"
```

### 包含匹配

检查路径是否包含特定字符

```yaml
type: contains
path: "custom/furniture"
```

### 正则匹配

使用正则表达式匹配路径

```yaml
type: pattern
pattern: "此处使用正则表达式"
```

## 冲突解决方案

### JSON合并

将两个 JSON 文件合并为一个

```yaml
type: merge_json
deeply: true
```

### 保留匹配

当两个文件冲突时，保留满足指定条件的文件。

```yaml
type: retain_matching
term:
  type: contains
  path: "resources/default/resourcepack"
```

### 条件解析

执行条件解析

```yaml
type: conditional
term:
  type: xxx
resolution:
  type: xxx
```

### 合并资源包元文件

为 `pack.mcmeta` 定制的特殊解决方案

```yaml
type: "merge_pack_mcmeta"
description: "<gray>CraftEngine资源包" # 资源包描述
```

### 合并纹理图集文件

为 `atlases/xx.json` 定制的特殊解决方案

```yaml
type: "merge_atlas"
```