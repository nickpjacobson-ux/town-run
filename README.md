# Town Run Flow

A live estimate of Uncompahgre River flow through Montrose's "town run," from the Chipeta Lake put-in past the Water Sports Park to the Taviwach Park take-out. No gauge sits on this stretch, so the page figures the flow from state and federal gauges upstream. Every time it loads, your browser pulls fresh readings straight from Colorado DWR and USGS, and it refreshes every 15 minutes while open.

**Not an official gauge.** Look at the river before you put in. The page embeds the City of Montrose's live park webcam (it loads when you tap it) so you can check the waves by eye.

## How the estimate works

```
town run ≈ Road Bridge gauge (DWR UNCBRGCO)
           − Montrose & Delta Canal (MANDCNCO)
           − Stark-Volkman Ditch (4100566A; typical value when silent)
           − Loutsenhizer Canal (LOUTCNCO)
           + Dry Cedar Creek (typical value; not gauged)
```

- The Road Bridge gauge sits below the South Canal outfall, so it already includes the Gunnison water delivered through the Gunnison Tunnel.
- The three diversions between that gauge and Chipeta Lake are metered by DWR.
- The West Canal takes its water off the South Canal by a flume over the river, so it never touches the river and isn't in the sum.
- **Dry Cedar Creek** enters between Chipeta Lake and the park. Its typical flow comes from 34 USGS measurements near its mouth (1991–2001): 16.5 cfs (sd 6.9) from April through October and 2.2 cfs (sd 0.5) from November through March. The page uses the irrigation-season value while the tunnel runs (South Canal over 100 cfs), easing to the winter value over the 7 days after it shuts off. Lateral piping since then may have lowered it.
- **Stark-Volkman Ditch** has live telemetry only since September 2026. When it has no reading in the last 24 hours, the page uses its typical diversion for the month from DWR HydroBase daily records, 2020–2025 (about 20–25 cfs May–September, 11 in October, 0 November–March).
- The City of Montrose's park page publishes an estimate built the same way (Road Bridge − M&D − Loutsenhizer), without Dry Cedar Creek or the Stark-Volkman Ditch.

## The likely range and the gauge check

Each gauge is assumed good to about 10 percent (one standard deviation) while the tunnel runs and 15 percent when it's off; errors are combined in quadrature with the uncertainty of the typical values. That makes the likely range roughly a 2-in-3 interval.

The figures come from comparing gauges with nothing major entering or leaving between them, using daily data for 2016–2026:

| Comparison | Median | Normal (5th–95th percentile) | Implied error per gauge |
|---|---|---|---|
| DWR above South Canal ÷ Colona | 0.86 | 0.65–1.03 | ~7% May–Sep, ~10% winter |
| (Road Bridge − above South Canal) ÷ South Canal, steady tunnel over 200 cfs | 0.76 | 0.54–0.94 | ~10% |
| Road Bridge ÷ Colona, tunnel off (only 50 days) | 1.12 | 0.66–1.23 | ~16% |

The page's gauge check recomputes these comparisons from the last 24 hours of hourly readings and flags any that fall outside the normal range, since then the gauges don't add up and the estimate is less certain than its range shows.

## What it leaves out

- Storm drains and irrigation return flows in town aren't counted, so the park may run a little above the estimate after rain or heavy irrigation.
- Travel time: water passing the Road Bridge gauge reaches the park a few hours later.
- No independent flow measurements exist at the park. Colorado River Watch volunteer flow values in the Water Quality Portal for River Bottom Park and the Mayfly site track the Colona gauge almost exactly (median ratio 1.01), even on days when the canals were moving hundreds of cfs, so they don't work as a check.
- The canal stations stop reporting in winter; the page then shows the last complete reading.

## Data sources

| Station | What it is | Agency |
|---|---|---|
| 09147025 | Uncompahgre River below Ridgway Reservoir (release) | USGS |
| 09147500 | Uncompahgre River at Colona (reference) | USGS |
| UNCUPSCO | Uncompahgre River upstream of South Canal | Colorado DWR |
| SOUCANCO | South Canal near Montrose (at the tunnel) | Colorado DWR |
| UNCBRGCO | Uncompahgre River at Uncompahgre Road Bridge | Colorado DWR |
| MANDCNCO | Montrose & Delta Canal | Colorado DWR |
| 4100566A | Stark-Volkman Ditch (telemetry); WDID 4100566 (HydroBase records) | Colorado DWR |
| LOUTCNCO | Loutsenhizer Canal | Colorado DWR |
| 382711107520101 | Dry Cedar Creek near mouth (field measurements, 1991–2001) | USGS |

Live readings come from the [DWR telemetry API](https://dwr.state.co.us/rest/get/) and the [USGS Water Data API](https://api.waterdata.usgs.gov/docs/), both provisional. The webcam is the City of Montrose's [Water Sports Park](https://www.cityofmontrose.org/613/Water-Sports-Park) stream. The river course on the map is simplified from USGS NHDPlus flowlines; the South Canal's route between the tunnel and the outfall is schematic.

## Editing

Everything is in `index.html`. Station IDs, the assumed gauge errors, the Dry Cedar Creek and Stark-Volkman typical values, the gauge-check ranges and the refresh interval are constants near the top of the script.
