# Rime 配置（鼠须管）

基于[雾凇拼音](https://github.com/iDvel/rime-ice)的个人配置，运行于 macOS 鼠须管（Squirrel）。

## 方案

- **rime_ice**（雾凇拼音，全拼）—— 主方案
- **melt_eng** —— 英文输入，作为次翻译器挂载，支持中英混输
- **radical_pinyin** —— 部件拆字反查（`uU` 前缀）

## 安装

本仓库即 Rime 用户目录，`~/Library/Rime` 软链到此：

```bash
ln -s ~/Developer/GitHub/Rime ~/Library/Rime
```

## 更新

通过 [plum](https://github.com/rime/plum)（东风破）更新：

```bash
# 日常更新词库（只动 cn_dicts/en_dicts/opencc，不覆盖 schema/dict，推荐）
bash rime-install iDvel/rime-ice:others/recipes/all_dicts

# rime-ice 版本升级（覆盖所有上游文件，升级后需检查自定义是否受影响）
bash rime-install iDvel/rime-ice:others/recipes/full
```

## 自定义

上游文件由 plum 管理，**不要手改**：`rime_ice.schema.yaml`、`rime_ice.dict.yaml`、`cn_dicts/`、`en_dicts/`、`lua/`、`opencc/`、`symbols*`、`melt_eng.*`、`radical_pinyin.*`

自定义收敛在补丁文件，plum 不会覆盖：

| 文件 | 用途 |
|---|---|
| `default.custom.yaml` | 全局配置（候选菜单、方案开关、标点、快捷键） |
| `rime_ice.custom.yaml` | 方案定制（模糊音、en_spacer、自定义短语） |
| `squirrel.custom.yaml` | 外观主题、各应用的 `ascii_mode` |
| `rime_custom_phrase.txt` | 自定义短语（设备名、邮箱、常用英文词） |

当前自定义项：

- 模糊音：`zh/z`、`ch/c`、`sh/s`、`eng/en`、`in/ing`
- `en_spacer`：连续输入英文时自动补空格
- `fold_options: false`：单方案直接展开方案选单
- 词库同步目录：iCloud `RimeSync/`
