# Whale Shark Movement Modeling

Analyzed irregular Argos satellite telemetry from whale sharks in the eastern Pacific to examine how environmental and coastal conditions relate to movement persistence. Combined exploratory analysis, state-space modeling, and spatial generalized additive mixed models (GAMMs) in R.

## Approach

- **Data exploration and cleaning:** Examined geographic coverage, observation gaps, location-error classes, and movement speeds. Cleaned the tracking records to obtain 12,157 observations from 60 sharks recorded between 2011 and 2021.
- **Track reconstruction:** Split tracks at gaps longer than seven days and retained segments with at least 20 observations. Fitted state-space models to 58 segments from 32 sharks, accounting for location uncertainty and regularizing trajectories to 24-hour intervals.
- **Movement and environmental data:** Estimated movement persistence from daily trajectories and matched locations to sea surface temperature, bathymetry, distance to coast, and coast type. The final environmental analysis used 1,509 daily observations.
- **Spatial modeling:** Fitted a beta GAMM with a logit link, standardized environmental predictors, a coastal-distance interaction, a two-dimensional spatial smooth, and shark-level random effects. Assessed model adequacy using residual diagnostics and basis-dimension checks.

## Results

The final spatial GAMM explained **85.3% of deviance**, with an **adjusted R² of 0.793**. Higher sea surface temperature, shallower bathymetry, and greater offshore distance were associated with higher movement persistence. The offshore-distance association was weaker near island coasts than continental coasts, while spatial and between-shark variation remained important.

Movement persistence describes directional consistency rather than a complete behavioral classification. Results above follow the final report; presentations document earlier stages of the analysis and may contain different model specifications or findings.

## Code and Reports

- [Final report](whale_shark_final.pdf) — full methods, results, and diagnostics.
- [Exploratory analysis](Whale_shark_EDA.pdf) — initial data exploration.
- [Analysis code](code/) — movement modeling, environmental data construction, and sensitivity analyses.
- [Presentations](presentations/) — progress and final presentation materials.

**Tools:** R, aniMotum, mgcv, sf, dplyr, ggplot2, rerddap, and rerddapXtracto.

The scripts use external telemetry and environmental inputs; the repository does not include all data required to reproduce the analysis.
