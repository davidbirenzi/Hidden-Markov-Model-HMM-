# Hidden Markov Model - Human Activity Recognition

Individual assignment project for recognizing human activities from smartphone sensor data.

## Project Structure

```
Hidden Markov Model/
├── standing/          # Training data - standing activity (samples 01-10)
├── walking/           # Training data - walking activity (samples 01-10)
├── jumping/           # Training data - jumping activity (samples 01-10)
├── still/             # Training data - still activity (samples 01-10)
├── test_data/         # Unseen test data (samples 09-10 from each activity)
├── hmm_activity_recognition.ipynb   # Main notebook with HMM implementation
└── README.md
```

## Data Collection

- **App used:** Sensor Logger
- **Sensors:** Accelerometer (x, y, z) and Gyroscope (x, y, z)
- **Sampling rate:** ~100 Hz (one sample every 0.01 seconds)
- **Activities:** Standing, Walking, Jumping, Still
- **Duration:** 5-10 seconds per recording
- **Samples:** 10 recordings per activity (40 total recordings, 80 CSV files)

## Train/Test Split

- **Training:** Samples 01-08 from each activity folder (32 recordings)
- **Testing:** Samples 09-10 in `test_data/` folder (8 unseen recordings)

## How to Run

1. Install required packages:
   ```
   pip install numpy pandas matplotlib seaborn scipy scikit-learn jupyter
   ```

2. Open and run the notebook:
   ```
   jupyter notebook hmm_activity_recognition.ipynb
   ```

## HMM Implementation

- **Hidden States:** standing, walking, jumping, still
- **Observations:** 8 features per time window (6 time-domain + 2 frequency-domain)
- **Algorithms:** Viterbi (decoding) and Baum-Welch (training)
- **Window size:** 1 second (100 samples at 100 Hz)

## Features Extracted

| Feature | Domain | Description |
|---------|--------|-------------|
| accel_mean | Time | Mean accelerometer magnitude |
| accel_variance | Time | Variance of accelerometer magnitude |
| accel_std | Time | Standard deviation |
| sma | Time | Signal Magnitude Area |
| corr_xy | Time | Correlation between x and y axes |
| gyro_mean | Time | Mean gyroscope magnitude |
| dominant_freq | Frequency | Dominant frequency from FFT |
| spectral_energy | Frequency | Total spectral energy from FFT |
