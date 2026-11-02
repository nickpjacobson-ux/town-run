# Town Run Flow

A live estimate of Uncompahgre River flow through Montrose's "town run," from the Chipeta Lake put-in past the Water Sports Park to the Taviwach Park take-out. No gauge sits on this stretch, so the page figures the flow from state and federal gauges upstream. Every time it loads, your browser pulls fresh readings straight from Colorado DWR and USGS, plus NOAA's river forecast and radar rain, and it refreshes every 15 minutes while open.

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
- **Stark-Volkman Ditch** has live telemetry only since September 2026. When it has no reading in the last 24 hours, the live estimate uses its typical diversion for the month from DWR HydroBase daily records, 2020–2025 (about 20–25 cfs May–September, 11 in October, 0 November–March).
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

## Storm outlook

Summer storms raise the town run mostly through creeks Ridgway Reservoir doesn't control. Cow Creek (107 sq mi, joining 2.4 km below the dam) is the largest and is gauged; Horsefly Creek (45 sq mi) and Dry Cedar Creek (24 sq mi) join below every gauge. The Outlook section combines three things, drawn in park time (about 2 hours after water passes the Road Bridge gauge):

1. **Cow Creek routing (next 3–5 hours).** Colona follows Cow Creek and the dam release about 2 hours later (coefficients 0.91 and 0.87), and Road Bridge follows Colona about an hour after that (coefficient 1.0). These were fit hour by hour on 72 summer storm rises (July–October 2016–2026) and tested leaving out one year at a time. While Cow Creek was rising, the average miss 3 hours ahead at Road Bridge fell from 46 cfs (assuming no change) to 36 cfs; 1 hour ahead, from 30 to 19. Timing holds up better than size: the real rise came in at a median 0.8 times the routed rise, and 2 times in 3 between 0.1 and 2 times, so the page draws the routed line at 0.8 with that range. Replaying big storms: on July 29, 2026, with Cow Creek at 406 cfs in the 8 PM hour, the routing gave about 1,060 cfs at Road Bridge for 11 PM (range 810–1,490); the gauge read 1,040.
2. **CBRFC forecast (next 3 days).** NOAA's Colorado Basin River Forecast Center forecasts the Road Bridge gauge (UNBC2) with forecast rain. The page shifts it to match the latest reading, easing the shift out with a 12-hour time constant, then runs it through the same sum as the estimate with the canals held at their latest readings. The Cow Creek chart shows CBRFC's Cow Creek forecast (COWC2) against the gauge, and the page says when the creek is running well above or below it.
3. **Radar rain and the chance of a rise.** NOAA's MRMS radar-only rainfall, averaged over each creek's drainage (NLDI basins), is mapped for the last 1, 6 and 24 hours.
   - *Radar can't size a rise.* A rain-runoff model for Cow Creek (hourly radar for every wet spell of July–October 2021–2026, runoff share set by the last 72 hours of rain, a fitted unit hydrograph, and a correction from the creek's own response) was tested a year at a time. Six hours ahead it missed by 10.4 cfs on average in rainy hours against 11.5 for assuming no change, and at the start of the 24 biggest rises it called a rise of 20+ cfs for none of them, even when tested on the years it was fit to and with the basin's wettest radar cell in place of its average. Radar shows about the same rain for storms that do nothing and storms that send Cow Creek up hundreds of cfs, and it missed the rain entirely before 9 of 53 rises.
   - *Radar does tell the odds.* A logistic model fit hour by hour on the same record gives the chance of a 20+ cfs Cow Creek rise within 12 hours from three radar numbers: the last 6 hours of rain, the 66 hours before them, and the last hour. Tested a year at a time it ranked hours well (area under the ROC curve 0.76, against 0.69 with 6-hour rain alone), and its odds held up through about 40%: hours given 20–35% saw a rise 32% of the time. Above that it ran high, so the page maps its chance onto what actually happened in that test (0.42 → 42%, 0.59 → 52%, 0.80 → 59%) and shows it as a percentage to the nearest 5%, topping out at 60%. The 72-hour rain matters: at any 6-hour total, the wetter half of past hours had 1.5 to 2.5 times the odds.
   - When the chance is 15% or more, the outlook shades the hours a rise would reach the park, with the typical size of past rises after similar rain (for example, after 4 mm or more in 6 hours, a median 93 cfs at Cow Creek, about 68 at the park, peaking at the gauge 2–6 hours after the radar's latest hour). 6-hour totals of 4 mm (0.16 inch) or more show in green in the rain table.

### Tried and dropped

Each was tested on July–October 2021–2026 in 6-hour periods, leave-one-year-out (a coarser test than the page's hourly chance model, which scores 0.76 on its own), for the chance of a 20+ cfs Cow Creek rise and for its size (area under the ROC curve; 0.5 is a coin flip). Rain and hail came for every rainy period, the day before each rise and a fifth of dry periods; lightning for the rainy periods and the days before rises.

| Signal (each with 72-hour rain) | Odds: AUC | Size of the rise |
|---|---|---|
| Radar-only rain (what the page uses) | 0.68 | not predictable |
| Gauge-corrected rain (MRMS MultiSensor QPE, Pass 2) | 0.68 (false calls 43% vs 51%) | not predictable |
| Radar hail size (MESH, 6-hour max) | 0.64 | not predictable |
| Lightning (NLDN cloud-to-ground density) | 0.65 | not predictable |
| All of them blended | 0.68 | not predictable |

- The two rain sources differed most in October storms, when radar-only rain read about a third of the gauge-corrected amount. Gauge-corrected rain's small gain doesn't justify the scheduled server job the page would need to get it live (the browser-friendly radar service offers only radar-only rain).
- Hail and lightning mark the most violent summer cells (July 29, 2026 had both), but most big rises, and all the October ones, had neither.
- NOAA's National Water Model: its v3.0 retrospective, driven by observed rain, rose 0.4 cfs or less on Cow Creek (reach 9769820) in all 21 storms of 2021–2022, which rose 20–123 cfs at the gauge. On November 1, 2026 its live forecast stayed flat at 23 cfs while the creek rose past 200.
- Extrapolating Cow Creek's own early rise didn't help either: after a 20+ cfs jump, the median further rise was 6 cfs.

Reservoir operators cut the release in 21 of 72 past storms, which shrinks a rise. The routing picks up a cut once it shows at the dam gauge; the CBRFC forecast may not. Neither the routing nor the forecast is an official forecast for the park.

## What it leaves out

- Storm drains and irrigation return flows in town aren't counted, so the park may run a little above the estimate after rain or heavy irrigation. Neither are Horsefly and Dry Cedar creeks' storm runoff; the page flags rain on them instead.
- Travel time: the readout uses the latest readings, so it runs about 2 hours ahead of the park. The Outlook chart is drawn in park time.
- No independent flow measurements exist at the park. Colorado River Watch volunteer flow values in the Water Quality Portal for River Bottom Park and the Mayfly site track the Colona gauge almost exactly (median ratio 1.01), even on days when the canals were moving hundreds of cfs, so they don't work as a check.
- The canal stations stop reporting in winter; the page then shows the last complete reading.

## History charts

The history section shows the last 7 days (hourly), 90 days, 1 year or 5 years (daily). For the daily views the page also pulls DWR HydroBase's official daily diversion records for the M&D Canal (WDID 4100545), Loutsenhizer Canal (4100537) and Stark-Volkman Ditch (4100566):

- Where a record exists, it replaces the canal's telemetry. The records are reviewed, and they correct readings that stuck while a canal shut down (in March 2022 the M&D telemetry sat at 130 cfs for days, more than the river carried, while the official record shows the canal off). M&D and Loutsenhizer records run through October 2025 so far.
- Stark-Volkman's records skip days the ditch was off, so between its first and last record a missing day counts as off. In July 2024, for example, it was off from July 8 to July 22, which the typical value would have missed by about 20 cfs.
- After the records end, the canal stations go quiet each winter. With the tunnel off (South Canal under 100 cfs), the page takes the canals as off, which DWR's records show for every December through February.
- Days when the canal gauges read more than the river carries, even allowing for gauge error, are left blank rather than plotted as an impossible flow.

## Data sources

| Station | What it is | Agency |
|---|---|---|
| 09147025 | Uncompahgre River below Ridgway Reservoir (release) | USGS |
| COWCRKCO | Cow Creek near Ridgway Reservoir | Colorado DWR |
| 09147500 | Uncompahgre River at Colona (reference) | USGS |
| UNCUPSCO | Uncompahgre River upstream of South Canal | Colorado DWR |
| SOUCANCO | South Canal near Montrose (at the tunnel) | Colorado DWR |
| UNCBRGCO | Uncompahgre River at Uncompahgre Road Bridge | Colorado DWR |
| MANDCNCO | Montrose & Delta Canal | Colorado DWR |
| 4100566A | Stark-Volkman Ditch (telemetry); WDID 4100566 (HydroBase records) | Colorado DWR |
| 4100545, 4100537 | M&D and Loutsenhizer canals (HydroBase daily diversion records, for history) | Colorado DWR |
| LOUTCNCO | Loutsenhizer Canal | Colorado DWR |
| 382711107520101 | Dry Cedar Creek near mouth (field measurements, 1991–2001) | USGS |
| UNBC2, COWC2 | River forecasts for Road Bridge and Cow Creek | NOAA CBRFC |
| MRMS QPE | Radar-only rainfall, 1-, 6- and 24-hour totals | NOAA |

Live readings come from the [DWR telemetry API](https://dwr.state.co.us/rest/get/) and the [USGS Water Data API](https://api.waterdata.usgs.gov/docs/), both provisional. Forecasts come from the [National Water Prediction Service API](https://api.water.noaa.gov/nwps/v1/docs/) and radar from NOAA's [MRMS image service](https://mapservices.weather.noaa.gov/raster/rest/services/obs/mrms_qpe/ImageServer). Drainage outlines are from the USGS [NLDI](https://waterdata.usgs.gov/blog/nldi-intro/) and creek lines from the National Hydrography Dataset. The webcam is the City of Montrose's [Water Sports Park](https://www.cityofmontrose.org/613/Water-Sports-Park) stream. The river course on the map is simplified from USGS NHDPlus flowlines; the South Canal's route between the tunnel and the outfall is schematic.

## Editing

Everything is in `index.html`. Station IDs, the assumed gauge errors, the Dry Cedar Creek and Stark-Volkman typical values, the gauge-check ranges, the storm-routing coefficients (`ROUTE`), the forecast blending and the radar thresholds are constants near the top of the script.
