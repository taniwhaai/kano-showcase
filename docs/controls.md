# Controls

The scrollable **Controls** window opens at startup. Reopen it with **F1** or
the **Controls** button. It includes direct clock-speed and pause/resume buttons.
Close it with **F1**, **Esc** or **×** to use the keys below, then click the
landscape to capture the pointer and look around.

## Moving

| Input | Action |
|---|---|
| **W A S D** / arrows | walk |
| **Shift** (held) | run (~5× walk) |
| **Space** | jump |
| **mouse** | look |
| **F** | fly / land |
| **E / C** or **Page Up / Page Down** | climb / descend while flying |

## Interrogating

| Input | Action |
|---|---|
| **I** | open the interrogation panel — six tabs (Here · Why · Weather · Ground · Life · Scene) answered from the world itself; copy the coordinates, the query, or a link |
| **Right mouse button** | inspect the tree you're facing — its species prose and the generative flora DSL that grew it |
| **Left mouse button** | (cursor free) re-capture look / dismiss the panel |
| **Esc** | close panels and free the pointer |
| **F1** | open / close the Controls window |
| **Q** | open the quit confirmation |

## Travel

| Input | Action |
|---|---|
| **G** | globe view — click a spot to travel, drag to orbit, scroll to zoom (curated places show as gold pins) |
| **M** | overview map of where you're standing — click to travel |
| **Tab** | show / hide the Places list |
| **1**–**7** | jump to a curated place |
| **B** | copy a bookmark of your location, view and time |
| **?** | random land teleport |
| **J** | start / end the three-stop guided tour |
| **N** | next tour stop |
| **K** | pause / resume the tour |

The tour waits for each scene to settle, then stays for one minute. It
advances the clock to local daylight. Some Places arrivals start in flight
with a chosen heading; **F** lands, and **E/C** changes height. The exploration
panel also provides these controls and a visitor link to
[the running Copperhollow settlement](https://copperhollow.taniwha.ai).

Launch at a chosen spot with `--focus lat,lon`, or `--visit <bookmark>`.

## Time & display

| Input | Action |
|---|---|
| **.** / **,** | skip the day–night clock forward / back (~1 hour per press) |
| **P** | pause / resume the clock |
| **T** | cycle clock speed: 1× → 10× → 60× → 600× → 1× |
| **H** | show / hide the scanner HUD — compass, reticle, and the lat/lon of what you're facing (hidden at launch) |
| **R** | toggle the world grid |
| **O** | toggle the painterly colour grade |
| **V** | toggle vsync |

The default is **60×**: one real minute advances one world hour. To slow it to
real time, press **T twice** from the default, or choose **Real time · 1×** in
Controls. **Slow · 10×** is also available there. **P** pauses/resumes time.

Use **Advance to daylight** in the exploration panel when the scene is dark.
