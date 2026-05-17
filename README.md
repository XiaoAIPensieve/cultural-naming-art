# cultural-naming-art
Transform a foreign name and identity into a Chinese cultural masterpiece
# 🀄 Cultural Naming & AI Art Creation

### Transform a Foreign Identity into a Chinese Cultural Masterpiece

[![License](https://img.shields.io/github/license/XiaoAIPensieve/cultural-naming-art?style=flat-square&color=success)](LICENSE)
[![Version](https://img.shields.io/github/v/tag/XiaoAIPensieve/cultural-naming-art?style=flat-square&color=blue)](https://github.com/XiaoAIPensieve/cultural-naming-art/releases)
[![Python](https://img.shields.io/badge/python-3.10%2B-blue?style=flat-square)](https://python.org)
[![OpenClaw](https://img.shields.io/badge/OpenClaw-Compatible-ff6b35?style=flat-square)](https://clawhub.ai)
[![Models](https://img.shields.io/badge/Models-GPT--4o%20%7C%20Claude--3.5-sonnet-purple?style=flat-square)]()

> Give any foreign tourist a **complete Chinese cultural identity** — in one conversation.
> Names, poems, seals, landscapes, and portraits, all powered by AI.
**Made with 墨 (ink) and ❤️ by [XiaoAIPensieve](https://github.com/XiaoAIPensieve)**

*"每一个名字，都是一首诗的开始。"*
*"Every name is the beginning of a poem."*
---

## ✨ What It Does

```
Your Name  ──►  明远 (Míng Yuǎn)  "Brilliant and Far-reaching"
                    │
                    ├── 📜 七言绝句 — Tang-style 4-line poem with your name
                    ├── 📜 七言律诗 — 8-line regulated verse with antithetical couplets
                    ├── 🔴 篆刻印章 — Traditional seal carving art (DALL·E 3 ready)
                    ├── 🏔️ 水墨山水 — Ink-wash landscape painting inspired by your poem
                    └── 👤 古风人物 — Ancient portrait avatar in dynasty aesthetic
```

---

## 🎯 6 Creative Modules

### 1. 🀄 Chinese Name Generation
**Semantic-Phonetic Fusion Algorithm**

- Maps your original syllables → beautiful Chinese characters
- Enriches meaning with your chosen theme: Nature · Strength · Wisdom · Beauty · Freedom · Passion
- Outputs **3 curated options**, each with etymology, literary reference & vibe tags
- 200+ taboo character filter for cultural safety

### 2. 📜 Classical Poetry — 七言绝句 (Jueju)
**4-line, 28-character Tang masterpiece**

```
明远凌云志四方，     Míng Yuǎn líng yún zhì sì fāng
千山万水路悠长。     Qiān shān wàn shuǐ lù yōu cháng
一声长啸惊飞鸟，     Yī shēng cháng xiào jīng fēi niǎo
万里江湖任翱翔。     Wàn lǐ jiānghú rèn áo xiáng

Translation:
Ming Yuan soars with ambitions spanning all directions,
Through ten thousand mountains and endless waters he travels far.
A single long cry startles the birds to flight —
Ten thousand li of rivers and lakes, his to roam.
```

### 3. 📜 Classical Poetry — 七言律诗 (Lüshi)
**8-line, 56-character regulated verse with 对仗联 (antithetical couplets)**

```
Lines 3–4 couplet:
  碧水东流千里远  ↔  青山北望万年高
  Blue waters flowing east, a thousand li distant  ↔
  Green mountains gazing north, ten thousand years high
```

### 4. 🔴 Seal Carving Art (篆刻印章)
**Museum-quality seal prompts for DALL·E 3 / Stable Diffusion XL**

| Characters | Layout | Style |
|---|---|---|
| 1 char | Centered | 阳刻 (white on red) |
| 2 chars | Vertical | 阴刻 (red on white) |
| 3 chars | 品字形 | 阳刻 |
| 4 chars | 2×2 grid | 朱白相间 |

- Soapstone material · 小篆 script · cinnabar vermillion ink
- Xuan paper texture · authentic ink bleed · scholarly desk context

### 5. 🏔️ Shanshui Landscape (水墨山水)
**Ink-wash paintings in 4 dynasty styles**

| Dynasty | Style | Masters |
|---|---|---|
| **Song** (宋) | Monumental, misty, contemplative | Fan Kuan, Guo Xi |
| **Tang** (唐) | Warm atmospheric color washes | Wang Wei |
| **Ming** (明) | Dramatic Zhe School cliffs | Dai Jin |
| **Modern** (现代) | Zen minimalism · maximum 留白 | Qi Baishi |

- Poem's first line as atmospheric anchor
- Red seal stamp with your name
- Vertical calligraphy inscription
- 2:3 vertical hanging scroll format

### 6. 👤 Ancient Portrait Avatar (古风人物头像)
**Dynasty aesthetics by theme**

| Theme | Dynasty | Costume |
|---|---|---|
| Nature | Song 文人 | Scholar robes, bamboo hat, ink brush |
| Strength | Tang 将军 | Phoenix armor, crimson cape, sword |
| Wisdom | Song 儒士 | Ancient scrolls, scholar's rock |
| Beauty | Tang 才女 | Phoenix hairpin, peonies, court dress |
| Freedom | Ming 侠客 | Travel cloak, bamboo hat, sword |
| Passion | Tang 乐人 | Pipa instrument, expressive gesture |

---

## 🚀 Quick Start

### Python SDK

```bash
pip install openai anthropic
```

```python
from skill import CulturalNamingSkill, Gender, Theme

skill = CulturalNamingSkill()

# Step 1: Generate 3 Chinese name options
names = skill.generate_names(
    original_name="Alexander",
    gender=Gender.MASCULINE,
    themes=[Theme.STRENGTH, Theme.FREEDOM]
)
print(skill.format_names_display(names, "Alexander"))

# Step 2: User picks name #1 → generate poem
chosen = names[0]  # 明远 (Míng Yuǎn)
system_prompt, user_msg = skill.get_jueju_prompt(chosen)
llm_response = your_llm_client.chat(system_prompt, user_msg)
poem = skill.parse_jueju_response(llm_response, chosen)
print(skill.format_poem_display(poem))

# Step 3: Generate art prompts → send to DALL·E 3
seal_art   = skill.build_seal_art(chosen)
shanshui   = skill.build_shanshui_art(chosen, poem)
portrait   = skill.build_portrait_art(chosen)

image = dalle3.generate(
    prompt=seal_art.prompt,
    size="1024x1024",
    quality="hd",
    style="natural",
    negative_prompt=seal_art.negative_prompt,
)
```

### OpenClaw (Lobster Claw)

```bash
# Upload the skill folder
cp -r .trae/skills/cultural-naming-art YOUR_PROJECT/.trae/skills/
```

Your agent will auto-recognize all trigger phrases:
- *"Give me a Chinese name"*
- *"Create a seal with my name"*
- *"Write a classical Chinese poem"*
- *"Generate a Shanshui painting"*
- *"Ancient portrait avatar"*
- *"Give me everything!"*

### Tencent SkillHub

Upload `tencent_skilhub_manifest.json` at:
`https://skillhub.cloud.tencent.com/developer/publish`

---

## 📁 Project Structure

```
cultural-naming-art/
│
├── SKILL.md                         # Agent behavioral specification
├── openclaw_config.yaml             # OpenClaw deployment config
├── tencent_skilhub_manifest.json    # Tencent SkillHub manifest
├── skill.py                         # Core Python logic
├── prompts.py                       # High-fidelity art prompt library
│                                    #   - build_seal_prompt()
│                                    #   - build_shanshui_prompt()
│                                    #   - build_portrait_prompt()
├── DEPLOYMENT_GUIDE.md             # SkillHub publishing guide
├── requirements.txt                 # Python dependencies
└── README.md                        # This file
```

---

## 🛡️ Cultural Safety

| Protocol | Implementation |
|---|---|
| Taboo filter | 200+ characters blocked from name generation |
| Gender sensitivity | Always asks; neutral options available |
| Historical accuracy | Dynasty references cite era and master painters |
| Attribution | Every poem style credits Tang/Song classical origins |
| Art safety | No real historical figures as portrait subjects |
| Educational framing | Every output explains the *why* behind the art |

---

## 🤖 Supported Models

| Role | Provider | Model |
|---|---|---|
| **Name & Poetry** | Anthropic | claude-3-5-sonnet-20241022 |
| **Name & Poetry** | OpenAI | gpt-4o |
| **Seal Art** | OpenAI | dall-e-3 (quality: hd) |
| **Landscape/Portrait** | OpenAI | dall-e-3 or stable-diffusion-xl |
| **China fallback** | Tencent | hunyuan-image |

---

## 🎨 Complete User Journey

```
User:  "My name is Sarah. Can you give me a Chinese name?"

Skill: "What theme speaks to you?
        🌿 Nature · ⚔️ Strength · 📖 Wisdom
        🌸 Beauty · 🦅 Freedom · 🔥 Passion"

User:  "I'm a writer, so... Wisdom and Beauty!"

Skill: "Here are 3 names for 'Sarah' — Wisdom × Beauty:

  Option 1:  诗韵  (Shī Yùn)
             'Poetry + Rhythm / Rhyme'
             "A voice that carries the music of the ancients"

  Option 2:  雅晴  (Yǎ Qíng)
             'Elegant + Clear Sky'
             "Refined grace, as clear and bright as day"

  Option 3:  慧雅  (Huì Yǎ)
             'Wise + Elegant'
             "One whose wisdom is matched only by elegance"

  👉 Reply 1, 2, or 3 to choose!"

User:  "I love Option 1! 诗韵. Give me everything!"

Skill: → Generates 七言绝句 (诗韵 embedded in line 1)
        → Generates 七言律诗 (antithetical couplets annotated)
        → Builds seal prompt → [Generated: 诗韵 cinnabar seal on xuan paper]
        → Builds Shanshui prompt (Song style, Wisdom theme)
                               → [Generated: misty scholar's mountain at dawn]
        → Builds portrait prompt (Tang court poet aesthetic)
                               → [Generated: elegant figure with brush and scrolls]
        → Presents full cultural identity package ✨
```

---

## 🌍 Localization

Auto-detects and responds in: English · 简体中文 · 繁體中文 · Français · Deutsch · Español · 日本語 · 한국어

---

## 🗺️ Roadmap

- [ ] v2.1 — 五言绝句 (5-character Jueju) option
- [ ] v2.2 — Animated calligraphy seal carving (video)
- [ ] v2.3 — Regional name variants (Cantonese / Wu dialect)
- [ ] v2.4 — Printable PDF scroll export
- [ ] v3.0 — Real-time brush-painting video generation

---

## 🤝 Contributing

Issues and pull requests are welcome! Most wanted:
- 🔤 Expand phonetic mapping table for more name origins
- 🎨 New dynasty aesthetic presets
- 📜 Improved antithetical couplet generation
- 🌏 Regional dialect name variants

---

## 📜 License

[MIT](LICENSE) — free to use, modify, and distribute.

---

<div align="center">

**Made with 墨 (ink) and ❤️ by [XiaoAIPensieve](https://github.com/XiaoAIPensieve)**

*"每一个名字，都是一首诗的开始。"*
*"Every name is the beginning of a poem."*

[⭐ Star this repo](https://github.com/XiaoAIPensieve/cultural-naming-art) ·
[🐛 Report an Issue](https://github.com/XiaoAIPensieve/cultural-naming-art/issues) ·
[💬 Discussions](https://github.com/XiaoAIPensieve/cultural-naming-art/discussions)

</div>
