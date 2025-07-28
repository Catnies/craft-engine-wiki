---
title: 🪹 Compostable Item
id: compostable_item
---

Make non-compostable items compostable

```yaml
items:
  default:ender_pearl_flower_seeds:
    behavior:
      type: compostable_item
      chance: 0.5
```

![](/img/compostable_item_1.png)

:::caution

This doesn’t work with hoppers. Minecraft’s composting system is hardcoded—so only items that are naturally compostable will work properly in hoppers.

But don’t worry! You can still use a compostable item as the base material and tweak the compost chance using [⚙️ Item Settings](../settings.md).

:::