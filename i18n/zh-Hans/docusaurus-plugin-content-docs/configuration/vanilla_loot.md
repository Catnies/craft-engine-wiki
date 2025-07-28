---
title: 🗃️ Vanilla Loot
id: vanilla_loot
---

## Introduction

Minecraft's native loot system is robust but has one key limitation: it cannot integrate plugin-specific elements like placeholder checks, permissions, or other advanced features. Additionally, configuring vanilla data packs is cumbersome, especially when overriding default loot tables.

To solve this, our plugin provides a vanilla loot system override. Below is a quick-start example (where "..." represents loot configurations). For optimal results, we recommend reviewing [💎 Loot Table](../reference/loot_table.md) first to master loot configuration.

## Block Loots

```yaml
vanilla-loots:
  minecraft:grass_loot:
    type: block
    target: "minecraft:grass"
    # Whether to overwrite the vanilla loots
    override: false
    loot:
      ...
```

```yaml
vanilla-loots:
  minecraft:grass_loot:
    type: block
    target:
      - minecraft:wheat[age=0] # use a precise state
      - minecraft:wheat[age=1]
    override: false
    loot:
      ...
```

## Entity Loots

```yaml
vanilla-loots:
  minecraft:sheep_loot:
    type: entity
    target: "minecraft:sheep"
    # Whether to overwrite the vanilla loots
    override: false
    loot:
      ...
```
