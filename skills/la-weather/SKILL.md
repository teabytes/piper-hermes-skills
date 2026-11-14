---
name: la-weather
description: Compare today's and tomorrow's forecast for a named city and choose the drier day for outdoor plans.
version: 1.1.0
---

# City weather

Use `a3_weather_forecast` when available. Pass the requested city with its state
or country if given. Use Los Angeles when no city is given. If multiple cities
match, ask which one the user meant.

On a standard Hermes installation, look up coordinates and the local time zone.
Use the city only in a URL-encoded parameter. Keep the endpoint fixed.

```sh
curl --fail --silent --show-error --max-time 10 --get \
  --data-urlencode 'name=Tokyo' --data-urlencode 'count=10' \
  'https://geocoding-api.open-meteo.com/v1/search'
```

Replace the example city with the city name. If the user specified a country or state, match it against the returned country or administrative area before choosing coordinates. For the example, select Tokyo with country code JP. For Los Angeles you can
use latitude 34.05, longitude -118.24, and time zone America/Los_Angeles.
If the lookup returns multiple exact city names in different regions, ask for
a state or country. Use numeric coordinates from the selected result.

For US locations, request `https://api.weather.gov/points/LATITUDE,LONGITUDE`
with the user agent `Piper CSCI599 weather skill`. Use the `properties.forecast`
URL only if it is an HTTPS URL on `api.weather.gov`. Group the forecast periods
by local date from `startTime`. Daytime temperatures give the high and nighttime
temperatures give the low. Use the highest available precipitation probability
among that day's forecast periods.

For other locations, or if the US forecast is unavailable, use the coordinates
in the following public forecast request. Keep the endpoint fixed.

```sh
curl --fail --silent --show-error --max-time 10 \
  'https://wttr.in/35.69,139.69?format=j1'
```

Replace the example coordinates with the selected city's latitude and longitude
rounded to two decimal places. Read the two local dates from `weather`. Read
each day's `maxtempF` and `mintempF`, and use the highest available
`hourly[].chanceofrain` for rain chance.

Name the resolved city and report the local date, high and low in Fahrenheit,
and the available precipitation or rain chance. For outdoor plans, prefer
the day with the lower chance and explain why. Report a tie if applicable.
Credit the provider and mark missing values as unavailable.
