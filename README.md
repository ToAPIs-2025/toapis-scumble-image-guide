# ToAPIs image-provider guide for Scumble


<!-- TOAPIS-MODELS-20261020 -->
## Model support and prices · 2026-10-20

Added standalone API presets: 31 image request templates and 8 video presets. Current-key pricing matches 26 image and 8 video presets; 5 image templates block new paid calls while pricing is unavailable. Native provider/UI/import/render acceptance remains as documented in the original guide below.

| Image model / tested preset | Current preset quote / image | Historical example amount / image | Fee evidence |
|---|---:|---:|---|
| gpt-image-2(VIP)<br><sub>low</sub> | $0.0019/image | **$0.0019/image** | Billing log, phase unknown |
| gpt-image-2.5-flare-vip<br><sub>low</sub> | Current-key quote unavailable | **$0.005272/image**<br><sub>Token-metered; current $/M unavailable. This sample is not a fixed image tariff.</sub> | Task receipt settled |
| nano_banana<br><sub>1K</sub> | $0.012/image | **$0.012/image** | Billing log, phase unknown |
| gemini-nano-banana-2.1<br><sub>1K</sub> | $0.015/image | **$0.015/image** | Billing log, phase unknown |
| gpt-image-2<br><sub>1K</sub> | $0.015/image | **$0.015/image** | Billing log, phase unknown |
| gemini-nano-banana-2.1-vip<br><sub>1K</sub> | $0.02/image | **$0.02/image** | Billing log, phase unknown |
| qwen-image-3.0<br><sub>1K</sub> | Current-key quote unavailable | **$0.021/image** | Billing log, phase unknown |
| gpt-image-2.5-flare<br><sub>high</sub> | $0.0225/image | **$0.0225/image** | Billing log, phase unknown |
| gpt-image-2.5-sunburst<br><sub>high</sub> | $0.0225/image | **$0.0225/image** | Billing log, phase unknown |
| flux-2-pro<br><sub>1K</sub> | $0.025/image | **$0.025/image** | Billing log, phase unknown |
| doubao-seedream-5-0-pro<br><sub>1K</sub> | $0.042857/image | **$0.042856/image** | Billing log, phase unknown |

| Video model | Preset / input | Settled clip charge | File duration | Case USD/s, ascending |
|---|---|---:|---:|---|
| MiniMax-H3-Max-Turbo | 5s / 480P / text-to-video | $0.125/clip | 5.18s | **$0.024131/s**<br><sub>Pricing tariff: $0.025/s</sub> |
| seedance-2-mini | 4s / 480p / first-frame | $0.13338/clip | 4.04s | **$0.033015/s**<br><sub>Pricing tariff: $3.285714/M total tokens</sub> |
| seedance-2-fast | 4s / 480p / text-to-video | $0.214568/clip | 4.04s | **$0.053111/s**<br><sub>Pricing tariff: $5.285714/M total tokens</sub> |
| kling-v3 | 5s / 720p / std / text-to-video | $0.3/clip | 5.04s | **$0.059524/s**<br><sub>Pricing tariff: $0.06/s</sub> |
| MiniMax-H3 | 5s / 768p / text-to-video | $0.32/clip | 5.17s | **$0.061896/s**<br><sub>Pricing tariff: $0.064/s</sub> |
| seedance-2 | 4s / 480p / first-frame | $0.26676/clip | 4.04s | **$0.06603/s**<br><sub>Pricing tariff: $6.571429/M total tokens</sub> |
| kling-3.0-turbo | 4s / 720p / text-to-video | $0.32/clip | 4.04s | **$0.079208/s**<br><sub>Pricing tariff: $0.08/s</sub> |
| seedance-2-5 | 4s / 480p / text-to-video | $0.3883/clip | 4.04s | **$0.096114/s**<br><sub>Pricing tariff: $10/M total tokens</sub> |

Pricing checked 2026-10-20. Image examples are dated 2026-10-17; video examples 2026-10-20. Tables sort by example amount or case USD/s. Presets and input modes differ; this is not a matched-settings quality ranking. Unknown-phase image logs are not confirmed final net settlements. Current quotes and historical amounts are separate. Video charges are billing=settled; case USD/s divides charge by actual file duration, never processing time. Token tariffs appear in small text and do not imply a fixed per-second price.

gpt-image-2(VIP) starts at $0.0019/image; this low/1K preset is $0.0019/image. The standalone sampler has 31 historically successful image request templates and 8 video presets. Current-key pricing matches 26 image and 8 video presets; 5 image templates block new paid submission until an exact price is available.

[Local sampler](toapis-models/README.md) · [Full price table](PRICING.md) · [Original media and fee evidence](https://github.com/ToAPIs-2025/toapis-quickstart/tree/main/tutorials/model-support-2026-10-20)

Original project examples, historical charges and integration instructions follow. Historical amounts are not rewritten as today’s quotes.

<!-- /TOAPIS-MODELS-20261020 -->

[简体中文](README_zh-CN.md) · [Original Scumble](https://github.com/DenRakEiw/scumble) · [Image acceptance checklist](ACCEPTANCE.md) · [Prices](PRICING.md) · [Actual charges](COSTS.md)

An independent **ToAPIs-maintained guide** to Scumble's existing image provider, with four real generated/reference-edited images, original inputs and a reusable wrapper. Install Scumble from the upstream project; this repository contains the guide and examples rather than an application release.

Scumble's maintainer acknowledged the four calls in [issue #5](https://github.com/DenRakEiw/scumble/issues/5#issuecomment-6217158456), and recorded the standard/VIP live-run scope in the [recipe](https://github.com/DenRakEiw/scumble/blob/4e6c17e5fc6f2ddbc35d201edaee3a04ac40356d/recipes/gpt_image_2.json) and [provider documentation](https://github.com/DenRakEiw/scumble/blob/4e6c17e5fc6f2ddbc35d201edaee3a04ac40356d/docs/RECIPES.md). This acknowledges the tested API path, not an endorsement, sponsorship or partnership.

**Scumble is an image editor with no video features.** Support for this guide follows the maintainer's image acceptance checklist. The official-channel mask edit remains for upstream to validate; our four calls do not validate it.

## Four real image outputs

Tested October 13, 2026, at upstream SHA `0d0be6b3e41f00e8621af14fe11597eaf258501f`. The wrapper invokes the unchanged `electron/main/providers/toapis.js` module: upload → generate/edit → query the same task → download. All four outputs are 1024×1024 PNGs.

![ToAPIs image-provider guide for Scumble](screenshots/en/01-cover.png)

| Example | Exact API ID / preset | Dashboard-confirmed charge | Original output |
|---|---|---:|---|
| Cream studio | `gpt-image-2-vip` / low / 1K | $0.0019 | [PNG](assets/vip-low-coral-bowl.png) |
| Dark studio, reference edit | `gpt-image-2-vip` / low / 1K | $0.0019 | [PNG](assets/vip-low-dark-bowl.png) |
| Sunlit interior, reference edit | `gpt-image-2-vip` / low / 1K | $0.0019 | [PNG](assets/vip-low-interior-bowl.png) |
| Standard studio | `gpt-image-2` / 1K | $0.015 | [PNG](assets/standard-coral-bowl.png) |

Total: **4.14 credits = $0.0207**, confirmed by the account owner's dashboard screenshot; the original API responses had no billing value. An earlier submission with incorrect context returned no task ID; its acceptance/cost remain unknown and are excluded. [Cost provenance](COSTS.md) · [Original prompts](cases/briefs.json) · [Full gallery](GALLERY.md).

The low/1K preset for **gpt-image-2(VIP) is $0.0019/image** in this historical run; other presets start at different prices. Models and quality settings differ. Dated ToAPIs rates and charges are maintained in this guide; upstream provider descriptions remain neutral.

## Run the provider examples

Node 20+ (tested 24.19.0) and Git. Install the Electron application using upstream instructions. The commands below exercise the provider module without launching the canvas. Default mode makes no API request; `--live` explicitly submits paid calls.

```bash
git clone https://github.com/ToAPIs-2025/toapis-scumble-image-guide.git

git clone https://github.com/DenRakEiw/scumble.git scumble-upstream

git -C scumble-upstream checkout 0d0be6b3e41f00e8621af14fe11597eaf258501f

cd toapis-scumble-image-guide

cp .env.example .env

# Fill TOAPIS_API_KEY privately. Windows PowerShell: Copy-Item .env.example .env

node run_cases.cjs --upstream ../scumble-upstream

node ../scumble-upstream/tools/toapis_test.js

node run_cases.cjs --upstream ../scumble-upstream --key-file .env --live --case vip-low-coral-bowl

node run_cases.cjs --upstream ../scumble-upstream --key-file .env --live
```

The dark/interior edits depend on `vip-low-coral-bowl`. Completed evidence is reused. A stored submission without a completed result stops execution: query the original task before considering another submission. Use the system CA/proxy configuration; keep TLS verification enabled.

## Provider mapping and validation boundary

1. Set `ctx.key` and **`ctx.base`** (origin, e.g. `https://toapis.cn`), rather than `ctx.settings`.
2. Standard uses `gpt-image-2` with quality omitted. VIP uses `gpt-image-2-vip`, `quality=low`, `resolution=1k`, `n=1`, `size=1:1`.
3. Reference images: `POST /v1/uploads/images`, then the uploaded URL in `reference_images`.
4. Generation: `POST /v1/images/generations`; status: `GET /v1/images/generations/{id}`; download the result without forwarding the API key.
5. The wrapper adds durable submission records, one generation POST per case, at least 8-second polling intervals, original-byte outputs and SHA-256 evidence.

The two reference edits are whole-image instruction edits. They do not validate alpha-mask inpainting. Canvas interaction, selection stitching, layer export and masked editing remain unvalidated here. The maintainer has recorded the upload/query/size results for standard and VIP; boundary limits and full canvas round trips still need separate acceptance. See [the five-item checklist](ACCEPTANCE.md).

## Upstream credit and support

The Scumble maintainer keeps provider documentation neutral and does not maintain vendor price-comparison pages. We maintain ToAPIs-specific configuration, dated costs and support evidence here. For an image-provider problem, supply the Scumble commit/version, recipe/channel, crop and mask dimensions, expected versus actual pixels, and a redacted error. Exchange private credentials and account details only through a private support channel.

The original author referral URL `https://toapis.com/login?aff=vfR1` is preserved. Its ownership and payout arrangements remain unverified; this guide does not claim or replace that code.

[Scumble source and license](https://github.com/DenRakEiw/scumble/tree/0d0be6b3e41f00e8621af14fe11597eaf258501f) · [GPL-3.0](LICENSE) · [ToAPIs model page](https://go2v.toapis.com/1013_scumble_cheaper_gh_en) · [Reusable guide images](SCREENSHOT_GUIDE.md)
