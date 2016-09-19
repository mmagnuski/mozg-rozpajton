mne python reymontówka
----------------------

## intro (day 1)
Topics:
* environment setup
* loading and viewing files
* mne data containers
* reading events, montage
* filtering
* epoching
* viewing and rejecting epochs
* setting and interpolating bad channels

expected time: `1 - 2 hours`

## ica (day 1)
Topics:
* running ica
* inspecting component maps and properties
* inspecting component timeseries
* rejecting and labeling components
* evaluating effects of removing component

bonus: (day 2)
* ica on multiple files
* corrmap to auto-select eye components

expected time: `45 minutes - 1 hour`
               + `20 - 35 minutes` for bonus

## erp (day 1 / day 2)
* erps are plain-simple: `erp_face = epochs['face'].average()`
* erp visualizations
* dictionary comprehensions for erp conditions, concatenating erps
* peak finding

expected time: `45 minutes - 1 hour`

## stats (day 2)
* performing cluster-correction
* visualizing effects

expected time: `45 minutes - 1 hour`

## time-frequency (day 2)
* calculating frequency representation (welch)
* time-frequency representation with morlet wavelets
* vis
* stats

expected time: `~ 1 hour`

## bonus materials (day 2)
If we have enough time for this:
* automatic rejection with `autoreject`
* using Annotations
* time-decoding
* writing an analysis script

