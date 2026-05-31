# jsps-dc-application

A Claude Code skill for drafting **JSPS 特別研究員-DC (DC1/DC2)** application content files
(申請内容ファイル) — the research plan and the self-analysis of research ability — in
**Japanese or English**, producing **compile-ready LaTeX** (KakenhiLaTeX template).

学振 特別研究員-DC の「申請内容ファイル」(研究計画＋研究遂行力の自己分析)を、
日本語/英語で、採用級の構成・表現で起草・推敲・翻訳するための Claude Code スキルです。

> Scope: **DC1 / DC2 only.** For KAKENHI *project* grants (基盤/若手/挑戦的) use a grant-proposal
> skill instead; this is a fellowship (evaluates the *researcher*, not the project).

## What it does

Follows the official DC 様式 (4 sections, page budget **1 / 2 / 1 / 2**) and the JSPS
review criteria (審査の観点):

| Section | Pages | Content |
|---|---|---|
| 【２】(1) 研究の概要及び研究の位置づけ | 1 | summary (~500 字) + field background/issues + origin of the idea |
| 【２】(2) 研究目的・内容等 | 2 | objectives, methods, yearly plan, originality, expected results |
| 【３】人権の保護及び法令等の遵守への対応 | 1 | ethics/compliance (or 該当しない) |
| 【４】研究遂行力の自己分析 | 2 | (1) strengths (evidenced by track record) (2) elements to develop |

It enforces hard rules: fill each section to its page budget, never fabricate achievements
or citations, keep figures legible in grayscale, and respect format constraints (≥10pt, ≤3MB).

## Install

**As a Claude Code plugin (recommended for teams):**
```
/plugin marketplace add OnizukaLab/jsps-dc-application
/plugin install jsps-dc-application@jsps-dc-application
```
Then invoke it by describing your task, e.g. *「学振 DC2 の申請内容ファイルを書きたい…」*
or `/jsps-dc-application:jsps-dc-application`.

**Manual (single user):**
```
git clone https://github.com/OnizukaLab/jsps-dc-application
cp -r jsps-dc-application/skills/jsps-dc-application ~/.claude/skills/
# restart Claude Code; invoke with /jsps-dc-application
```

## Layout

```
skills/jsps-dc-application/
├── SKILL.md                    # workflow + review criteria + hard rules + self-check
├── references/
│   ├── reference.md            # 様式 / format rules / 審査の観点 / A・B 区分
│   ├── writing-patterns.md     # adoption-level writing patterns (anonymized) + good/bad
│   ├── dc1-vs-dc2.md           # DC1 vs DC2 emphasis + JA(である調)/EN style
│   └── official/README.md      # links to the official JSPS docs (not bundled — see below)
├── assets/latex-template/      # KakenhiLaTeX DC template (multi) + CREDIT
└── evals/evals.json            # trigger + quality test cases
```

## Third-party content & license

- The skill's own content (SKILL.md, references authored here) is released under the **MIT License** (see `LICENSE`).
- `assets/latex-template/` is **KakenhiLaTeX** by Prof. Taku Yamanaka (Osaka U / KEK), redistributed
  under its own terms for researcher use — see `assets/latex-template/CREDIT.md`. Not covered by this repo's MIT license.
- The official **JSPS 募集要項 / 申請書作成要領 / 書面審査の手引** are **not bundled** (they are JSPS
  documents); `references/official/README.md` links to the official downloads. Always confirm you are
  using the **current year's** 様式.

## Disclaimer

This tool **assists drafting only**. Research content, the truthfulness of achievements, and the
final submission are the applicant's responsibility. Using AI to help write **your own** application
is legitimate; do not feed **others'** confidential application materials into generative AI.
