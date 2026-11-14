# Piper Hermes skills

This Hermes skill tap contains a city weather workflow for CSCI 599
Assignment 3. It uses Open-Meteo for location lookup, the National Weather
Service for US forecasts, and wttr.in for international forecasts. It requires
network access and a terminal with curl. It needs no account or API key.

Add this tap to Hermes with
`hermes skills tap add teabytes/piper-hermes-skills`. Install the skill with
`hermes skills install teabytes/piper-hermes-skills/la-weather`.

Ask Hermes to compare today and tomorrow in Tokyo, Japan and suggest the drier
day for an outdoor activity. The answer should show both local dates,
temperatures, the available rain chance, and the forecast source.
