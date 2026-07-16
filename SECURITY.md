# Security

If you find a security issue in the Kano Showcase binaries or the bundled
`kano` MCP daemon, please email **security@taniwha.ai** rather than opening a
public issue.

Notes for the security-curious:

- Hīkoi and `kano` are fully offline — no accounts, no telemetry, no network
  calls.
- `kano` (local MCP) communicates over stdio only; it opens no network ports.
- Release assets ship with SHA-256 checksums (the `.sha256` file beside each
  download); verify your download against them.
