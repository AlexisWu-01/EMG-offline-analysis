# Preprossing
We first apply a low-pass filter on the data to reduce noise. The thresold was set to 20Hz. Then we apply 6 feature extractions for each channel in each trial.

# Feature Set
cite: https://link.springer.com/article/10.1007/s00779-019-01285-2
| Feature | Math Expression | Meaning | channel1  feature histogram $$\text{all plots can be found in}$$[github](https://github.com/AlexisWu-01/EMG-offline-analysis/tree/main/feature_plots)|
| --- | --- | --- | --- |
| Waveform Length | $$WL = \frac{1}{N} \sum_{i=1}^{N-1} \|x_{i-1}-x_{i}\|$$ | Sum of the absolute differences between adjacent signal point | ![WL Histogram](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_wl.png?raw=true)
| Mean Absolute Value | $$\text{MAV} = \frac{1}{N} \sum_{i=1}^N\|x_i\|$$ | Average of the absolute values of the signal points | ![MAV Histogram](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_mav.png?raw=true)
| Slope Sign Change | $$SSC = \sum_{i=2}^{N-1}f[(x_i-x_{i-1}\times (x_{i+1}-x_i)]$$ $f(x) = 1, \text{ if } x \geq \text{threshold, else }0$ | Counts of times the slope changes sign (indicative of signal frequency) | ![SSC Histogram](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_ssc.png?raw=true)
| Zero Crossing | $$\sum_{i=1}^N[(x_i \times x_{i-1}) < 0]$$ | Number of the times signal crosses zero (also frequency characteristic) | ![ZC Histogram](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_zc.png?raw=true)
| Variance | $$\frac{1}{N-1} \sum(x_i-\bar x)^2$$ | Averaged squared deviation of the data from its mean (measures dispersion) | ![Variance Histogram](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_var.png?raw=true)
|Sample Entropy | N/A | Complexity measure, assessing the regularity and unpredictability of a time-series. Lower values indicate more self-similarity, higher values suggest a higher degree of complexity or irregularity | ![Sample Entropy Histogram](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/feature_plots/ch1_sampen.png?raw=true) |

# Training 
To compare the effectiveness of each feature, we perform training on each of the feature type using the 4 channels. Here are the results:
## Sample Entropy
| Model| Accuracy | F1 Score (each label) | Confusion Matirx|
| --- | --- | ---| ---|
| KNN - Training | 0.55 | 0.75, 0.29, 0.48 |![sampEn KNN train](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/sampen_KNN_train.png?raw=True) |
| KNN - Testing |  0.617| 0.86 0.46  0.55|![sampEn KNN test](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/sampen_KNN_test.png?raw=True) |
| SVM - Training | 0.6 | 0.79 0.34 0.51|![sampEn SVM train](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/sampen_SVM_train.png?raw=True) |
| SVM -Testing| 0.63 | 0.87 0.43 0.58 | ![sampEn SVM test](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/sampen_SVM_test.png?raw=True)|

## Variance 
| Model| Accuracy | F1 Score (each label) | Confusion Matirx|
| --- | --- | ---| ---|
| KNN - Training | 0.85 | 0,8 0.86 0.89 | ![Variance KNN train](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/var_KNN_train.png?raw=True)|
| KNN - Testing | 0.8 | 0.73 0.84 0.85| ![Variance KNN test](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/var_KNN_test.png?raw=True)| 
| SVM - Training | 0.4| 0 0.44 0.54| ![Variance SVM train](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/var_SVM_train.png?raw=True)|
| SVM -Testing| 0.38 | 0.05 0.22 0.5| ![Variance SVM test](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/var_SVM_test.png?raw=True)|

## Waveform Length
| Model| Accuracy | F1 Score (each label) | Confusion Matirx|
| --- | --- | ---| ---|
| KNN - Training | 0.93 | 0.92  0.97 0.92 |![Waveform Length KNN train](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/wl_KNN_train.png?raw=True) |
| KNN - Testing | 0.95 | 0.93 0.99 0.94| ![Waveform Length KNN test](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/wl_KNN_test.png?raw=True) | 
| SVM - Training | 0.92| 0.89 1 0.88| ![Waveform Length SVM train](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/wl_SVM_train.png?raw=True)|
| SVM -Testing| 0.93 | 0.89 0.99 0.92|![Waveform Length SVM test](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/wl_SVM_test.png?raw=True) |

## Mean Absolute Value
| Model| Accuracy | F1 Score (each label) | Confusion Matirx|
| --- | --- | ---| ---|
| KNN - Training | 0.82 | 0.77  0.91 0.79 | ![Mean Absolute Value KNN train](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/mav_KNN_train.png?raw=True)|
| KNN - Testing | 0.84 | 0.77 0.87 0.89|![Mean Absolute Value KNN test](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/mav_KNN_test.png?raw=True) | 
| SVM - Training | 0.75| 0.63 0.9 0.73| ![Mean Absolute Value SVM train](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/mav_SVM_train.png?raw=True)|
| SVM -Testing| 0.5 | 0.25 0.54 0.6|![Mean Absolute Value SVM test](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/mav_SVM_test.png?raw=True) |

## Zero Crossing
| Model| Accuracy | F1 Score (each label) | Confusion Matirx|
| --- | --- | ---| ---|
| KNN - Training | 0.8 | 0.75  0.97 0.73 | |
| KNN - Testing | 0.87 | 0.8 0.99 0.81| | 
| SVM - Training | 0.85| 0.8 1 0.79| |
| SVM -Testing| 0.875 | 0.81 0.99 0.83| |


# Final Model

From the above experiments, we learned that the `wl`(waveform length) and `zc` (zero crossing)
# Feature selection
Zero crossing and Waveform Length

| Model| Accuracy | F1 Score (each label) | Confusion Matirx|
| --- | --- | ---| ---|
| KNN - Training | 0.88 | 0.86  0.93 0.87 | ![Final Model KNN train](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/wl%7Czc_KNN_train.png?raw=True)|
| KNN - Testing | 0.9 | 0.86 0.97 0.87| ![Final Model KNN test](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/wl%7Czc_KNN_test.png?raw=True)| 
| SVM - Training | 0.9| 0.88 0.97 0.87|![Final Model SVM train](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/wl%7Czc_SVM_train.png?raw=True) |
| SVM -Testing| 0.94 | 0.92 0.99 0.92|![Final Model KNN test](https://github.com/AlexisWu-01/EMG-offline-analysis/blob/main/result_plots/wl%7Czc_SVM_test.png?raw=True) |