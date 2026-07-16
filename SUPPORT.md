# Support

**Something not working?** Open an [issue](../../issues) and include:

1. Your OS and version (e.g. Windows 11, macOS 15, Ubuntu 24.04).
2. Your GPU and driver version.
3. What happened vs what you expected.
4. **`walk-error.log`** — if Hīkoi failed to start, this file appears beside
   the executable and says why. Paste its contents — but **read it first and
   redact anything personal** (usernames, local file paths, machine names, or
   anything else you'd rather not post publicly).
5. The release version you downloaded (from the zip name).

Common fixes first: see [Troubleshooting](docs/troubleshooting.md), including
the known-good GPU list and the unsigned-binary first-run steps.

Hīkoi needs a Vulkan / Metal / DX12-class GPU with recent drivers. Very old
or virtualized GPUs are the most common cause of a black screen or crash on
startup.
