# Feature Selection
| Feature | Waveform Length | Mean Absolute Value| Slope Sign Change | Zero Crossing| Variance| Sample Entropy|
| --- | --- | --- | --- | --- | --- | --- |
| Math Expression| $$WL = \frac{1}{N} \sum_{i=1}^{N-1} \|x_{i-1}-x_{i}\|$$ | $$\text{MAV} = \frac{1}{N} \sum_{i=1}^N\|x_i\|$$ | $$SSC = \sum_{i=2}^{N-1}f[(x_i-x_{i-1}\times (x_{i+1}-x_i)]$$ $f(x) = 1, \text{ if } x \geq \text{threshold, else }0$| $$\sum_{i=1}^N[(x_i \times x_{i-1}) < 0]$$| $$\frac{1}{N-1} \sum(x_i-\bar x)^2$$| NA|
| Meaning| Sum of the absolute differences between adjacent signal point| Average of the absolute values of the signal points| Counts of times the slope changes sign (indicative of signal frequency)| Number of the times signal crosses zero (also frequency characteristic)| Averaged squared deviation of the data from its mean (measures dispersion)| Complexity measure, assessing the regularity and unpredictability of a time-series. It quantifies the likelihood that runs of patterns that are close for M observations remain close on subsequent incremental comparisons. Lower values of SampEn indicate more self-similarity or regularity in the data, while higher values suggest a higher degree of complexity or irregularity|
| ch1 histogram | <img src="https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_wl.png?raw=true" width="300"/> | <img src="https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_mav.png?raw=true" width="300"/> | <img src="https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_ssc.png?raw=true" width="300"/> | <img src="https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_zc.png?raw=true" width="300"/> | <img src="https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_var.png?raw=true" width="300"/> | <img src="https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_sampen.png?raw=true" width="300"/> |


<head>
    <script type="text/javascript" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML"></script>
</head>
<table border="1">
    <thead>
        <tr>
            <th>Feature</th>
            <th>Waveform Length</th>
            <th>Mean Absolute Value</th>
            <th>Slope Sign Change</th>
            <th>Zero Crossing</th>
            <th>Variance</th>
            <th>Sample Entropy</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Math Expression</td>
            <td>$$WL = \frac{1}{N} \sum_{i=1}^{N-1} \|x_{i-1}-x_{i}\|$$</td>
            <td>\(\text{MAV} = \frac{1}{N} \sum_{i=1}^N\|x_i\|\)</td>
            <td>\(SSC = \sum_{i=2}^{N-1} \mathbf{1}[(x_i-x_{i-1})(x_{i+1}-x_i) < 0]\)</td>
            <td>\(ZC = \sum_{i=1}^N \mathbf{1}[(x_i \times x_{i-1}) < 0]\)</td>
            <td>\(\text{VAR} = \frac{1}{N-1} \sum_{i=1}^N(x_i-\bar x)^2\)</td>
            <td>\(\text{SampEn} = -\ln\left(\frac{A}{B}\right)\)</td>
        </tr>
        <tr>
            <td>Meaning</td>
            <td><!-- Your description for Waveform Length --></td>
            <td><!-- Your description for Mean Absolute Value --></td>
            <td><!-- Your description for Slope Sign Change --></td>
            <td><!-- Your description for Zero Crossing --></td>
            <td><!-- Your description for Variance --></td>
            <td><!-- Your description for Sample Entropy --></td>
        </tr>
        <tr>
            <td>ch1 histogram</td>
            <td><img src="https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_wl.png?raw=true" width="500"/></td>
            <td><img src="https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_mav.png?raw=true" width="500"/></td>
            <td><img src="https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_ssc.png?raw=true" width="500"/></td>
            <td><img src="https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_zc.png?raw=true" width="500"/></td>
            <td><img src="https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_var.png?raw=true" width="500"/></td>
            <td><img src="https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_sampen.png?raw=true" width="500"/></td>
        </tr>
    </tbody>
</table>
