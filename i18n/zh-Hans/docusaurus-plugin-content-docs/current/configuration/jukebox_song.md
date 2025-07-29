---
title: 💽 Jukebox Song
id: jukebox_song
---

:::caution

Due to the fact that Minecraft's registry becomes immutable once registered, you will need to restart the server in order to apply any new modifications. However, you can register a new song in real-time by modifying the configuration ID.

:::

```yaml
jukebox-songs:
  default:credits_music:
    sound: minecraft:music.credits
    length: 100.0  # music length in seconds
    description: "Credits"  
    comparator-output: 15
    range: 32
```

Just add the `minecraft:jukebox_playable` component, and your item becomes a playable music disc

```yaml
items:
  default:music_stick:
    material: stick
    data:
      jukebox-playable: default:credits_music
```

If you don't know how to customize a sound, please refer to [this page](sound.md).