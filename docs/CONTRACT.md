# Minter contract

Do not implement against folklore. Implement against this file.

## Identity

- Product: **Minter**
- Repo: `computerpets-minter`
- Category: Microservices
- Idea: Minting Engine
- Port / surface: `8081`

## Must

- Stay canon with 210 species. No illegal hybrids. No swapped voices.
- Treat the desktop overlay as the main quest. This organ is optional until wired.
- Fail soft: the overlay keeps walking if this service is down, unless this *is* the overlay.
- No PII in public artifacts (Steam id, wallet, home path, webcam frames).

## Data

Pin(cid, sha256) · MintJob(id, status, tokenId, txHash) · Transfer(from, to, tokenId)

## Surface

- POST /v1/pin — metadata JSON + asset → CID
- POST /v1/mint — {owner, speciesId, cid} → tokenId + txHash
- POST /v1/transfer — escrow-safe transfer
- POST /v1/burn — owner-signed burn
- GET /v1/tx/{hash} — confirmation depth

## Neighbors

- computerpets Spring verifier
- computerpets-bazaar
- computerpets-atelier
- computerpets-ledger
- computerpets-studio

## Failure doctrine

RPC flake → Resilience4j retry + circuit open. Underpriced gas → park job. Reorg below N confirms → do not credit overlay unlock.

## Stack

Java 21 · Spring Boot 3.3 · web3j 4.12 · IPFS / Pinata · Flyway · PostgreSQL · Resilience4j
