# OctoMedia

Multimedia standard library for [OctoFlow](https://github.com/octoflow-lang/octoflow) — audio, image, and video processing in pure `.flow`.

## Modules

### Audio
| Module | Description |
|--------|-------------|
| `pcm.flow` | PCM audio buffers — create, mix, resample, normalize, concat, fade |
| `oscillator.flow` | Waveform generators — sine, square, saw, triangle, white noise |
| `envelope.flow` | ADSR envelope generator with presets (piano, pad, pluck, perc) |
| `fft.flow` | Cooley-Tukey radix-2 FFT, IFFT, STFT, magnitude/phase/power spectrum |
| `audio_fx.flow` | Biquad filters (LP/HP/BP/notch), delay, reverb, distortion, chorus, compressor |
| `mixer.flow` | Multi-track mixer with volume, pan, mute/solo, stereo mixdown, master gain |
| `wav.flow` | WAV file parser — read RIFF PCM headers and sample data |
| `wav_encode.flow` | WAV file writer — 8-bit and 16-bit PCM, mono/stereo |

### Image
| Module | Description |
|--------|-------------|
| `bmp.flow` | BMP file parser and encoder |
| `gif.flow` | GIF decoder with LZW decompression |
| `gif_encode.flow` | GIF encoder with LZW compression and animation support |
| `gif_encode_gpu.flow` | GPU-accelerated GIF encoding via Loom |
| `image_filter.flow` | Convolution filters — blur, sharpen, edge detect, emboss |
| `image_transform.flow` | Resize (nearest/bilinear), rotate, scale, translate |
| `image_util.flow` | Image utilities — crop, flip, brightness, contrast, grayscale |
| `color_space.flow` | Color space conversion — RGB/YUV/YCbCr/XYZ/LAB/CMYK, Delta-E |
| `ttf.flow` | TrueType font parser — glyph outlines, metrics, rasterization |

### Video
| Module | Description |
|--------|-------------|
| `mp4.flow` | MP4/ISO-BMFF container parser |
| `avi.flow` | AVI container parser |
| `h264.flow` | H.264/AVC bitstream parser — NAL units, SPS/PPS, slice headers |
| `timeline.flow` | Video timeline — tracks, clips, transitions, keyframes, frame blending |

### Players
| Module | Description |
|--------|-------------|
| `audio_player.flow` | PCM playback engine — play/pause/stop/seek, loop, speed, fade, region |
| `image_viewer.flow` | Image viewer — zoom, pan, fit modes, rotation, gallery navigation |
| `video_player.flow` | Frame-by-frame video player — timeline sync, A/V sync, frame stepping |
| `playlist.flow` | Playlist management — add/remove, shuffle, repeat modes, next/prev |
| `media_player.flow` | Unified player — combines audio + video + playlist, subtitles, mute |

### GUI Editing Tools
| Module | Description |
|--------|-------------|
| `audio_editor.flow` | Waveform editor — selection, copy/cut/paste, gain/fade/reverse/normalize, undo, zoom, markers, effects chain |
| `image_editor.flow` | Layer-based image editor — brush/eraser/fill/eyedrop, layers with opacity/blend modes, selection, zoom/pan, flatten |
| `video_editor.flow` | Timeline editor — tracks, clip management (add/remove/move/trim/split), snap modes, in/out points, preview transport, markers, render queue, undo |

### Demos
| File | Description |
|------|-------------|
| `gif_decode_demo.flow` | GIF decoding demonstration |

## Tests

Every module has a corresponding `test_*.flow` file. 26 test files, 280+ test cases.

## Usage

```flow
use "pcm"
use "oscillator"
use "fft"

// Generate a 440Hz sine wave
let buf = pcm_create(44100.0, 1.0, 1.0)
osc_generate_into(buf, 440.0, 0.0, OSC_SINE)

// FFT analysis
let mut re = []
let mut im = []
let n = fft_forward(pcm_samples(buf), re, im, 1024.0)
```

## License

MIT — Part of the [OctoFlow](https://github.com/octoflow-lang/octoflow) ecosystem.
