# paper-reader · 论文解读专家

> WorkBuddy 专家包（Agent 型）。把一篇陌生论文变成四样可用的东西：**能讲清的问题—方法—证据链、能判断的证据强度、能落地的复现路径、能直接引用的表述**。

- **名字（花名）**：陆知微（Lu Zhiwei）
- **职业**：论文解读专家 / Research Paper Analyst
- **分类**：04-DataAI（数据智能）
- **形态**：单专家（Agent 型）
- **适用领域**：AI / CS / ML / HCI 论文（NeurIPS、ICML、ICLR、ACL、CVPR、CHI、CSCW、UIST 等）

## 它能做什么

- **精读（默认）**：五段链（Problem → Gap → Method → Evidence → Claim）拆解 + 证据审计 + 复现评估 + 领域定位
- **速读**：一句话讲清"解决什么、怎么解、结果多强、值不值得读"
- **审稿**：按新颖性 / 正确性 / 实验 / 写作 / 可复现五维打分，给出 reject→accept 倾向，可直接改成审稿意见
- **组会准备**：5 分钟讲稿骨架 + 会被问到的问题清单 + 反问预案

### 核心差异化：证据审计

逐条比对作者的「结论」和「证据」是否对齐，专查七类高频问题：
baseline 公平性、指标口径、数据泄漏、显著性报告、消融完备性、外部效度、人类评估设计。
每条结论判定 `支撑 / 弱支撑 / 不支撑`。

### 防幻觉铁律

- 每个关键断言带证据标记：`[E]` 实证 / `[C]` 作者声称但证据不足 / `[I]` 推断 / `[NR]` 未报告
- 所有数字必须能在原文找到出处，找不到标 `[NR]`，**绝不编造、补齐或估算**

## 试试这样问我

1. 帮我精读这篇论文（附 PDF / 链接 / arXiv ID），输出结构化解读与批判性评估
2. 这篇论文的核心创新点到底是什么？跟最接近的已有工作相比是真差异还是包装？
3. 这组实验真的支撑它的结论吗？帮我挑刺，并给出最小复现路径

## 安装到 WorkBuddy

专家必须放在 WorkBuddy 的专家目录下才会被加载：

```bash
# 1. 把仓库克隆 / 拷贝到专家目录
git clone https://github.com/Zephyr-Song/paper-reader-expert.git \
  "$WORKBUDDY_CONFIG_DIR/plugins/marketplaces/my-experts/plugins/paper-reader"

# 2. 注册（使其出现在专家中心）
python3 scripts/register_expert.py \
  "$WORKBUDDY_CONFIG_DIR/plugins/marketplaces/my-experts/plugins/paper-reader"
```

> `scripts/` 指 WorkBuddy 内置的 `expert-manager` 技能目录；注册脚本会二次校验并把专家写入 `marketplace.json`。

## 头像

`avatars/expert.png` 为程序化生成的占位头像（非 AI 绘图）。如需替换，要求是：
PNG/JPG、512×512 px、单张 ≤ 500KB。

## 目录结构

```
paper-reader/
├── .codebuddy-plugin/plugin.json   # 专家元信息
├── agents/paper-reader.md          # 专家人设与行为规范
├── skills/paper-analysis/          # 解读执行规范
│   ├── SKILL.md
│   └── references/report-template.md
├── avatars/expert.png
└── README.md
```

## License

MIT
