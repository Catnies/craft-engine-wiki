---
title: 🥪 Stackable Block
id: stackable_block
---

| Property Name | Property Type | Required |
|---------|---------|---------|
| CUSTOM    | int   | yes   |

**Stackable Block** allows you to use a specified item to stack this block, transforming it into a form with a larger quantity.

```yml
blocks:
  default:pebble:
    behavior:
      type: stackable_block
      property: pebble  # the name of the property for amount
      items:
        - default:pebble
      sounds:
        stack: minecraft:block.stone.fall
```

![](/img/stackable_block.png)