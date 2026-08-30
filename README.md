# intern-project-mining（实习含金量挖掘）

面向计算机专业实习生的 **Codex Skill**。把你公司的真实项目代码交给它，它会帮你梳理项目画像，挖掘出**有含金量、能写进简历、符合实习期真实工作量**的技术向开发需求，并一步步产出：项目画像 → 机会挖掘（需求背景 / 解决方案 / 量化口径 / 简历写法）→ 执行计划 → 复现练习 → 实习经历写法 → 面试预案。

适用场景：你有一个本地项目（或 README / 目录结构摘要），希望把已有代码和可落地的技术改造整理成有条理、经得起面试追问的实习成果。

## 特性

- **项目完整性检查**：读代码前先判断项目是否完整（构建配置、启动类、依赖、测试、缺失项），给出结论与缺口清单
- **技术向机会挖掘（L1 / L2 / L3 分级）**：默认只挖「实习生友好」需求——加缓存、SQL 优化、MQ 生产/消费、定时任务、工具类封装、小型业务模块、Java Agent 探针等；明确排除接口文档、流程规范等无技术含量的事
- **按实习时长校准**：会先问你实习了几个月（已结束的也问），据此限定产出条数与难度，避免「一眼假」
- **需求输出完整**：每条机会都带需求背景、解决方案、技术栈/技术点、面试延伸（八股文考点）、量化数据及口径（数据怎么测的）、简历写法参考，并按统一性价比口径排序
- **复现练习（可选）**：选中需求后可生成练习包，先备份原实现 → 移除该需求代码 → 你独立重写，加深真实掌握
- **简历与面试闭环**：直接输出「项目介绍 + 职责描述 + 工作内容」的实习经历写法，并为每个量化数字准备「数据来源 / 测量方法」说明，配套项目 → 八股文延伸的面试预案

## 目录结构

```text
intern-project-mining/
├── SKILL.md                        # skill 入口：核心原则 + 分阶段工作流
├── agents/
│   └── openai.yaml                 # UI 元数据与调用策略
└── references/
    ├── project-mapping.md              # Stage 0–1：信息收集、完整性检查、项目画像
    ├── opportunity-mining.md           # Stage 2：机会挖掘模板、打分口径、输出格式
    ├── intern-requirement-patterns.md  # 实习生典型需求分级（L1/L2/L3）与适配性检查
    ├── practice-lab.md                 # Stage 3B：复现练习流程（备份/移除/复盘）
    ├── resume-writing.md               # Stage 4：简历定制（项目介绍/职责描述/工作内容/量化口径）
    └── interview-prep.md               # Stage 5：面试预案（Q&A、八股文延伸、量化数据问答）
```

## 安装

需要 Codex（OpenAI 的终端编码代理）。安装后**新开一个对话**即可触发。

### 方式一：复制文件夹（最简单）

把仓库中的 `intern-project-mining/` 文件夹复制到本机 skill 目录：

```bash
# Windows (PowerShell)
Copy-Item -Path .\intern-project-mining -Destination "$HOME\.codex\skills\intern-project-mining" -Recurse

# macOS / Linux
cp -r intern-project-mining "$HOME/.codex/skills/intern-project-mining"
```

### 方式二：git clone

```bash
git clone https://github.com/dream-kaii/intern-project-mining.git
cp -r intern-project-mining/intern-project-mining "$HOME/.codex/skills/intern-project-mining"
```

Windows PowerShell：

```powershell
git clone https://github.com/dream-kaii/intern-project-mining.git
Copy-Item .\intern-project-mining\intern-project-mining "$HOME\.codex\skills\intern-project-mining" -Recurse -Force
```

## 使用方法

新开一个 Codex 对话，直接触发：

```
用 $intern-project-mining 分析这个项目：<项目路径>
```

或等 description 自动匹配（当你提供公司项目代码并希望获得实习亮点 / 简历素材 / 复现练习 / 面试预案时）。

## 工作流程

skill 按阶段引导，每阶段结束给出阶段结果，并提供「确认 / 追问 / 跳过」选项；确认后再进入下一阶段，允许随时回退。

| 阶段 | 内容 |
| --- | --- |
| Stage 0 | 信息收集：项目路径、岗位方向、实习时长（已结束也问几个月）、简历时间线 |
| Stage 1 | 项目完整性检查 + 项目画像（业务、技术栈、架构、数据流、主流技术识别） |
| Stage 2 | 机会挖掘：按实习时长给出适量 L1/L2 技术需求，含背景、方案、量化口径和简历写法，按性价比排序 |
| Stage 3 | 执行计划：需求口径、技术方案与改造点、里程碑、验收标准 |
| Stage 3B | 复现练习（可选）：备份原实现 → 清空代码 → 独立重写 → 复盘 |
| Stage 4 | 简历定制：直接输出项目介绍 + 职责描述 + 工作内容的正常实习经历 |
| Stage 5 | 面试预案：熟悉计划、追问 Q&A、项目 → 八股文延伸、量化数据问答 |

机会数量会随实习时长调整：2 个月以内通常聚焦 1 条核心需求，3–4 个月通常选择 1–2 条，6 个月及以上可加入少量 L2 需求。

## 注意事项

- **保密**：skill 只在本机读取项目代码，不调用外部网络工具；输出不粘贴大段原始代码。不要上传含密钥、内网地址、客户数据的文件；敏感项目先过滤再分析。这些措施只能把泄露面降到最小，无法保证绝对安全。
- **不要直接搬运公司代码**：本 skill 的输出是「分析 + 模板 + 引导」，不会替你生成大段公司代码；请遵守你所在公司的代码保密协议。
- **复现练习会改动项目文件**：Stage 3B 会先备份到项目目录外再移除原实现，动手前确认备份完整、了解恢复方式。

## 开发 / 修改

- 修改 `SKILL.md` 控制工作流与原则，阶段细节在 `references/` 下
- 保持 `name`、`description` 与仓库/触发语一致，新增的参考文件请在 `SKILL.md` 中说明用途
- 改完建议直接复制到本机 `~/.codex/skills/intern-project-mining/` 做一轮真实对话冒烟

## License

MIT
