# ZH-L16C Planner

> **For education only. Not for planning or conducting real dives.** This planner is provided as is, without any warranty that it applies the Bühlmann ZH-L16C model and gradient factors correctly or that its schedules would prevent decompression sickness. Do not use its output to plan or execute any dive. Diving is inherently dangerous, decompression diving adds to that risk, and deep dives on several gases including helium add the most. Plan real dives with tested, established tools and the training to use them.

**App:** https://mjwishon.github.io/zhl16c-planner/

An educational Bühlmann ZH-L16C decompression planner with gradient factors for open circuit, CCR, and CCR with open-circuit bailout. It runs entirely in the browser, and nothing is sent anywhere.

## What you can set

- Mode: open circuit, CCR, or CCR with OC bailout
- Depth, bottom time (runtime at the start of the ascent), GF low and GF high
- Last-stop GF (optional, off by default): hold the last stop until the surfacing GF is at or below a third value, e.g. 30/85 with the last stop held to 70
- Up to four more levels (for example 80 m for 20 min, then 60 m for 20 min); an added level's time is the time at depth, and in open circuit each level can have its own gas
- In CCR, optional open-circuit deco gases (you stay on the loop until the first one's switch depth)
- In CCR, optional diluent changes on the ascent (e.g. 21/35 from 36 m, 50 % from 21 m); the loop keeps the setpoint and the new diluent sets the inert gas mix
- In CCR, optional open-circuit oxygen at the last stop, either or both: for the last minutes of the stop, and extra time after the loop clears (each 15 min by default)
- Bottom gas (OC, and the bailout bottom gas) and diluent (CCR) as separate gases, both 12/65 by default, and setpoints (descent, bottom, deco)
- Defaults for every mode: 80 m for 25 min, GF 30/70, GUE standard deco gases (21/35 from 57 m, 35/25 from 36 m, 50 % from 21 m, O2 from 6 m)
- Travel gas for open circuit (on by default: 21/35, switching to the bottom gas at 57 m)
- Gas lists offer GUE standard mixes, or Custom for any O2/He
- Up to five deco or bailout gases, each with a default or custom switch depth
- Descent rate, ascent rate to the first stop, rate between stops, and rate to the surface
- Stop spacing, last stop depth (any depth from 1 to 9 m, default 6 m), and 6 m spacing for stops deeper than 30 m (off by default)
- No stops while a direct ascent stays within GF high (on by default)
- Bottom and deco RMV for gas planning (open circuit and bailout; defaults 15 and 12 L/min)
- Safety stop on no-deco dives, with its depth and time (on by default, 3 min at 5 m)

## What it shows

- Gas alerts (warnings only): ppO2 above 1.4 or END deeper than 40 m for the bottom gas or a diluent flush; above 1.6 or END 40 m for deco gases at their switch depth

- The dive plan as a runtime table (depth, stop time, runtime, gas, setpoint, ppO₂, END, GF at each stop, and Surf GF: the GF you would surface with if you left at that point)
- Gas needed per open-circuit gas, in surface litres
- The profile with the decompression ceiling
- A bar chart of all 16 compartments on surfacing, showing how close each is to its M-value and which one leads
- Nitrogen and helium pressure in each compartment over the dive and after surfacing (line graphs; time after surfacing is adjustable, default 2 hours)

## Install on a phone or desktop

- **iPhone / iPad (Safari):** Share → Add to Home Screen.
- **Android (Chrome):** menu → Install app.
- **Windows / macOS (Chrome or Edge):** install icon in the address bar.

After the first visit it also works offline.

## Method

- ZH-L16C with 16 compartments (compartment 1b), Schreiner equation while moving, exact loading at constant depth. Salt water at 10 m per bar.
- CCR loop: diluent inert gas at ambient pressure minus water vapour minus setpoint.
- END: equivalent narcotic depth with oxygen and nitrogen narcotic and helium not, against air; in CCR from the actual loop gas.
- Levels: level 1 time includes the descent; an added level's time is the time at depth, with the travel added. OC levels can each have their own gas; CCR stays at the bottom setpoint. Moving up to a shallower level adds stops wherever needed so the GF-low ceiling is never crossed; deco is planned from the end of the last level.
- No-deco limit: if a direct ascent keeps every compartment within GF high on surfacing, the plan has no stops (can be switched off).
- First stop: GF-low ceiling at the end of the bottom, rounded up to the stop grid. It moves one stop deeper if the ascent would already violate it (Baker's projected ascent).
- Each stop is held to the next whole minute, then a minute at a time until the ceiling at the next stop's GF is within 1 cm of the next stop. GF rises linearly with depth from GF low at the first stop to GF high at the surface.
- Open circuit and bailout use the richest gas within its switch depth. On the way to the first stop the switch happens at the switch depth; after that, on arrival at a stop.

## References

1. A. A. Bühlmann, *Decompression – Decompression Sickness*, Springer, 1984.
2. E. C. Baker, *Understanding M-values*, 1998.
3. E. C. Baker, *Clearing Up the Confusion About "Deep Stops"*, 1998.
4. E. C. Baker, public-domain decompression programs in Fortran.
5. H. R. Schreiner and P. L. Kelley, "A pragmatic view of decompression", *Underwater Physiology IV*, 1971.

## Files

| File | Purpose |
|---|---|
| `index.html` | The app, including the planner |
| `manifest.webmanifest`, `icons/` | Install name and icons |
| `sw.js` | Offline support |

To run it locally, open `index.html` in a browser.
