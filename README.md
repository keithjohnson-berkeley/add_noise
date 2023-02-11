# add_noise
Function to add noise (white,pink,babble) to audio clips.  See the ipynb for example usage.

In a nutshell:

 ```x,sr = add_noise(signal_name, "pink", snr = snr) ```

* signal_name = the name of a sound file (
  *  Mono files only
  *  will be converted to 22050 Hz sampling
*  noise_type = 'pink','white','brown', or the name of a noise soundfile.
  * Some example sound files are provided (via Kamil Wojcicki, UTD, July 2011)
  * Colored noise function from Felix Patzelt (github.com/felixpatzelt)
*  snr = signal to noise ratio
*  target_amp = peak amplitude of the result (default is -2 dB from maximum).
*  results:  
  *  x = audio buffer with noise added (use soundfile.write() [for example] to write as a file.
  *  sr = sampling rate of the sound in the x buffer

### Dependencies:

```
  from pathlib import Path
  import numpy as np 
  import matplotlib.pyplot as plt
  import random
  import colorednoise as cn  # installed from: https://github.com/felixpatzelt/colorednoise
  import librosa
  import soundfile as sf
  import IPython.display as ipd
```

### Example

```
  for signal_name in list(signal_home.glob('*.wav')):  
     for snr in range(-3,4,3):     
         x,sr = add_noise(signal_name, "pink", snr = snr)  
         new_name = (f'{signal_home / signal_name.stem}_pink_snr{snr}.wav')
         print(f'saving {new_name}')
         sf.write(new_name, x, sr, subtype='PCM_16')
```
    
