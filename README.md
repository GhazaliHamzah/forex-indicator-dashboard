# Forex Indicator Dashboard

A single-screen dashboard for MetaTrader 5 traders that shows indicator
readings for one instrument at a time. This repository holds the first design
draft.

**Status:** design draft. All prices and readings in it are sample data for
layout review, not live market figures.

## What the dashboard shows

| Section | Content |
|---|---|
| Stochastic by timeframe | %K and %D at 14, 5, 3 for M5, M15, M30, H1, H4, D1, W1 and MN, each labelled Overbought, Oversold or Neutral |
| Pivot, support and resistance | Pivot point with R1 to R3 and S1 to S3, the current price placed between them, and the distance in pips to each level |
| Weekly market trend | Uptrend, Downtrend or Sideways on W1, the four readings behind it, and the last 12 weekly closes |

The dashboard shows indicator readings only. It gives no buy or sell calls,
entries or targets.

## Repository layout

```
index.html         Standalone dashboard page. Open it in any browser.
design/
  canvas.json      Canvas index: title and artboard frame
  Main.dc.html     The dashboard artboard (layout, sample data, logic)
```

`index.html` is a single self-contained file with no build step. Its sample
data sits in the `DATA` object at the top of the script, and the overbought
and oversold levels are the `OVERBOUGHT` and `OVERSOLD` constants.

The files in `design/` are canvas design sources. They open on the design
canvas they were made on and do not run as a standalone web page.

## Assumptions still to confirm

| Item | Draft assumption |
|---|---|
| Overbought and oversold levels | 80 and 20, read on %K |
| Pivot formula | Classic, from the previous day's high, low and close |
| Weekly trend rule | Close above the 20-week average and 20-week above the 50-week is an uptrend; both below is a downtrend; otherwise sideways |
| Instruments | EURUSD, GBPUSD, USDJPY and XAUUSD as examples |
| Layout | One instrument per screen |

## Planned build

1. A bridge Expert Advisor in MT5 that reads indicator values and sends them to a server
2. A cloud API that stores the readings
3. This dashboard, connected to live readings
4. Login and subscription billing
