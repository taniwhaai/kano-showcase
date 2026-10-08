# Connect your AI to the world

The showcase bundle includes **`kano`**, a small server that lets an AI query
the exact world you're walking in Hīkoi, over the **Model Context Protocol
(MCP)**. Everything runs locally — no account, no network.

> You do **not** need this to enjoy the showcase — Hīkoi answers questions
> about the world on its own (press I). This is for pointing your
> *own* AI at the same world.

## Claude Desktop

Edit your MCP config (Settings → Developer → Edit Config, or the file
directly):

- macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
- Windows: `%APPDATA%\Claude\claude_desktop_config.json`

Add (use the **absolute path** to the files you unzipped):

```json
{
  "mcpServers": {
    "kano": {
      "command": "/absolute/path/to/kano",
      "args": ["/absolute/path/to/default.s9z"]
    }
  }
}
```

On Windows the paths look like `C:\\Users\\you\\kano-showcase\\kano.exe` and
`C:\\Users\\you\\kano-showcase\\default.s9z` (double backslashes in JSON).

Restart Claude Desktop. You'll see `kano` in the tools list.

## Claude Code (CLI)

From inside the unzipped folder:

```bash
claude mcp add kano -- ./kano ./default.s9z
```

(Or give absolute paths if you run it from elsewhere.)

## Cursor / other MCP clients

Any client that supports local stdio MCP servers works — point it at the
`kano` binary with the world file as its one argument. The command is always
`kano <path-to-default.s9z>`.

## Questions worth asking

Once connected, try these — coordinates are real spots on the showcase world
(the same places in Hīkoi's Tab menu):

- **Life at the spawn:** *"What grows at -3.14739, -19.03260, and tell me one
  plant's life story?"* → `grows` + `specimen`.
- **Causal climate:** *"Explain the climate at 54.64816, -42.66931. Why does
  this place support forest?"* → `why`.
- **First-person scene:** *"Stand at 17.14615, 126.34890 — what would I see
  and feel?"* → `walk` + `observe`.

These are Kowhai coordinates from RC16. Previous downloads contain a different
world. Broad queries describe regional conditions; use the viewer for the
finer local walking surface.
- **Follow the water:** *"Trace the drainage from -0.41, 38.07 down to the
  sea."* → `trace` — source-to-sea narrative.
- **The world's oddities:** *"Show me the strangest places on this world,
  then explain one."* → `surprises`, then interrogate a pick.
- **Prospecting (an agentic example):** *"Is there anywhere within a few
  hundred km of the spawn where a mine would make geological sense? Justify it
  from the rocks."* → the AI reads `tectonics`, sweeps with `survey`, and
  confirms candidates with `minerals` / `pluton` — a nice demo of multi-step
  reasoning, and the world is honest enough to come up dry where the geology
  says so. The showcase is about the world, not the ore.

Right-click any feature in Hīkoi to copy its coordinates, then paste them into
questions of your own.

## Why the answers agree with what you see

Hīkoi and `kano` call the **same deterministic world model**. The text isn't
commentary about a screenshot — it's another projection of the same world, so
the ridge you're looking at and the tectonic story the AI tells are the same
fact seen two ways.
