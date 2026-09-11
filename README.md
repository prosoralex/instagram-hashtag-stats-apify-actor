# Instagram Hashtag Stats — Apify Actor usage guide

[![Run for free on Apify](https://img.shields.io/badge/Apify-Run%20it%20free%20%E2%80%94%20%245%2Fmo%20credit-24C1E0)](https://console.apify.com/sign-up?fpr=aupara)

Get total post count and top posts for any Instagram hashtag — no login required. Powered by real browser rendering for reliable results even on the most popular hashtags. Perfect for content strategy, trend monitoring and influencer research.

> **This repository does not contain the Actor's source code.** The Actor
> itself is closed-source and runs on Apify's infrastructure — this repo is
> just documentation and example client code showing how to call it via the
> Apify API/SDK with your own Apify API token. Think of it as a "cookbook"
> repo, not the product itself.

**Run it on Apify →** [https://apify.com/leadsbrary/instagram-hashtag-stats?fpr=aupara](https://apify.com/leadsbrary/instagram-hashtag-stats?fpr=aupara)

## What it does

A scraper Actor that extracts Instagram hashtag statistics and current top posts: it retrieves hashtag-level metrics (total post count and human-readable volume) and captures top-post metadata including post identifiers and links, media type (video, image, carousel), author handle and numeric author ID, engagement metrics (likes, comments, video views), thumbnail/display image URLs, caption text, and ISO timestamps. The Actor uses a dual extraction strategy (fast public API probe then headless browser fallback) with stealth browser rendering (Playwright/stealth techniques), progressive scrolling to trigger client-side lazy loading, parallel processing, and automatic retries; it operates against public Instagram pages without requiring login or session cookies.…

## Pricing

Pay-per-event pricing — you only pay for what the Actor actually delivers:

- **Actor Start** — $0.00005 (one-time, per run). Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
- **Instagram Hashtag Stats & Top Posts** — $0.003–$0.001 depending on your Apify usage tier. Get total post count and top posts for any Instagram hashtag — no login required. Powered by real browser rendering for reliable results even on the most popular hashtags. Perfect for content strategy, trend monitoring and influencer research.

*(Apify may also charge a small amount for the platform compute the Actor
uses while running — see the [pricing tab](https://apify.com/leadsbrary/instagram-hashtag-stats?fpr=aupara) on the Actor page
for exact current numbers.)*

## Quick start

You need an Apify account and API token (`console.apify.com` → Settings →
Integrations). Don't have one yet? See the signup section below — new
accounts get **$5 of free usage credit every month**.

### cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/leadsbrary~instagram-hashtag-stats/runs?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
  "hashtags": [
    "travel"
  ],
  "includeTopPosts": true,
  "maxTopPosts": 9,
  "concurrency": 3
}'
```

### Python (`apify-client`)

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")

run_input = {
  "hashtags": [
    "travel"
  ],
  "includeTopPosts": true,
  "maxTopPosts": 9,
  "concurrency": 3
}

run = client.actor("leadsbrary/instagram-hashtag-stats").call(run_input=run_input)

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

### JavaScript (`apify-client`)

```javascript
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: 'YOUR_APIFY_TOKEN' });

const runInput = {
  "hashtags": [
    "travel"
  ],
  "includeTopPosts": true,
  "maxTopPosts": 9,
  "concurrency": 3
};

const run = await client.actor('leadsbrary/instagram-hashtag-stats').call(runInput);
const { items } = await client.dataset(run.defaultDatasetId).listItems();
console.log(items);
```

See [`example.py`](./example.py) in this repo for a complete runnable script.

## Don't have an Apify account yet?

[Sign up here](https://console.apify.com/sign-up?fpr=aupara) — new accounts get **$5 of free platform credit
every month**, enough to try most Actors without paying anything upfront.
Browsing for other tools? The full [Apify Store](https://apify.com/store?fpr=aupara) has thousands
of ready-made Actors.

## Links

- Actor page (run it, see live pricing/reviews): [https://apify.com/leadsbrary/instagram-hashtag-stats?fpr=aupara](https://apify.com/leadsbrary/instagram-hashtag-stats?fpr=aupara)
- All Actors from this developer: [https://apify.com/leadsbrary?fpr=aupara](https://apify.com/leadsbrary?fpr=aupara)
- Apify API docs: [https://docs.apify.com/api/v2](https://docs.apify.com/api/v2)

## License

The example code in this repository (README snippets, `example.py`) is
released under the MIT License — see [LICENSE](./LICENSE). This does not
cover the Actor itself, which remains closed-source and is operated by its
developer on the Apify platform.
