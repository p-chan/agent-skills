# Credits

このスキルは、OpenAI と Anthropic の公式ドキュメントに共通する指針を土台にし、[Matt Pocock](https://github.com/mattpocock) の [`writing-for-agents`](https://github.com/mattpocock/skills/tree/main/skills/productivity/writing-for-agents) スキル（v1.2.3）の考え方を加えている。

## 公式ドキュメント

2026-09-27 に確認した。

- OpenAI
  - [Custom instructions with AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md)
  - [Customization](https://learn.chatgpt.com/docs/customization/overview)
  - [Best practices](https://learn.chatgpt.com/guides/best-practices)
  - [Build skills](https://learn.chatgpt.com/docs/build-skills)
  - [AGENTS.md](https://agents.md/)
- Anthropic
  - [How Claude remembers your project](https://code.claude.com/docs/en/memory)
  - [Best practices for Claude Code](https://code.claude.com/docs/en/best-practices)
  - [Extend Claude with skills](https://code.claude.com/docs/en/skills)
  - [Skill authoring best practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)

両社に共通する指針（指示ファイルを短く保つ、推測できない情報だけを書く、同じ誤りが繰り返されたら追加する、特定の作業は Skill に、例外なく守らせるルールは hook や lint に移す、`description` に何をするかといつ使うかを書き主な用途を先頭に置く、など）を土台にした。片方だけにある指針は、もう片方と矛盾しないものを取り入れた（確認できるほど具体的に書く、どこまで任せるかを作業に合わせる、参照を1階層に保つ、などは Anthropic、完了の定義を書く、読みすぎるときに優先して読む場所を書く、などは OpenAI）。

## writing-for-agents

`SKILL.md` の参照（原文では context pointer）、2つの負荷、情報の配置、完了条件、文書の分け方、キーワード（原文では leading word）、禁止の扱い、整理と削除の考え方と、`references/skills.md` の呼び出し方、呼び出し方での分け方、案内役の Skill（原文では router skill）の考え方は、`writing-for-agents` からほぼそのまま取り入れた。

## Licenses

### [mattpocock/skills](https://github.com/mattpocock/skills)

```text
MIT License

Copyright (c) 2026 Matt Pocock

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
