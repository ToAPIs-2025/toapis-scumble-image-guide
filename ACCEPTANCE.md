# Scumble image-provider acceptance checklist

Aligned on October 19, 2026 with [the maintainer's checklist](https://github.com/DenRakEiw/scumble/issues/5#issuecomment-6217158456) and [closure note](https://github.com/DenRakEiw/scumble/issues/5#issuecomment-6233198798). Scumble has no video features. Four standard/VIP calls were acknowledged; this is not full canvas acceptance.

| Item | Required behavior | Current evidence / remaining work |
|---|---|---|
| 1. Official-channel mask edit | Selection uploaded as `mask_url`; transparent = repaint; use the crop's own aspect ratio. | **Open; upstream will run this.** The four standard/VIP calls did not use this mask route. Do not substitute a reference edit for this test. |
| 2. Reference uploads | Stay within the channel's documented count, dimensions and file-size limits. | Upload path demonstrated in standard/VIP evidence; maximum-limit and invalid-input boundaries have not all been exercised. |
| 3. Submission and stable status | Persist the submit task ID; query that same task. Do not resubmit after a lost answer. | Four successful provider calls and wrapper records. Any 429/503 retry must follow upstream/API rules and account for uncertain acceptance; this guide makes no additional paid retry. |
| 4. Results usable for stitching | Record real dimensions and return usable image bytes for the selected crop. | Four 1024×1024 PNGs recorded. Non-square crops, selection stitching and the full canvas round trip remain unvalidated here. |
| 5. Readable failures | Return actionable errors with secrets redacted. | Capture redacted request/configuration, HTTP status and error text for support. No additional live negative-case acceptance is claimed. |

## Support handoff

Supply the Scumble commit/version, recipe and channel, expected crop size, mask alpha semantics/dimensions, reference count/size, expected versus actual output dimensions, and redacted status/error text. Send keys, request IDs and account details privately. ToAPIs can help clarify request mapping, limits, task status and errors; the maintainer owns upstream acceptance, including the pending official mask case.

The dated ToAPIs costs stay in [this guide](PRICING.md); no vendor comparison or vendor-maintained documentation page is requested upstream. [中文](ACCEPTANCE_zh-CN.md).
