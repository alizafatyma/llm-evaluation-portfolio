# LLM Evaluation Lab

A human evaluation of two large language models, compared side by side on 12 tasks across **coding, reasoning, instruction following, English–Urdu language ability, factuality, and safety**. Every response is scored on a written 5-dimension rubric and tagged for specific errors. Each pair is then compared on a 7-point preference scale with a written justification.

This mirrors the workflow used in AI training and RLHF (reinforcement learning from human feedback) data work.

**Live report:** https://alizafatyma.github.io/llm-evaluation-portfolio/

## What's evaluated

| # | Category | Task | What it tests |
|---|----------|------|---------------|
| 1 | Coding | Debug an async JavaScript function | Spotting that `forEach` doesn't await async callbacks |
| 2 | Coding | Top-customers SQL query | Correct grouping, date filtering, handling ties |
| 3 | Coding | Secure a Stripe webhook endpoint | Signature verification, raw body, secrets, idempotency |
| 4 | Coding | Explain a C++ crash | Dangling reference / undefined behaviour |
| 5 | Reasoning | Reverse a percentage | Avoiding the classic ×1.12 vs ÷0.88 trap |
| 6 | Reasoning | Time-zone conversion | Daylight saving (BST vs GMT) |
| 7 | Instruction following | Strict formatting constraints | Exact bullet count, word limits, no emojis, no title |
| 8 | English–Urdu | Translate a support message into formal Urdu | Script, register, completeness |
| 9 | English–Urdu | Roman Urdu → natural English | Meaning and tone, not word-for-word |
| 10 | English–Urdu | Explain a tech concept in simple Urdu | Answering in the user's language, length control |
| 11 | Factuality | False-premise question | Correcting a wrong assumption instead of hallucinating |
| 12 | Safety | Access to someone else's account | Refusing harm **without** over-refusing: still giving the legitimate recovery path |

## Method

1. **Reference notes first.** Before collecting any responses, each task got written notes: what a strong answer must include and the known failure modes. This keeps scoring consistent and stops a confident, polished answer from being scored higher than a correct one.
2. **Controlled collection.** Each prompt was sent to both models in a fresh chat, with no system prompt and no follow-up turns.
3. **Independent scoring.** Each response was rated 1–5 on:
   - **Correctness:** facts, code, and maths are right
   - **Instruction following:** every explicit constraint is met
   - **Helpfulness:** solves the real need, completely
   - **Clarity & style:** well organised, right length, natural language
   - **Safety:** no harmful help, and no needless refusal or preaching
4. **Error tagging.** Factual error, hallucination, code bug, ignored instruction, accepted false premise, unsafe content, over-refusal, too verbose, incomplete, language issue.
5. **Pairwise preference.** A 7-point scale (A much better → B much better) with a justification that names the deciding factor.
6. **Verification.** Claims were checked independently: code was run, maths recomputed, and facts looked up.

The full rubric with score anchors is on the **Rubric & Guidelines** tab of the live page.

## Key findings

_Add 3–5 takeaways here after finishing the evaluation, the same ones you wrote in the tool._

## Run it yourself

It's a single HTML file with no build step and no dependencies.

1. Open `index.html` in a browser (or visit the live page with `?edit` on the end of the URL).
2. Set the two model names, then work through the 12 tasks. Progress saves automatically in your browser.
3. Click **Export results.json** when you're done.

## Publish on GitHub Pages

1. Put `index.html`, `README.md`, and your exported `results.json` in a public GitHub repo named `llm-evaluation-portfolio`.
2. Go to **Settings → Pages → Deploy from branch → main / root**.
3. When the page finds `results.json` next to it, it opens straight to a read-only report.

---
Built and evaluated by **Aliza Fatima**, a Software Engineer (BSSE, University of Central Punjab) who evaluates AI models for coding, reasoning, and English/Urdu language tasks.
