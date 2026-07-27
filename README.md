# Mock Interview

一个**先上网查这家公司真实面试题**、然后**会追问**的 AI 面试官。

不是从固定题库里抽题——你说要面 BCG，它去把 BCG 官网的 practice case 和候选人回忆帖翻一遍，弄清楚这一轮到底考什么，再开始问。case、product sense、metric 诊断、技术题，不是只有 behavioral。

[English](#english) · [快速开始](#快速开始) · [它和别的有什么不一样](#它和别的有什么不一样)

<!-- 录一个 30 秒的 GIF 放这里：它联网找真题 → 提问 → 追问 → 报告。这是决定别人会不会 star 的一屏。 -->
<!-- ![demo](docs/demo.gif) -->

---

## 它和别的有什么不一样

市面上的 AI 模拟面试基本都是同一个毛病：一口气甩你二十道通用题，你答什么它都说"很好的回答！"，然后结束。

而真实面试根本不长这样。**麦肯锡一面是 case 不是聊天**，Amazon 每道题都对着一条 Leadership Principle 打分，PM 有一整轮就问"这个指标掉了 20%，你怎么办"。三件事都不一样，用同一套通用题去练，等于没练。

所以这个 skill 做三件事：

**1. 先查这一轮到底考什么**

拿到公司和岗位后，它会去搜这家公司的真实面试流程和被报告过的题目——公司官网的招聘页、候选人回忆帖、以及 MBB 自己公开发布的 practice case。开始之前它会告诉你查到了什么："你这一轮是一个 behavioral + 一个面试官主导的 case，我按这个配比来。"

查不到就直说，退回内置题库。它不会编一个听起来很像的流程糊弄你。

**2. 一次一题，而且会追问**

不提前剧透，不中途给提示。回答含糊、把团队功劳说成自己的、没有结果和数字——它会追着问。大约一半的回答会被追问，这个比例是照着真实面试来的。

追问才是大多数人当场崩掉的地方，也是练习时最容易被跳过的地方。

**3. 打分不放水**

3 分 = 真实面试中的平均水平，不是差。给所有人打 4 分的反馈等于没有反馈。

---

## 覆盖的题型

| 类型 | 内容 |
|---|---|
| **Case（咨询）** | 完整 case 协议，区分麦肯锡式（面试官主导）和 BCG/Bain 式（候选人主导）。内置两个带完整数据表的 case，数据要你开口问才给，算错了会被追。 |
| **Product sense** | 你没说清用户和问题就直接给方案，它会当场打断——这是 PM 面最常见的死法。 |
| **Metric 诊断** | 指标掉了 18%，逐层给你数据，看你是先做维度拆分还是上来就猜原因。 |
| **Estimation** | 市场估算，不看数字对不对，看拆解和有没有 sanity check。 |
| **技术 / 金融** | 系统设计、三张报表、DCF、以及"用大白话解释你简历上这个东西"——最见真章的一道题。 |
| **Behavioral** | STAR，带追问阶梯（含 Amazon LP 映射）。 |

不做实时 coding——那需要编辑器和编译器，模拟出来只会给你虚假的信心。

---

## 快速开始

**1. 下载**

```bash
git clone https://github.com/ameliapeng-gif/real-mock-interview-agent.git
```

不用命令行的话，点页面右上角绿色 `Code` → `Download ZIP`，解压即可。

**2. 装进 MiniMax Code**

把 `mock-interview` 整个文件夹导入 MCode 的 skills 目录（设置 → Skills）。

> 这个 skill 依赖两个能力：**联网查真题**（浏览器 Agent）和**语音提问**（TTS）。任何支持 SKILL.md 且能联网的 Agent 都能跑核心流程，但语音部分调的是 MiniMax 的接口。

**3. 开始**

```
用我这份简历，模拟一轮 BCG 的暑期实习面试
```

把简历拖进去，说清楚公司和岗位。它会先去查，然后问你要几道题、要不要语音。

---

## 语音面试

文字练习会藏住你的问题——你在键盘上不会说"嗯…这个…"。开语音会诚实很多。

完整闭环是：**它出声问 → 你出声答 → 它转写并按你实际说出口的内容打分。**

```bash
cp .env.example .env
```

在 `.env` 里填 MiniMax API key（[国内](https://platform.minimaxi.com/) · [海外](https://platform.minimax.io/)）。

回答有两种方式：

- **系统听写**（默认，零配置）：Mac 连按两下 Fn，手机按键盘上的话筒，说完文字就进对话框了
- **录音**（信号更好）：`python scripts/record.py`，回车结束。有音频才能分析你的语速、口头禅和最长的一次卡壳——这几项在文字里完全看不出来，而且往往是最扎心的

没配 key 也能用，自动退回文字模式。

---

## 隐私

- 你的简历和回答会作为对话内容发给你正在用的模型，和你平时直接粘贴给它是一样的。这个仓库不收集、不上传、不存储任何东西。
- `.env` 已经在 `.gitignore` 里。**如果你 fork 了这个仓库，提交前请再确认一次 API key 没有被 commit 进去**——key 泄露到 GitHub 会在几分钟内被爬走。
- 仓库里的示例简历是虚构的。

---

## 参与

最欢迎这三类 PR：**更多行业的真实题**、**更狠的追问**、**各家公司面试风格的修正**。你刚面完记得回来补一笔，这个仓库的价值全在这儿。

---

## English

An AI interviewer that **researches the actual loop first**, then **actually follows
up**.

It doesn't pull from a static question list. Tell it you're interviewing at BCG and
it goes and reads BCG's own published practice cases and candidate write-ups, works
out what this round actually tests, and builds from that. Cases, product sense,
metric diagnostics, technicals — not just behavioral.

**What's different:**

- **It researches first.** Company careers pages, candidate reports, and the practice
  cases MBB firms publish themselves. It tells you what it found before starting —
  "your loop is one behavioral round and one interviewer-led case." If it can't find
  anything, it says so instead of inventing a plausible-sounding process.
- **One question at a time, and it probes.** Vague answers, team credit taken as
  personal credit, results with no numbers — all draw a follow-up. Roughly half of
  answers do, which is what makes it feel real.
- **It scores honestly.** 3 out of 5 is an average real candidate. Feedback that
  scores everyone a 4 is worthless.

**Coverage:** consulting cases with full protocol and data exhibits (interviewer-led
vs candidate-led), product sense, metric diagnostics, estimation, system design,
finance technicals, and behavioral with follow-up ladders. No live coding — that
needs a real editor, and simulating it builds false confidence.

**Debrief:** per-question scores, what was missing, and a rewritten answer built only
from material you actually gave it. Missing numbers are marked `[your number here]`
rather than invented — a fabricated metric is how people get caught.

**Install:** clone, drop the folder into your agent's skills directory, then say
*"run a mock BCG summer analyst interview using my resume."* Voice mode needs a
MiniMax API key in `.env`; without one it falls back to text.

**Privacy:** your resume goes to whichever model you're already using, same as
pasting it in a chat. Nothing is collected by this repo. `.env` is gitignored —
double-check before you commit if you fork.

---

## License

MIT — 拿去随便用，改了也不用告诉我。

<!-- 如果这个项目是在品牌合作中做的，在这里加一行 disclosure，比如：
Built while testing MiniMax Code. Opinions are my own. -->
