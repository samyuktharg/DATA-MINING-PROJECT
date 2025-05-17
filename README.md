# Keyword Spotting System – Speech Processing Project

A speech processing system for detecting specific keywords in audio streams, with a focus on robustness to accents and variations in pronunciation.

---

## Project Focus

**Application:** Keyword Spotting  
**Use Case:** Crime & Threat Detection (e.g., "kill", "shoot", "bomb")

This system identifies predefined keywords in surveillance or conversational audio, useful in security and forensic domains.

---

## Technical Overview

### Audio Processing Pipeline

1. **Audio Acquisition**: 16 kHz mono recordings using `librosa`
2. **Feature Extraction**: 20 MFCC coefficients
3. **Normalization**: Z-score with epsilon for numerical stability
4. **Phoneme Transformation**: Set 1st MFCC to its mean
5. **Pattern Matching**: DTW with normalized Euclidean distance
6. **Sliding Window Detection**:
   - `window_size_factor = 2`
   - `step_size = 5`
   - DTW threshold = `2.1`
   - Minimum detection gap = `0.5 sec`
7. **Visualization**: Waveform, spectrogram, DTW distance

---

## Data

- **Keyword Audio**: `"kill.wav"` (clean American accent)
- **Test Audio**:
  - “They were planning to kill the witness before the trial.” (American & British)
  - “They started to shoot without warning.” (Control case)

---

## Evaluation

- **True Positives:** Accurate keyword hits
- **False Positives:** Noise-triggered matches
- **Robustness:** Handles accents and minor speed variations
- **Efficiency:** Adjustable step/window sizes for performance tuning

---

## 📈 Results

| Test Audio                                  | Detection |
|--------------------------------------------|-----------|
| “...to kill the witness...” (American)     | ✅        |
| “...to kill the witness...” (British)      | ✅        |
| “...to shoot without warning...”           | ❌        |

---

## Future Improvements

- Adaptive thresholding per keyword/accent
- Phoneme-level enhancements
- Deep learning (CNN/RNN) integration
- Real-time processing and GUI support
- Multi-keyword detection

---

## Contributors

- **S K Karisma** – 23011101119  
- **Samyuktha R G** – 23011101128  
