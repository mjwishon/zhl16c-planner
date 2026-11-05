# ZH-L16C Planner

> This planner follows the published Bühlmann ZH-L16C model with gradient factors and comes without warranty. Check every plan against your own planning software or dive computer, and dive within your training.

**App:** https://mjwishon.github.io/zhl16c-planner/

A Bühlmann ZH-L16C decompression planner with gradient factors for open circuit, CCR, and CCR with open-circuit bailout. It runs entirely in the browser, and nothing is sent anywhere.

## What you can set

- Mode: open circuit, CCR, or CCR with OC bailout
- Depth, bottom time (runtime at the start of the ascent), GF low and GF high
- Bottom gas, or diluent and setpoints (descent, bottom, deco), and the bailout gas
- Up to five deco or bailout gases, each with a default or custom switch depth
- Descent rate, ascent rate to the first stop, rate between stops, and rate to the surface
- Stop spacing, last stop depth, and 6 m spacing for stops deeper than 30 m
- No stops while a direct ascent stays within GF high (on by default)
- Safety stop on no-deco dives, with its depth and time (on by default, 3 min at 5 m)

## What it shows

- The dive plan as a runtime table (depth, stop time, runtime, gas, ppO₂ or setpoint, GF at each stop)
- The profile with the decompression ceiling
- A bar chart of all 16 compartments on surfacing, showing how close each is to its M-value and which one leads

## Install on a phone or desktop

- **iPhone / iPad (Safari):** Share → Add to Home Screen.
- **Android (Chrome):** menu → Install app.
- **Windows / macOS (Chrome or Edge):** install icon in the address bar.

After the first visit it also works offline.

## Method

- ZH-L16C with 16 compartments (compartment 1b), Schreiner equation while moving, exact loading at constant depth. Salt water at 10 m per bar.
- CCR loop: diluent inert gas at ambient pressure minus water vapour minus setpoint.
- No-deco limit: if a direct ascent keeps every compartment within GF high on surfacing, the plan has no stops (can be switched off).
- First stop: GF-low ceiling at the end of the bottom, rounded up to the stop grid. It moves one stop deeper if the ascent would already violate it (Baker's projected ascent).
- Each stop is held to the next whole minute, then a minute at a time until the ceiling at the next stop's GF clears the next stop. GF rises linearly with depth from GF low at the first stop to GF high at the surface.
- Open circuit and bailout use the richest gas within its switch depth. On the way to the first stop the switch happens at the switch depth; after that, on arrival at a stop.

## References

1. A. A. Bühlmann, *Decompression – Decompression Sickness*, Springer, 1984.
2. E. C. Baker, *Understanding M-values*, 1998.
3. E. C. Baker, *Clearing Up the Confusion About "Deep Stops"*, 1998.
4. E. C. Baker, public-domain decompression programs in Fortran.
5. H. R. Schreiner and P. L. Kelley, "A pragmatic view of decompression", *Underwater Physiology IV*, 1971.
6. [libbuhlmann](https://github.com/AquaBSD/libbuhlmann), open-source ZH-L16 and gradient factor library.

## Files

| File | Purpose |
|---|---|
| `index.html` | The app, including the planner |
| `manifest.webmanifest`, `icons/` | Install name and icons |
| `sw.js` | Offline support |

To run it locally, open `index.html` in a browser.
