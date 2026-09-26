# Trustee Wallet Web — Living Phase-1 Tracker

**Current baseline:** `b3da467f`  
**Custody:** Non-custodial by default  
**Application auth:** WebAuthn/passkeys planned; **Manus OAuth excluded**

## Current state

- [x] Static responsive wallet prototype confirmed healthy.
- [x] Desktop/mobile visual verification completed.
- [x] TypeScript and production build checks passed.
- [x] Browser smoke test completed for navigation and Send modal.
- [x] Phase-1 architecture and security plan written.
- [x] Inherited Manus OAuth helper/dialog artifacts removed.
- [ ] Full-stack scaffold and database foundation.
- [ ] Passkey registration/login and session lifecycle.
- [ ] Security middleware, redaction, rate limits, and health checks.
- [ ] Public wallet metadata schema and authorization tests.
- [ ] Mock provider adapter, cache, cursors, and sync status.
- [ ] Stage-1 security verification and checkpoint.

## Decision log

### ADR-001 — Non-custodial custody

Wallet keys remain on the user device. The backend stores public metadata only and later accepts signed payloads, never unsigned key material.

### ADR-002 — No Manus OAuth

Manus OAuth is not part of the application authentication architecture. The scaffold's inherited OAuth helper/dialog were removed. Provider-neutral WebAuthn passkeys are the planned account-authentication mechanism; wallet unlock remains an independent local control.

### ADR-003 — Read-only before signing

Build and verify API, database, auth, observability, and provider isolation before introducing recovery phrases, private keys, transaction signing, swaps, or mainnet mutation.

## Active risks

- The current UI still uses hardcoded demo data.
- Full-stack migration has not started.
- No wallet-secret or signing path exists yet, which is intentional.
- Independent security review remains a release gate before any mainnet signing.
