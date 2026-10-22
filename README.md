# SP-1 stem packer/player utility
A single-page web tool for making and previewing stem files for the SP-1 stem player created by teenage engineering.
Intended to be used with https://solderless.engineering/ to upload Stems onto your device.

This webpage takes up to four stems, made from WAV, MP3 or most other audio files, and packs them into one 8-channel WAV the SP-1 can play. It also opens existing 8-channel stem files so you can preview them with SP-1 style faders.

All conversions/playback runs within your browser.

## Usage
 
Visit https://dombeef.github.io/te-sp-1-stem-packer-player/stem-packer-player.html to use this webpage, or download the html file within the repository and open that in a modern web browser.
 
### Packing stems
 
1. **Load audio.** Drop files anywhere on the page or over a specific stem, press **import**, or use **+ add** on a single stem.
2. **Arrange.** Each column is one stem, which can contain multiple files which will get mixed together. You can drag a file to another column.
3. **Preview.** Press play and use the faders to check the balance.
4. **Export.** Enter a name and an optional BPM, then press **build wav**. The BPM is added to the filename, e.g. `song_120bpm.wav`.
5. **Load the stem onto your SP-1** with the stem loader at [solderless.engineering](https://solderless.engineering/). The loader needs desktop Chrome or Edge.

### Playing stems
 
Import or drop an 8-channel stem file and it splits it back into four stems. The name and BPM are read from the filename. This can be used to either play back a previously created stem, or edit and rearrange the channels within the stem.
 
The faders and keys only change the live preview. The exported file is always at full level.
 
## Output format
 
Signed 24-bit PCM, 48 kHz, 8 channels, WAV format that is compatible with solderless.engineering.
 
| Channel | Stem |
| --- | --- |
| 1 | Stem 1, left |
| 2 | Stem 1, right |
| 3 | Stem 2, left |
| 4 | Stem 2, right |
| 5 | Stem 3, left |
| 6 | Stem 3, right |
| 7 | Stem 4, left |
| 8 | Stem 4, right |
 
- MP3 and mono files are converted to stereo.
- Everything is resampled to 48 kHz.
- All stems start at 0:00. Shorter stems and empty slots are padded with silence.
- With **prevent clipping** on, a stem whose mix peaks above 0 dBFS is turned down just enough to fit.
- WAV files are limited to 4 GB, which is about 62 minutes at this format.
## Import rules
 
- **One 8-channel file** is split into stems 1–4 by channel pair. Stems that are completely silent stay empty.
- **Any other files** are sorted by name and spread one per stem. A 5th file mixes into stem 1, a 6th into stem 2, and so on.
- Importing replaces whatever is loaded. **+ add** on a column adds to just that stem while keeping the other files untouched.
