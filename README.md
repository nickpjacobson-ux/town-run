# Town Run Flow

A live estimate of Uncompahgre River flow through Montrose's "town run," from the Chipeta Lake put-in past the Water Sports Park to the Taviwach Park take-out. No gauge sits on this stretch, so the page figures the flow from state and federal gauges upstream. Every time it loads, your browser pulls fresh readings straight from Colorado DWR and USGS, and it refreshes every 15 minutes while open.

**Not an official gauge.** Look at the river before you put in.

## How the estimate works

```
town run ≈ Road Bridge gauge (DWR UNCBRGCO)
           − Montrose & Delta Canal (MANDCNCO)
           − Stark-Volkman Ditch (4100566A)
           − Loutsenhizer Canal (LOUTCNCO)
```

- The Road Bridge gauge sits below the South Canal outfall, so it already includes the Gunnison water delivered through the Gunnison Tunnel.
- All three diversions between that gauge and Chipeta Lake are metered by DWR.
- The West Canal takes its water off the South Canal by a flume over the river, so it never touches the river and isn't in the sum.
- The likely range assumes each gauge is good to about 6 percent, combined in quadrature.

## What it leaves out

- Dry Cedar Creek, storm drains and irrigation return flows enter in town and aren't measured, so the park probably runs a little above the estimate.
- Travel time: water passing the Road Bridge gauge reaches the park a few hours later.
- The Stark-Volkman Ditch has reported only since September 2026; when it isn't reporting it counts as zero.
- The estimate hasn't been checked against field measurements at the park yet.
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
| 4100566A | Stark-Volkman Ditch | Colorado DWR |
| LOUTCNCO | Loutsenhizer Canal | Colorado DWR |

Readings come from the [DWR telemetry API](https://dwr.state.co.us/rest/get/) and the [USGS Water Data API](https://api.waterdata.usgs.gov/docs/), both provisional. The river course on the map is simplified from USGS NHDPlus flowlines; the South Canal's route between the tunnel and the outfall is schematic.

## Editing

Everything is in `index.html`. Station IDs, the assumed gauge error and the refresh interval are constants near the top of the script.
