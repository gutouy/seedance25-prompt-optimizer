# Seedance 2.5 Prompt Optimizer — Codex Skill

一个面向 Codex 的 Seedance 2.5 视频提示词优化 Skill。

它可以把一句简单、口语化的视频创意，扩写成结构清晰、细节充分、可直接用于 Seedance 2.5 的成品提示词；并根据任务自动切换到多素材、长视频、视频编辑、视频延长、首尾帧、多关键帧、宫格分镜、白模、一键成片和无缝转场等结构。

## 主要能力

- 保留用户的主体、数量、剧情、风格、镜头、声音和参考素材职责等硬约束。
- 自动补充与视频相关的低风险细节，而不是单纯堆砌形容词。
- 自动补全动作过程、结束状态、场景动态、光线与材质、镜头路径、环境声和连续性。
- 将“紧张、孤独、温馨”等抽象情绪转化为可观察的表情、视线、呼吸和肢体表现。
- 自动识别并路由不同任务类型，复杂任务使用对应模板。
- 对多素材任务明确 `@图片 / @视频 / @音频` 的职责，降低人物、道具和场景串位。
- 对长视频按“阶段 + 结束状态”组织事件，减少剧情遗漏和状态漂移。
- 对视频编辑明确唯一母版、编辑范围、保持内容和时间线继承。
- 对视频延长、关键帧和无缝转场加强边界画面、运动趋势和声音连续性。
- 内置能力边界检查，不承诺帧级剪辑、逐像素一致或生成文字 100% 精确。

## 支持的任务类型

1. 普通文生视频
2. 多图片 / 视频 / 音频参考
3. 30 秒或多阶段长视频
4. 视频编辑
5. 视频向前 / 向后延长
6. 首帧 / 首尾帧生成
7. 多关键帧顺序控制
8. 宫格分镜 / Storyboard
9. 粗粒度白模参考
10. 细粒度白模重渲染
11. 一键成片
12. 两段视频无缝转场

## 目录结构

```text
seedance25-prompt-optimizer/
├── SKILL.md
├── README.md
├── LICENSE
├── .gitignore
├── agents/
│   └── openai.yaml
└── references/
    ├── core-rules.md
    ├── task-templates.md
    └── examples.md
```

## 安装

### Codex 全局安装

macOS / Linux：

```bash
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/gutouy/seedance25-prompt-optimizer.git \
  "$HOME/.agents/skills/seedance25-prompt-optimizer"
```

Windows PowerShell：

```powershell
New-Item -ItemType Directory -Force "$HOME\.agents\skills" | Out-Null
git clone https://github.com/gutouy/seedance25-prompt-optimizer.git "$HOME\.agents\skills\seedance25-prompt-optimizer"
```

### 项目级安装

如果只希望某个项目使用该 Skill，将仓库放到项目的 `.agents/skills` 目录：

```bash
git clone https://github.com/gutouy/seedance25-prompt-optimizer.git \
  .agents/skills/seedance25-prompt-optimizer
```

## 使用

可以显式调用：

```text
$seedance25-prompt-optimizer
```

例如：

```text
$seedance25-prompt-optimizer
一只白色狐狸站在雪山山脊上，回头看镜头，很孤独，电影感。
```

也可以直接自然语言请求：

```text
帮我把这个简单创意优化成 Seedance 2.5 可以直接使用的详细视频提示词：
一辆红色跑车在雨夜穿过霓虹城市街道，速度感强。
```

该 Skill 会优先保留用户明确要求，再补充真正影响视频生成的动作、镜头、光线、声音、情绪表现和连续性约束。

## 设计原则

### 1. 不是“越长越好”

新增细节至少应解决一个实际问题：主体更明确、动作更可执行、场景更可信、光线材质更清晰、镜头更明确、声音更匹配、情绪更可观察、前后状态更连续，或参考素材更不容易串位。

### 2. 自动补细节，但不过度编造

默认可以补充低风险的动作过程、环境动态、光影反应、镜头路径、环境声和连续性；不会擅自创造品牌、关键对白、精确字幕、人物身份、产品参数或改变故事主体。

### 3. 复杂任务先路由，再扩写

多素材、长视频、编辑、延长、关键帧、白模和转场不会强行套用普通文生视频模板，而是先识别任务类型，再加载相应规则。

## 示例

更多完整输入 / 输出示例见：

```text
references/examples.md
```

## 贡献

欢迎提交 Issue 或 Pull Request，包括：

- 新的 Seedance 2.5 提示词任务模板
- 更稳定的镜头、动作或连续性写法
- 失败案例和修正规则
- 中英文示例
- Codex Skill 兼容性改进

提交改动时，请尽量保持规则“可执行、可观察、低歧义”，避免仅增加修饰词。

## 免责声明

本项目是非官方社区工具，与字节跳动、即梦或 Seedance 官方不存在隶属或授权关系。模型能力、产品参数和平台行为可能发生变化，请以相关产品的最新官方说明为准。

本仓库不包含或重新发布原始提示词指南全文；Skill 中的规则经过重新组织和工程化，用于提示词优化工作流。

## License

MIT License。详见 [`LICENSE`](./LICENSE)。
