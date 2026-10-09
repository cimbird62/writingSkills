# writingSkills

编剧、画面构图与人物塑造技能库，供 Codex 和 Claude Code 使用。目前包含 **28 个技能**：26 个编剧技能、美学构图技能 `imagedraf`，以及按人物塑造课件整理的 `character-shaping`。

## 技能包

| 技能包 | 数量 | 内容 | 目录 |
|---|---:|---|---|
| screenwriting | 26 | 故事结构、人物冲突、对白、场景、剧集、戏曲、案例与行业实务 | [plugins/screenwriting/skills](plugins/screenwriting/skills) |
| composition | 1 | 构图、镜头、光影、色彩、材质、氛围与中文图像/视频提示词 | [plugins/composition/skills](plugins/composition/skills) |
| character | 1 | 人物小传、行动细节、反差、留白、八项塑造技巧与情绪场景 | [plugins/character/skills](plugins/character/skills) |

编剧技能的参考资料和术语表完整保留。构图技能包含 `SKILL.md`、`image2 SKILL.md` 和 `agents/openai.yaml`。

人物塑造技能依据《从“符号”到“人”：让人物被记住》整理，配有课程页码与案例参考、可选的 15 秒短片及手机拍摄指导。已有的 `sw-character-conflict` 提供上游编剧理论，`character-shaping` 提供这份课件的具体塑造方法。

## 安装

先通过 SSH 克隆仓库：

```bash
git clone git@github.com:cimbird62/writingSkills.git
cd writingSkills
```

### Codex 个人技能

在仓库目录执行，将全部 28 个技能加入个人技能目录：

```bash
mkdir -p ~/.codex/skills
cp -Rn plugins/screenwriting/skills/. ~/.codex/skills/
cp -Rn plugins/composition/skills/. ~/.codex/skills/
cp -Rn plugins/character/skills/. ~/.codex/skills/
```

`-n` 保留已有同名文件。需要升级已安装版本时，请先备份再替换对应技能目录。

### Codex 项目技能

将变量替换为需要使用技能的项目路径，然后在本仓库目录执行：

```bash
WRITING_SKILLS_PROJECT=/absolute/path/to/your-project
mkdir -p "$WRITING_SKILLS_PROJECT/.agents/skills"
cp -Rn plugins/screenwriting/skills/. "$WRITING_SKILLS_PROJECT/.agents/skills/"
cp -Rn plugins/composition/skills/. "$WRITING_SKILLS_PROJECT/.agents/skills/"
cp -Rn plugins/character/skills/. "$WRITING_SKILLS_PROJECT/.agents/skills/"
```

### Claude Code 个人技能

```bash
mkdir -p ~/.claude/skills
cp -Rn plugins/screenwriting/skills/. ~/.claude/skills/
cp -Rn plugins/composition/skills/. ~/.claude/skills/
cp -Rn plugins/character/skills/. ~/.claude/skills/
```

仓库还包含 Codex 和 Claude Code 的插件市场清单，分别位于 `.agents/plugins/marketplace.json` 和 `.claude-plugin/marketplace.json`。两个清单均提供 `screenwriting`、`composition` 和 `character` 插件。

## 调用示例

在 Codex 中用技能名显式调用：

```text
$sw-workflow 帮我建立一个编剧项目，整理阶段目标与进度。
$sw-story-structure 把这个故事梗概整理成完整的节拍表。
$sw-dialogue 修改这场戏的对白，增强潜台词和人物差异。
$sw-series-engine-bible 把这个创意发展成剧集设计和剧集圣经。
$imagedraf 优化这个镜头的构图、光影和材质，输出中文生成提示词。
$character-shaping 按我们的课件塑造这个人物，用行动、反差和留白让他被记住。
```

编剧技能按照提问语言作答。`imagedraf` 默认输出可直接使用的中文图像或视频提示词。

## 全部技能

| 技能 | 用途 |
|---|---|
| `sw-workflow` | 编剧项目调度、进度与 story bible |
| `sw-story-structure` | 故事结构与节拍 |
| `sw-premise-theme` | 前提、主题与一句话故事 |
| `sw-character-conflict` | 人物、动机与冲突 |
| `sw-dialogue` | 对白与潜台词 |
| `sw-scene-craft` | 场景、段落、细节与道具 |
| `sw-format-adaptation` | 剧本格式、写作流程与改编 |
| `sw-truby-anatomy` | 特鲁比有机故事结构 |
| `sw-genre-anatomy` | 类型节拍与混合类型 |
| `sw-series-structure` | 单集与季度结构 |
| `sw-series-engine-bible` | 剧集引擎与剧集圣经 |
| `sw-writers-room` | 编剧室与制作流程 |
| `sw-sitcom-comedy` | 半小时喜剧与笑点设计 |
| `sw-chinese-opera-banqiang` | 板腔体戏曲写作 |
| `sw-chinese-opera-banqiang-cases` | 板腔体全本案例 |
| `sw-chinese-opera-qupai` | 曲牌体戏曲写作 |
| `sw-chinese-opera-qupai-cases` | 曲牌体全本案例 |
| `sw-american-case-studies` | 美国电影剧作案例 |
| `sw-japanese-screenwriting` | 日本编剧方法 |
| `sw-korean-french-screenwriting` | 韩国与法国编剧方法 |
| `sw-chinese-series-practice` | 国产剧创作与制片流程 |
| `sw-industry-business` | 编剧行业、提案与商业实务 |
| `chekhov-dramaturgy` | 契诃夫戏剧方法 |
| `ozu-screenplay-style` | 小津安二郎剧本方法 |
| `succession-series-writing` | 《继承之战》群像剧方法 |
| `sw-series-case-studies` | 剧集案例库 |
| `imagedraf` | 美学构图与图像/视频提示词导演 |
| `character-shaping` | 按课件塑造鲜活人物，设计行为细节、反差、留白与情绪场景 |

## 检查与来源

```bash
python3 tools/check-skills.py --strict
```

检查脚本遍历三个技能包，验证技能名称、描述长度和技能目录下的 Markdown 引用路径。

编剧技能来自 [jtydhr88/screenwriting-skills](https://github.com/jtydhr88/screenwriting-skills)，其 [MIT 许可证](plugins/screenwriting/LICENSE)、[版权说明](plugins/screenwriting/NOTICE) 和原作者信息均已保留。检查脚本的许可证位于 [tools/LICENSE](tools/LICENSE)。构图技能来自个人技能目录 `imagedraf`，本次迁入保留原有文件内容，未增加授权声明。

人物塑造技能来自用户指定的 18 页课件，其 [课程参考](plugins/character/skills/character-shaping/reference.md) 保留页码、方法归纳与案例边界。仓库收录整理后的技能与参考文字，原 PDF 未入库；未推定课件作者或额外授权。

完整编剧说明与来源书目见 [上游中文文档](docs/screenwriting/README_ZH.md)。迁入版本记录见 [UPSTREAM.md](UPSTREAM.md)。
