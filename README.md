# Feature Set
| Feature | Math Expression | Meaning | ch1 histogram |
| --- | --- | --- | --- |
| Waveform Length | $$WL = \frac{1}{N} \sum_{i=1}^{N-1} \|x_{i-1}-x_{i}\|$$ | Sum of the absolute differences between adjacent signal point | ![WL Histogram](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_wl.png?raw=true)
| Mean Absolute Value | $$\text{MAV} = \frac{1}{N} \sum_{i=1}^N\|x_i\|$$ | Average of the absolute values of the signal points | ![MAV Histogram](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_mav.png?raw=true)
| Slope Sign Change | $$SSC = \sum_{i=2}^{N-1}f[(x_i-x_{i-1}\times (x_{i+1}-x_i)]$$ $f(x) = 1, \text{ if } x \geq \text{threshold, else }0$ | Counts of times the slope changes sign (indicative of signal frequency) | ![SSC Histogram](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_ssc.png?raw=true)
| Zero Crossing | $$\sum_{i=1}^N[(x_i \times x_{i-1}) < 0]$$ | Number of the times signal crosses zero (also frequency characteristic) | ![ZC Histogram](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_zc.png?raw=true)
| Variance | $$\frac{1}{N-1} \sum(x_i-\bar x)^2$$ | Averaged squared deviation of the data from its mean (measures dispersion) | ![Variance Histogram](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_var.png?raw=true)
|Sample Entropy | N/A | Complexity measure, assessing the regularity and unpredictability of a time-series. Lower values indicate more self-similarity, higher values suggest a higher degree of complexity or irregularity | ![Sample Entropy Histogram](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_sampen.png?raw=true) |
