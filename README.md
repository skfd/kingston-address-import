# kingston-address-import

The **Kingston city checkout** of the address-import family — city #9,
scaffolded 2026-08-16 by the breadth-first onboarding loop (engine
`future-work/multi-city/onboarding-queue.md`). Status: **onboarding**. No
proposal published, no uploads made; the config is a first draft for
conflation baseline runs.

The pipeline lives in the engine repo,
[`address-importer-friend`](https://github.com/skfd/address-importer-friend)
(see its README for setup). This repo carries only Kingston's `config.toml`,
credentials (`.env.*`, gitignored, from the `.example` files), and — locally,
gitignored — `data/` with the OSM extract and `data/kingston/tool.db`.

```bash
cd ../address-importer-friend
python run.py --city-dir ../kingston-address-import
```

Source data: City of Kingston civic address points via the sibling
[`ontario-address-changes`](https://github.com/skfd/ontario-address-changes)
tracker (`data/kingston/kingston.db`, 77,386 active rows / 45,387 civic
addresses at snapshot 47, 2026-08-15 — the freshest source in the
portfolio). The 2026-08-12 portfolio survey put the gap in the high-80s
percent.

Traits (details in config comments): the highest unit share in the family
(40.0%, collapsed to civic); stable `ADDRESS_ID` key; ALL-CAPS abbreviated
typed streets; `FULL_ADDRESS` appends the unit (Guelph trap);
`ELECTORAL_DISTRICT_NAME` declared as ward; MUNICIPALITY constant
(undeclared for-cause). Tiles subdivide 42 uniquely-named "Neighbourhood
Boundaries" polygons (99.98% point coverage) — and the source rows carry a
matching `NEIGHBOURHOOD` prop, a future QA cross-check. Kingston is a
separated city inside Frontenac County.

Entry state probed 2026-08-16 (`onboarding/entry-state-2026-08-16.json`):
**greenfield** — CanVec 6.0 seed (893 of 1,617 sampled), Matthew Darwin's
2018 rename retag, and `zzptichka`'s properly-tagged 2018 Ontario Building
Import (buildings, with addresses riding along). `DenisCarriere` touched
city data back in 2014 ("source = City of Kingston", 468 changes).
Currently active: `trigonometric` addressing via StreetComplete surveys
(260 sampled elements in 2025, changesets into 2026-03). An import target;
contacts: trigonometric (active), zzptichka (experienced importer,
Ontario-wide), Matthew Darwin. Convention: `addr:city=Kingston`,
`addr:province=Ontario` (86 vs 5).

Before any production upload: wiki proposal page, forum announcement, and
feedback window per the
[OSM Import Guidelines](https://wiki.openstreetmap.org/wiki/Import/Guidelines)
— Toronto's [`IMPORT_PROPOSAL.mediawiki`](https://github.com/skfd/toronto-2-address-import/blob/main/IMPORT_PROPOSAL.mediawiki)
is the template.

MIT licensed.
