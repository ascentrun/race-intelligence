# Ascent Running – Race Intelligence

A single-page race analysis tool for Sportraxs-powered events. Load any race by ID and instantly explore leaderboard splits, segment performance, elevation profiles, and athlete climbing vs descending tendencies.

**Live app:** [ascentrun.github.io/race-intelligence](https://ascentrun.github.io/race-intelligence)

---

## How to use

### 1. Load a race
Enter the **Sportraxs race ID** in the top input field and select how many athletes to analyse — Top 10, Top 25, Top 50, or All. Click **LOAD**.

Data is cached in your browser after the first load, so subsequent visits are instant. Use the **↻** refresh button to force a fresh fetch from the API.

### 2. Race overview
Once loaded you'll see:

- **Leaderboard** — overall finishing positions with split times at each checkpoint
- **Halfway split** — the checkpoint closest to half the total race distance, showing who led at the midpoint and their position change to the finish
- **Pacing ratio** — each athlete's second-half time relative to their first half (a ratio below 1.0 means they ran the second half faster)

### 3. Segment analysis
Each checkpoint-to-checkpoint segment is listed with:

- **Segment time and speed (km/h)** for every athlete
- **Elevation gain/loss** calculated from the full course profile (not just checkpoint altitude difference), giving accurate cumulative climb and descent per section
- **VAM** (vertical metres per hour) on climbing segments
- **Segment rank** — athletes sorted fastest to slowest for that section
- **CP position** — each athlete's overall position at the end checkpoint

Segments are automatically classified as **climbing** (>55% of vertical movement is upward) or **descending**, colour-coded orange and green respectively.

### 4. Climbing vs Descending spectrum
Each athlete is ranked within every climbing and descending segment. Their **average rank** across all climb segments and all descent segments is used to place them on a spectrum from pure climber to pure descender.

**Highlight cards:**

| Card | Meaning |
|------|---------|
| Best Climber | Lowest average rank across uphill segments (min 50% of climbs completed) |
| Best Descender | Lowest average rank across downhill segments (min 50% of descents completed) |
| Climbing Biased | Better average rank on climbs than on descents |
| Descending Biased | Better average rank on descents than on climbs |
| Most Consistent | Smallest difference between climb and descent average rank |

The spectrum bar shows where each athlete sits between the two extremes. The `↑` and `↓` values show their average rank on uphills and downhills respectively.

---

## Notes

- Race IDs are found in the Sportraxs platform URL for the event
- All data is fetched directly from the Sportraxs API — no backend required
- The app runs entirely in the browser; no data is sent anywhere except back to the Sportraxs API
- Cached data is stored in your browser's localStorage and is not shared between devices or users

---

Built by [Ascent Running](https://ascentrunning.co.za)
