# OAuth PKCE

Proof Key for Code Exchange (PKCE, RFC 7636) is an OAuth 2.0 extension for public clients. The client creates a high-entropy `code_verifier`, derives `code_challenge` (recommended method `S256`), sends the challenge on the authorization request, and sends the verifier on the token request.

## Claims

- PKCE is specified in RFC 7636 — https://www.rfc-editor.org/rfc/rfc7636
- The S256 challenge is BASE64URL(SHA256(ASCII(code_verifier))) — https://www.rfc-editor.org/rfc/rfc7636#section-4.2

## Gaps

This sample note exists so hub search can be verified (`search-knowledge "oauth pkce"`). Expand it when a real research run covers PKCE.
