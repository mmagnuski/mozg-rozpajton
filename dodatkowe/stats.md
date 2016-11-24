:construction:

# Cluster-correction

in `mne.stats` you'll find:

function name | what it does
--- | ---
`permutation_cluster_1samp_test()` | paired contrasts with spatial prior.
`permutation_cluster_test()` | F-contrasts with spatial prior.
`spatio_temporal_permutation_cluster_1samp_test()` | paired contrasts without spatial prior.
`spatio_temporal_permutation_cluster_test()` | F-contrasts without spatial prior.

*spatial prior* means here predefined region of interest (one sensor for example).
