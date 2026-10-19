# Dated ToAPIs image prices for this guide

Quoted with the test key on **2026-10-13**. These historical model-specific rates belong to this ToAPIs guide, not upstream provider documentation. Query `GET /v1/pricing?model=...` with your own key before submitting a new request.

| Display model / API ID | Tested preset | Historical quote | Confirmed charge per image | Calls |
|---|---|---:|---:|---:|
| gpt-image-2(VIP) / `gpt-image-2-vip` | low / 1K / n=1 | $0.0019/image | $0.0019 | 3 |
| gpt-image-2 / `gpt-image-2` | 1K / n=1; quality omitted | $0.015/image | $0.015 | 1 |

gpt-image-2(VIP) starts at **$0.0019/image**; the tested low/1K configuration is **$0.0019/image**. Models, channels and quality settings differ; rates do not imply equivalent output quality. Returned account discounts are already included.

The four image charges total **$0.0207**. API billing was absent; the account owner confirmed the dashboard charges. One earlier unconfirmed submission is excluded. Scumble is image-only; no video pricing or video acceptance applies here.

[Actual charges](COSTS.md) · [Original dated pricing snapshot](evidence/pricing.json) · [Image checklist](ACCEPTANCE.md) · [Current ToAPIs rates](https://toapis.com/en/pricing) · [Pricing API](https://docs.toapis.com/docs/en/api-reference/account/pricing) · [中文](PRICING_zh-CN.md)
