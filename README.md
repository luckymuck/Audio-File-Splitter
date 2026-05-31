# Audio File Splitter
Vinyl &amp; Tape Audio File Splitter is a single-file browser tool for:
- splitting recordings into individual tracks using:
  - detection methods,
  - a list, or
  - album-based metadata information;
- tagging metadata
  - from MusicBrainz, Discogs, or user information,
  - bpm detection,
  - song recognition with third-party connection (Shazam, AcoutID, AudD)
- exporting as:
  - Zip of MP3 files,
  - WAV, or
  - FFmpeg scripts to run locally.

# Use and Features
## 1. Add an audio file.
(MP3, WAV, FLAC, OGG, M4A). 

## 2. Waveform viewer and split editor. 
- A zoomable view of the audio file.  
- Splits can be added, deleted, and moved.
- Audio can be played/stopped from any location with right-click.
- Optional view as spectrogram to better spot song changes.
- Optional view of audio signals of energy, bmp, brightness, crowd detection, beat density.

## 3. Detection.
### A. Detection based upon silence.
Looks for "silence" of a minimum length below a certain volumn threshold.  Default theshholds based upon album recording type.
### B. Detection using Multi-Signal Analysis.
For live shows or DJ sets additional signal of energy, BMP, color, crowd detection, and beat detection signals may help.
### C. Apply splits from a manual list.
Paste a list of tracks and times.  Accepts several formats.
### D. Apply splits and metadata based upon information of individual song tracks.
Look-up albums using MusicBrainz or Discogs. (Time results are often off by a few seconds.)
All metadata search uses the [MusicBrainz](https://musicbrainz.org) public API (CC0 licence). No key required. Requests identify themselves as `VinylSplitter/1.0` per MusicBrainz's usage guidelines.
### E. Add BPM metadata to tracks.

## 4. Identify unknown tracks and add metadata.
Using your own API key, sending an audio sample to [Shazam via RapidAPI](https://rapidapi.com/apidojo/api/shazam), AcoustID, or [AudD](https://audd.io) 

## 5. Review and tagging of identified tracts.
- Manually add track information.  
- Test play each tract.
- Review proposed split locations.

## 6. Export 
### Formats
- **ZIP (MP3)** process the file into individual tracks for a single download.
- **FFmpeg Script** .sh (macOS/Linux): Place in the same folder as your audio file, run chmod +x script.sh && ./script.sh. Produces fully-tagged MP3s. Get FFmpeg ↗ (FFmpeg is faster than processing in browswer.)
- **FFmpeg Script** .bat (Windows): Place in the same folder as your audio file, then double-click or run from a command prompt. Requires FFmpeg on your PATH.  
- **WAV (Lossless)**: Exports each track as a WAV file. Use Mp3tag or Kid3 to add ID3 tags afterwards.
- **Cue Sheet**: A single .cue file describing all split points — use with your audio player or ripper.
- **Metadata JSON**: A structured JSON file with all track metadata for use in custom workflows.

  ## Screenshots
  ### Before a file is added, one column
<img width="484" height="980" alt="Screenshot1" src="https://github.com/user-attachments/assets/c9469ce4-017e-42de-8513-b8783c583176" />

### File loaded, signal analysis performed, one column
<img width="498" height="2226" alt="Screenshot3" src="https://github.com/user-attachments/assets/0d14d6b4-b265-4dfa-beee-b8666a1a5ef2" />

### File loaded, signal analysis performed, track detection via Shazam in process, two columns
<img width="900" height="2000" alt="Screenshot2" src="https://github.com/user-attachments/assets/540cb2e6-29ca-406c-bffe-100262581bda" />

## Multi-Signal Analysis
- **Silence / Energy** — Detects track boundaries by finding quiet regions where the audio amplitude drops below a fixed threshold. Gaps with deeper silence and lengths matching the expected inter-track gap score higher; a built-in beat guard suppresses false positives caused by drum solos or sparse sections.
- **BPM / Rhythm** — Estimates tempo and uses changes to detect tracks.
- **Spectral Centroid** — Measures the average "brightness" of the audio on each side of a gap. A significant shift in the centre of spectral mass suggests a change in instrumentation or production style between two songs.
- **Crowd Noise** — Attempts to identify typical crowd noise which may otherwise conceal track changes in live recordings.
- **Beat Denisity** — Measures number of beats with a gap indicating a track change.

