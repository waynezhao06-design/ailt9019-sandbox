---
title: Tokyo Weather Snapshot
observed_at: 2026-09-08T21:30+09:00
location: Tokyo, Japan
coordinates: [35.6895, 139.6917]
timezone: Asia/Tokyo
source: Open-Meteo Forecast API
source_url: https://api.open-meteo.com/v1/forecast
tags: [weather, tokyo, open-meteo]
---

# Tokyo Weather - 2026-09-08 21:30 JST

A single coordinate-pinned call to the Open-Meteo forecast API.

## Current conditions

| Metric | Value |
| --- | --- |
| Temperature | 25.3 C |
| Feels like | 31.5 C |
| Humidity | 97% |
| Cloud cover | 100% |
| Precipitation | 1.30 mm |
| Wind | 2.9 km/h |
| Weather code | 63 (moderate rain) |

## 3-day outlook

| Date | High | Low | Rain chance | Code |
| --- | --- | --- | --- | --- |
| Tue 2026-09-08 | 28.5 C | 22.4 C | 88% | 63 |
| Wed 2026-09-09 | 29.7 C | 19.7 C | 99% | 63 |
| Thu 2026-09-10 | 22.2 C | 19.1 C | 86% | 63 |

WMO code 63 = moderate rain. Rain every day; Wednesday is the worst
(near-certain rain, 29.7 C high), Thursday cools by about 7 C.

## Raw API response

Pretty-printed for readability - the API returned it on a single line.

```json
{
  "latitude": 35.7,
  "longitude": 139.6875,
  "generationtime_ms": 68.3748722076416,
  "utc_offset_seconds": 32400,
  "timezone": "Asia/Tokyo",
  "timezone_abbreviation": "GMT+9",
  "elevation": 40.0,
  "current": {
    "time": "2026-09-08T21:30",
    "interval": 900,
    "temperature_2m": 25.3,
    "relative_humidity_2m": 97,
    "apparent_temperature": 31.5,
    "weather_code": 63,
    "wind_speed_10m": 2.9,
    "precipitation": 1.30,
    "cloud_cover": 100
  },
  "daily": {
    "time": ["2026-09-08", "2026-09-09", "2026-09-10"],
    "temperature_2m_max": [28.5, 29.7, 22.2],
    "temperature_2m_min": [22.4, 19.7, 19.1],
    "precipitation_probability_max": [88, 99, 86],
    "weather_code": [63, 63, 63]
  }
}
```

## Notes on retrieval

- **Coordinates, not place name.** Earlier lookups using the name "Tokyo"
  resolved to Shikinejima, an island ~180 km south and administratively part
  of Tokyo prefecture. That gave a misleading 27 C with 40 km/h winds.
  Pinning to `35.6895, 139.6917` avoids it.
- **One retry.** The first request returned
  `{"error":true,"reason":"The service is overloaded"}`; the identical
  request succeeded ~seconds later.
- **No cross-check.** A second source was not consulted, per the preference for
  a single fast call on simple lookups.
