---
title: ㊙️ Font
id: font
---

import UrlCard from '@site/src/components/UrlCard';

:::info

This process is extremely simple and requires no plugin-side configuration. Just follow the tutorial below.

:::

## TTF

<UrlCard
  url="https://minecraft.wiki/w/Font#TTF_provider"
  title="TTF Fonts"
/>

For TTF fonts, you need to create a `default.json` file in the following path. If you already have a `default.json` file, simply append your font JSON to the bottom of the existing JSON file.

<div style={{textAlign: 'center'}}>
  <img src="/img/font_1.png" alt="" />
</div>

```json
{
    "providers": [
        {
            "type": "ttf",
            "file": "minecraft:custom_font.ttf",
            "oversample": 10,
            "size": 11
        }
    ]
}
```

<div style={{textAlign: 'center'}}>
  <img src="/img/font_2.png" alt="" />
</div>

## Bitmap

<UrlCard
  url="https://minecraft.wiki/w/Font#Bitmap_provider"
  title="Bitmap Fonts"
/>

If you wish to replace the vanilla character images, simply place the following PNG files in the specified path as outlined below.

<div style={{textAlign: 'center'}}>
  <img src="/img/font_3.png" alt="" />
</div>

## Unihex

To configure the unihex font in Minecraft, which is relatively less common and rarely used, you can refer to the Minecraft Wiki for detailed instructions.

<UrlCard
  url="https://minecraft.wiki/w/Font#Unihex_provider"
  title="Unihex Fonts"
/>