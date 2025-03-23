# Speech Processing 

## Documentation on Speech

### Nature of Continuous Speech

Continuous speech is a fluid stream of sounds, with each segment corresponding to a phone—an acoustic feature influenced by factors such as the speaker’s voice and contextual variations. Phones do not exist in isolation but blend seamlessly:

- **Diphones**: Formed by the transition between two consecutive phones.
- **Triphones and Quinphones**: Offer a more detailed context by considering the influence of neighboring phones.

In spontaneous speech, syllables remain stable, though the number of phones can vary due to natural speech patterns. Words limit the possible combinations of phones, aiding in the accurate interpretation of spoken language.

Additionally, fillers like "um," "uh," or breathing sounds are naturally occurring, reflecting hesitation or the speaker’s thought process.

### Types of Speech Sounds

- **Voiced Sounds**: Produced by the periodic vibration of the vocal cords, as in vowels.
  - Male pitch range: 50–250 Hz
  - Female pitch range: 120–500 Hz
- **Unvoiced Sounds**: Created by turbulent airflow through a constriction, like the "s" sound in "six."
- **Plosives**: Produced when air pressure is built up and suddenly released, as in "t" or "p."
- **Mixed Sounds**: Contain both voiced and unvoiced components, like the "z" sound in "is."

### Speech Signal Representation

- **Time-domain representation**: The raw speech signal as an audio waveform, where the signal amplitude varies over time.
- **Frequency-domain representation**: The signal is decomposed into frequency components using the Fast Fourier Transform (FFT).
- **Spectrograms**: A 2D representation of frequency content changing over time, created using the Short-Time Fourier Transform (STFT).

### Speech Features

- **Mel-frequency Cepstral Coefficients (MFCCs)**: Represent the short-term power spectrum of sound, emphasizing perceptually relevant frequencies.
- **Formants**: Resonant frequencies important for vowel recognition and speaker identification.
- **Pitch**: The perceived frequency of speech, crucial for distinguishing speech from non-speech sounds.
- **Energy**: Reflects the loudness of the speech signal, useful for detecting speech pauses or background noise.

### Phonemics and Phonetics

Phonemics is the study of phonemes, the smallest units of speech that carry linguistic meaning. Phonemes are essential for distinguishing words, like the difference between "pet" and "bet," where /p/ and /b/ alter the meaning.

- **Allophones**: Variations of a phoneme that do not change the meaning, such as the difference between the aspirated [ph] in "pit" and unaspirated [p] in "spit."

### MPEG-7 Audio Features

The MPEG-7 standard classifies audio and speech signals, including features for analyzing and categorizing sounds.

#### Audio Spectrum Centroid (ASC)

Measures the logarithmic frequency scale centered around 1 kHz, representing the frequency distribution in the power spectrum. It helps determine whether the sound is perceived as bright or dull.

#### Audio Spectrum Spread (ASS)

Measures the spectral distribution around the ASC, capturing how frequencies spread relative to the centroid. It helps differentiate between noise and speech by analyzing spectral content variance.

---

## Fundamental Technical Components

### 1. Audio Acquisition
The first step in working with speech data is acquiring the audio signal. This can be done using microphones or other recording devices.

### 2. Digitization
Once the speech is recorded, it needs to be converted into a digital format for processing.
- **Sampling**: The continuous audio signal is sampled at regular intervals to create a discrete signal. A common sampling rate for speech is 16 kHz.
- **Quantization**: Each sampled value is then quantized into a finite number of levels, typically represented by a certain number of bits (e.g., 16-bit quantization).

### 3. Preprocessing
Before analyzing the speech data, some preprocessing steps are often necessary:
- **Normalization**: Adjusting the amplitude of the audio signal to a standard level.
- **Noise Reduction**: Filtering out background noise to improve clarity.

### 4. Feature Extraction
Common features include:
- **Time-Domain Features**:
  - **Zero-Crossing Rate (ZCR)**: The rate at which the signal changes sign.
  - **Energy**: The sum of the squares of the signal amplitude.
- **Frequency-Domain Features**:
  - **Spectral Centroid**: The center of mass of the spectrum.
  - **MFCCs**: A representation of the short-term power spectrum of sound.

### 5. Windowing and Framing
Speech signals are non-stationary, meaning their statistical properties change over time. To analyze them effectively, the signal is divided into small overlapping segments called frames (e.g., 20-40 ms). Each frame is multiplied by a window function (e.g., Hamming window) to reduce edge effects.

### 6. Numerical Representation
Once the features are extracted, they are represented as numerical vectors. Each frame of the speech signal is converted into a feature vector, resulting in a sequence of vectors that represent the entire audio signal.

### 7. Analysis and Processing
With the numerical representation of the speech data, various analyses can be performed:
- **Statistical Analysis**: Calculating mean, variance, and other statistical properties of the features.
- **Pattern Recognition**: Identifying patterns or anomalies in the speech signal.

---

## Applications of Speech Processing

1. Speech Recognition (ASR - Automatic Speech Recognition)
2. Speech Synthesis (Text-to-Speech - TTS)
3. Speaker Recognition & Verification
4. Speech Enhancement & Noise Reduction
5. Speech Emotion Recognition
6. Speech-to-Music & Voice Manipulation
7. Language Translation
8. Keyword Spotting & Censorship

### **Application Chosen: Keyword Spotting**
Keyword spotting detects a word or short phrase within a stream of audio. A common use case is the voice activation of virtual assistants.

---

## Challenges & Solutions

### 1. Background Noise
**Challenge:** Environmental sounds like traffic, music, or other people talking can degrade speech quality.

**Solution:**
- Convert speech to frequency domain using FFT.
- Estimate noise profile from initial silent frames.
- Apply spectral subtraction: \( S_{\text{clean}}(f) = S_{\text{noisy}}(f) - N(f) \).
- Convert cleaned frequency components back using IFFT.

### 2. Homophones
**Challenge:** Words that sound the same but have different meanings (e.g., "to" vs. "too") can cause recognition errors.

**Solution:**
- Preprocess speech into sequences of words.
- Expand the keyword set with homophones.
- Use n-grams and beam search to validate context.
- Score candidates based on language rules.

### 3. Speaker Variations
**Challenge:** Different accents, dialects, and speaking styles affect recognition.

**Solution:**
- Convert speech to phonemes instead of raw text.
- Normalize phoneme variations using transformation rules.
- Compute phonetic distance (Levenshtein + Soundex).
- Apply adaptive thresholding for mispronunciations.

### 4. Speech Impairments
**Challenge:** Stuttering or slurred speech can affect recognition.

**Solution:**
- Define a fixed window size (e.g., 3 previous phonemes).
- Move the window and check for repeated sequences.
- Replace excessive phoneme repetitions with a single occurrence.
- Continue sliding until all repetitions are smoothed.

---

## Contributors

- **23011101119 – S K Karisma**
- **23011101128 – Samyuktha R G**
