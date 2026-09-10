# Stroop Contracts

> Soroban contracts and deployment tooling for the Stroop identity protocol.

Part of [Stroop](https://github.com/Stampbase), an open identity layer for
Stellar, built by [Stampbase](https://github.com/Stampbase).

## Where this fits

This repository is the source of truth for Stroop identity. Everything else —
the SDK, the web applications, Passport — reads state that originates here.

Credential attestations are **not** in scope. Those remain in StampRegistry;
the identity registry must not duplicate credential logic.

## Status

**Pre-alpha.** Scaffolding only. No contract has been written, and nothing
has been deployed to testnet or mainnet.

Nothing here is deployed to Stellar mainnet. Do not use any part of this
repository to custody value.

### Planned scope

- `IdentityRegistry`: profiles, controllers, canonical usernames
- Verified wallet associations with proof of wallet control
- Active avatar references
- Primary payment destination, mainnet-only by construction

### Explicitly out of scope

Credential attestations, participation history, and stamps — these belong to
StampRegistry.

## Building

```bash
rustup target add wasm32v1-none
cargo build
```

## Testing

```bash
cargo fmt --all --check
cargo clippy --all-targets -- -D warnings
cargo test --all
cargo audit
```

Authorization changes require negative tests. Proving the authorized caller
succeeds is half a test; the other half is proving every unauthorized caller is
rejected.

## Deployment keys

Deployment scripts take signing keys from environment variables or a secure
signer. No secret key belongs in this repository, in a script, in a fixture, or
in CI logs. Testnet and mainnet configuration are kept explicitly separate.

## Security

Do not report vulnerabilities through public issues. See
[`SECURITY.md`](./SECURITY.md) for private reporting.

## License

[Apache-2.0](./LICENSE).

## Related repositories

| Repository | Purpose |
| --- | --- |
| [`stroop-contracts`](https://github.com/Stampbase/stroop-contracts) | Soroban contracts: identity registry, usernames, wallet links |
| [`stroop-sdk`](https://github.com/Stampbase/stroop-sdk) | `@stroop-id/sdk` and `@stroop-id/react` |
| [`stroop-web`](https://github.com/Stampbase/stroop-web) | stroop.id — identity application |
| [`stroopy`](https://github.com/Stampbase/stroopy) | stroopy.me — character application |
| [`stroop-docs`](https://github.com/Stampbase/stroop-docs) | Protocol specifications |
