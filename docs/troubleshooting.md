# Troubleshooting

## Hīkoi won't start / closes immediately

Look for **`walk-error.log`** beside the executable — it names the problem.
Most often:

- **World file not found.** `default.s9z` must sit beside `hikoi` (it does in
  the zip — keep the folder together), or pass `--load <path>`.
- **No compatible GPU / drivers.** Hīkoi needs Vulkan, Metal, or DX12 with
  reasonably current drivers. Update your GPU drivers and retry.

## Unsigned-binary warnings (expected)

These builds aren't code-signed yet, so your OS will caution you:

- **Windows:** "Windows protected your PC" → **More info** → **Run anyway**.
- **macOS:** "cannot be opened because the developer cannot be verified" →
  right-click the app → **Open** → **Open**; or in a terminal:
  `xattr -d com.apple.quarantine /path/to/hikoi`.
- **Linux:** `chmod +x hikoi` if it isn't executable.

## Black screen or crash on load

A failed load or GPU/driver problem can leave a blank screen. Check
`walk-error.log` and try updating drivers. On laptops with
switchable graphics, ensure Hīkoi runs on the discrete GPU.

## Graphics validation

Release-specific graphics results are recorded with the release. RC16
has been captured on NVIDIA RTX 3080 with Vulkan and DX12, and
Intel integrated graphics with DX12. Physical Apple Silicon and Linux/Vulkan
graphics checks remain outstanding. An earlier RC16 candidate and RC15 both
aborted at their first rendered frame on the virtual Mac CI runner; this does
not establish native Mac behavior. Linux software Vulkan rendered successfully
as diagnostic evidence. A
successful platform build alone does not establish a working GPU backend.
Tell us your OS, GPU and driver through an [issue](https://github.com/taniwhaai/kano-showcase/issues).

Use recent Vulkan, Metal or DX12 drivers and at least 4 GB of graphics/shared
memory. Linux requires Vulkan drivers and an Ubuntu 22.04 (glibc 2.35) or
newer compatible runtime. The indexed terrain path on Metal and
DX12 uses the same dense ground field as the Vulkan terrain path, with detail
reducing away from the card centre.

## Globe view (G) shows only water

If pressing **G** shows an all-ocean planet with no land — even though walking
around first-person renders terrain fine — your GPU's **Vulkan** driver is
mis-rendering the globe (seen on some Windows cards, e.g. GTX 10-series). The
world data is fine; only that one view is affected.

Recent builds auto-select the DX12 backend on affected Windows GPUs, so this
shouldn't happen. If it still does, launch forcing DX12 from PowerShell in the
unzipped folder:

```powershell
$env:WGPU_BACKEND="dx12"; .\hikoi.exe
```

The first `gpu:` line it prints should then read `Dx12`, and the globe will show
land if the problem was specific to the Vulkan backend.

## Waiting for terrain or vegetation

Terrain and vegetation build as you arrive. Let the scene settle; the wait
varies by hardware and location. Keep `default.flora` beside the executables
and world. Its pre-baked assets save repeated vegetation work at curated
stops; a missing or rejected pack falls back to slower live generation.
The guided tour waits for the current scene before counting its stop time.

## It runs but a feature looks wrong

Please file an [issue](https://github.com/taniwhaai/kano-showcase/issues) with your OS, GPU, driver version, the
coordinates (press I), and a screenshot.
