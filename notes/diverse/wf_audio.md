# Arbejd med lyd

## Calculating a rolling window statistic
Omdan en audiofil til en såkaldt envelope, hvor datapunkterne bliver smoothed ud, så der ikke kommer så mange "takker" på grafen.

```python
# Audio is a Pandas DataFrame
print(audio.shape)
# (n_times, n_audio_files)

# Smooth our data by taking the rolling mean in a window of 59 samples
window_size = 50
windowed = audio.rolling(window=window_size)
audio_smooth = windowed.mean()
```

```python
audio_rectified = audio.apply(np.abs)
audio_envelope = audio_rectified.rolling(50).mean()
```

## Tempogram
```python
import librosa as lr
audio_tempo = lr.beat.tempo(audio, sr=sfreq, hop_length=2**6, aggregate=None)
```

## Spectrogram
FFT / Fouruer Transform

```python
from librosa.core import stft, amplitude_to_db 
from librosa.display import specshow

# Beregn STFT
HOP_LENGTH = 2**4
SIZE_WINDOW = 2**7
audio_spec = stft(audio, hop_length=HOP_LENGTH, n_fft=SIZE_WINDOW)

# Convert into decibels for visualization
spec_db = amplitude_to_db(audio_spec)

# Visualize
specshow(spec_db, sr=sfreq, x_axis='time', y_axis='hz', hop_length=HOP_LENGTH)
```

Beregn spectal features
```python
# Calculate the spectral centroid and bandwidth for the spectrogram
bandwidths = lr.feature.spectral_bandwidth(S=spec)[0]
centroids = lr.features.spectral_centroid(S=spec)[0]

# display these features on top of the spectrogram
ax = specshow(spec, x_axis='time', y_axis='hz', hop_length=HOP_LENGTH)
ax.plot(times_spec, centroids)
ax.fill_between(times_spec, centroids - bandwidths / 2, centroids + bandwidths / 2, alpha =0.5)
```