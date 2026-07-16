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

Almost always a GPU/driver issue. Try updating drivers first. On laptops with
switchable graphics, ensure Hīkoi runs on the discrete GPU.

## Known-good GPUs

Confirmed working (this list grows as we test — tell us yours via an
[issue](../../issues)):

| Vendor | Examples | Backend |
|---|---|---|
| NVIDIA | GTX 10-series and newer | Vulkan / DX12 |
| AMD | RX 500-series and newer | Vulkan / DX12 |
| Apple | M1 and newer | Metal |
| Intel | Iris Xe / Arc | Vulkan / DX12 |

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
land. (macOS and Linux are unaffected.)

## Trees appear a second or two after the terrain (expected)

On arrival the terrain draws first, then the vegetation fades in over the next
1–3 seconds while assets stream in the background. This is normal — nothing is
broken; give it a moment to settle.

## It runs but a feature looks wrong

Please file an [issue](../../issues) with your OS, GPU, driver version, the
coordinates (right-click shows them), and a screenshot.
