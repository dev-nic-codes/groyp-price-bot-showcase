# Architecture

```mermaid
flowchart TD
    M["Market data"] --> I["GROYP identity checks"]
    I --> C["Private cache"]
    C --> P["Price publisher"]
    E["Exchange events"] --> N["Trade normalization"]
    N --> W["Public wallet-label enrichment"]
    W --> O["Durable alert outbox"]
    O --> P
    A["Private admin controls"] --> C
    A --> O
```

Wallet labels are presentation enrichment, not an authorization source. Publication and alert delivery remain separate recovery domains. Exact providers, addresses, and state formats are omitted.
