# Support

**Something not working?** Open an [issue](https://github.com/taniwhaai/kano-showcase/issues) and include:

1. Your OS and version (e.g. Windows 11, macOS 15, Ubuntu 24.04).
2. Your GPU and driver version.
3. What happened vs what you expected.
4. **`walk-error.log`** — if Hīkoi failed to start, this file appears beside
   the executable and says why. Paste its contents — but **read it first and
   redact anything personal** (usernames, local file paths, machine names, or
   anything else you'd rather not post publicly).
5. The release version you downloaded (from the zip name).

Common fixes first: see [Troubleshooting](docs/troubleshooting.md), including
the graphics validation notes and the unsigned-binary first-run steps.

Hīkoi needs a Vulkan / Metal / DX12-class GPU with recent drivers and at least
4 GB of graphics or shared memory; 8 GB system RAM is recommended. A Windows
RTX 3080 / Vulkan rainy-forest capture at 1280×720 used a peak 2.75 GiB viewer
working set; leave additional room for the OS and graphics allocations. Very old
or virtualized GPUs are the most common cause of a black screen or crash on
startup.
