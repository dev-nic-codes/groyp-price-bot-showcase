# GROYP Price Bot

A Telegram market service for GROYP communities with resilient price sourcing, readable wallet labels, and reliable trade-alert delivery.

<!-- Add a redacted GROYP channel post here. -->

| Product link | [GROYP Prices on Telegram](https://t.me/groyppricesbot) |
|---|---|
| Audience | GROYP community operators and followers |
| Role | Product, backend, deployment, and operations by Nic |
| Status | Production |
| Code | Proprietary |

## Why it exists

Community price channels look simple, but live market data is frequently incomplete, throttled, or attached to the wrong asset. GROYP Price Bot validates identity before publication and keeps a private cached snapshot available during temporary provider trouble.

## Capabilities

- Scheduled GROYP price publishing
- Primary and validated fallback providers
- On-chain buy and sell notifications
- Trade deduplication and queued retries
- Wallet-name enrichment using public naming data
- Configurable thresholds, timing, templates, and destinations
- Private administrator menu and health information
- Backoff during provider or Telegram rate limits

## System shape

The price path validates provider results before updating its cache. The trade path normalizes venue-specific events and enriches public wallet labels before alerts enter a durable outbox.

See [Architecture](docs/architecture.md).

## Technology

Python standard library, Telegram Bot API, CoinGecko, DexScreener, TON providers, local private state, and systemd.

## Engineering work

- Rejecting lookalike market results
- Handling provider fallback without inconsistent public posts
- Caching wallet labels without exposing private operator data
- Preventing duplicate alerts across restarts
- Retrying delivery without advancing past failed work

## Current status

The supervised service reports active. Tests cover GROYP identity, market validation, venue classification, outbox behavior, templates, and private controls.

No implementation, wallet address, token address, endpoint, credential, state, or deployment file is present here.

[Roadmap](docs/roadmap.md) · [License](LICENSE) · Created by **Nic** ([GitHub](https://github.com/dev-nic-codes))
