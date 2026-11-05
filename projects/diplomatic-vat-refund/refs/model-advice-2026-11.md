# Receipt-reading model: desk research, 2026-11-05

Advice for the open model question, not a decision. Nothing here was tested on a receipt.
Written by Claude, so a recommendation involving Claude needs an independent test.

## Provider facts

| Model | Input / output per 1M tokens | Most image detail | Where it runs |
|---|---|---|---|
| DeepSeek `deepseek-flash` (V4.1 Flash) | $0.15 / $0.60 off-peak; $0.30 / $1.20 peak | About 1300x1300 pixels' worth; 1,024 tokens per image at most | DeepSeek's privacy policy says data is stored in China; its API terms weren't checked |
| Claude Haiku 5.5 | $0.10 / $0.50 | 2,576 px long edge; 4,784 tokens at most | Global or US only |
| Claude Sonnet 5.5 | $2 / $10 | 2,576 px long edge; 4,784 tokens at most | Global or US only |

DeepSeek's peak hours are 01:00-04:00 and 06:00-10:00 UTC on weekdays. `deepseek-v4-pro` has no vision.

## Estimated cost per receipt

Assumes 2,000 prompt tokens, 1,500 output tokens, one image at the most detail the model
accepts, and no thinking tokens. Actual cost must be measured.

| Model | Per receipt | Per 1,000 |
|---|---|---|
| Claude Haiku 5.5 | $0.0014 | $1.43 |
| DeepSeek Flash, off-peak | $0.0014 | $1.35 |
| DeepSeek Flash, peak | $0.0027 | $2.71 |
| Claude Sonnet 5.5 | $0.029 | $28.57 |

DIVAR's README estimates EUR 0.05-0.12 per receipt on Claude Opus 5.

## Evidence on reading quality

- No published test of the current `deepseek-flash` on German receipts was found.
- Better Stack saw an older DeepSeek vision version misread small text ("Per 15g" as "Per 30g") and blamed downscaling. DeepSeek now documents a higher limit, so this may no longer hold.
- Published receipt and invoice benchmarks mostly omit DeepSeek or test older models.

## Privacy evidence

- DeepSeek's policy (updated 2026-02-10) says it stores personal data in China and lists model training as a purpose, with an opt-out. It excludes end users of apps built on its developer platform, so its API terms need reading.
- In 2025 the Berlin data protection commissioner called DeepSeek's transfers of German users' data to China unlawful. That action concerned the app, not the API, and no later status was found.
- Claude's first-party API offers no EU-only processing either: inference is global or US only.

## Candidates to test

- DeepSeek Flash, the user's preference.
- Claude Haiku 5.5, the same price range.
- An option with EU processing: Gemini on a Vertex EU region, or Mistral OCR. Their prices and EU hosting come from secondary sources and need checking.
- Claude Sonnet 5.5, as a quality reference.

## Sources

- https://api-docs.deepseek.com/quick_start/pricing
- https://api-docs.deepseek.com/guides/vision
- https://cdn.deepseek.com/policies/en-US/deepseek-privacy-policy.html
- https://platform.claude.com/docs/en/about-claude/pricing
- https://platform.claude.com/docs/en/build-with-claude/vision
- https://platform.claude.com/docs/en/manage-claude/data-residency
- https://betterstack.com/community/guides/ai/deepseek-vision-api/
- https://ocrbenchmark.pages.dev
- https://benchmarking.nanonets.com/benchmarks/idp
- https://heise.de/-10462419
