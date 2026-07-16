# Connect your AI to the world

The showcase bundle includes **`kano`**, a small server that lets an AI query
the exact world you're walking in Hīkoi, over the **Model Context Protocol
(MCP)**. Everything runs locally — no account, no network.

> You do **not** need this to enjoy the showcase — Hīkoi answers questions
> about the world on its own (right-click anything). This is for pointing your
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

- **Life at the spawn:** *"What grows at -2, -138, and tell me one plant's
  life story?"* → `grows` + `specimen`. (A lowland emergent rainforest — the
  tallest trees on the world.)
- **Causal climate:** *"Why is -2, -138 a rainforest? Walk it back to the
  cause."* → `why` — the world traces it to the equatorial convergence.
- **First-person scene:** *"Stand at 42, 18 — what would I see, hear, and
  feel?"* → `walk` + `observe` + `listen`. (A cool temperate forest in a basin
  below sea level.)
- **Follow the water:** *"Trace the drainage from -2, -138 down to the sea."*
  → `trace` — source-to-sea narrative.
- **The world's oddities:** *"Show me the strangest places on this world,
  then explain one."* → `surprises`, then interrogate a pick.
- **Prospecting (an agentic example):** *"Is there anywhere near 0, -136 where
  a mine would make geological sense? Justify it from the rocks."* → the AI
  reads `tectonics`, sweeps with `survey`, and confirms with `minerals` — here
  it finds a laterite bauxite-nickel deposit under the deep tropical
  weathering. A nice demo of multi-step reasoning, though the showcase is
  about the world, not the ore.

Right-click any feature in Hīkoi to copy its coordinates, then paste them into
questions of your own.

## Why the answers agree with what you see

Hīkoi and `kano` call the **same deterministic world model**. The text isn't
commentary about a screenshot — it's another projection of the same world, so
the ridge you're looking at and the tectonic story the AI tells are the same
fact seen two ways.
