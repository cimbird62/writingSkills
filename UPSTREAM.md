# 技能来源记录

## 编剧技能包

- 来源仓库：[jtydhr88/screenwriting-skills](https://github.com/jtydhr88/screenwriting-skills)
- SSH 地址：`git@github.com:jtydhr88/screenwriting-skills.git`
- 来源提交：`51115f18d160aa8b2ac5813e4432b6f0b425358f`
- 迁入日期：2026-10-03
- 迁入位置：`plugins/screenwriting/`
- 技能数量：26
- 技能与参考文件数量：77

26 个技能目录的文件内容保持与来源提交一致。原插件清单、作者信息、许可证和版权说明一并保留。上游的五种语言 README 位于 `docs/screenwriting/`；文档增加了当前仓库入口，并调整了本地引用路径。

`tools/check-skills.py` 保持上游文件内容，其 MIT 许可证保存在 `tools/LICENSE`。

## 构图技能包

- 来源：个人技能 `imagedraf`
- 迁入日期：2026-10-03
- 迁入位置：`plugins/composition/skills/imagedraf/`
- 技能数量：1
- 文件：`SKILL.md`、`image2 SKILL.md`、`agents/openai.yaml`

三个文件完整迁入，内容保持与迁入时的个人技能一致。`composition` 的 Codex 与 Claude Code 插件清单由当前仓库提供。

## 当前仓库清单

`.agents/plugins/marketplace.json` 和 `.claude-plugin/marketplace.json` 使用市场名称 `writing-skills`，包含 `screenwriting` 与 `composition` 两个插件。
