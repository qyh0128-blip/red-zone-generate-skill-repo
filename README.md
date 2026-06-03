# Codex Skill: 红区生成

This repository contains the Codex skill `red-zone`.

## Skill

- Display name: 红区生成
- Internal name: `red-zone`
- Path: `skills/red-zone`

## Install From GitHub

Install the latest skill with:

```text
Install the skill from:
https://github.com/qyh0128-blip/red-zone-generate-skill-repo/tree/main/skills/red-zone
```

Then restart Codex so the new skill list is refreshed.

## What This Skill Does

- Replaces red marked areas in reference images.
- Default asset mode outputs a red-area replacement result and a matching white-background 1:1 icon/asset.
- Main KV mode outputs a red-area replacement result and a matching 1:1 KV source image intended for 1500 x 1500 use.

## Usage

Ask Codex:

```text
使用 $red-zone，在参考图红色区域生成蛋糕 icon
```

For H5 header or hero visuals:

```text
使用 $red-zone，生成 H5 主KV，主题是春节红包活动
```
