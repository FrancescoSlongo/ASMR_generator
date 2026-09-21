# Hush

Hush is a browser app that generates ASMR audio in real time. Nothing is recorded: every sound is synthesized from noise, filters and random timing, then placed around the listener's head with binaural (HRTF) panning.

It is a single HTML file with no dependencies and no build step.

> Use headphones. The 3D placement only works when each ear gets its own channel.

## What it can do

| Source | How it is made |
|---|---|
| Noise colours | White, pink, brown, grey, blue and violet, with tone and "waves" controls |
| Whispering | Noise-excited formant filters (source-filter speech model), wordless |
| Tapping | Modal synthesis: an impulse exciting three resonators (wood, plastic, glass) |
| Brushing | Filtered noise with stroke envelopes and spectral sweeps |
| Rain | Poisson-distributed drops over a filtered noise bed |
| Fire | Brown-noise rumble with heavy-tailed, clustered crackles |
| Water drops | Impact click plus a rising Minnaert bubble tone |
| Squishy | Squeezed filtered noise with bubble pops and sticky micro-clicks |
| Crinkles and cracks | Crinkly wrapper, cracking ice (dispersive chirps) or snapping twigs |
| Birds | Repeated motifs of frequency sweeps, whistles and trills |
| Crickets | Tone pulses; chirp rate follows Dolbear's law for the chosen temperature |
| Cat purring | ~25 Hz pulse train in alternating exhale and inhale phases |
| Frogs | Pulse-gated sawtooth through a throat resonance, with answering croaks |
| Singing bowl | Beating inharmonic modes, struck or sung |
| Kalimba | Tine modes (fundamental and 6.27× overtone), wandering melodies |
| Harp | Karplus–Strong plucked strings playing rolled chords |
| Wind chimes | Free-free tube modes struck by gusty wind |
| Warm pad | Detuned sawtooth chords that glide into each other |
| Mouth sounds | Tongue clicks, lip smacks and wet micro-click clusters |

All instruments share one key and scale, chosen at the top of the Instruments section. Sounds are grouped into sections (Ambience, Touch and objects, Animals, Instruments, Mouth and voice, Patterns), shown one at a time through a sticky Section menu that marks sections with something playing with a green dot; and a Now playing section lists every sound that is on, with its volume, an off button and the patterns driving it. Each source can be switched on and off, and has its own volume, direction, distance and movement pattern: still, circling, ear-to-ear or drifting. Each also has its own high-pass and low-pass filter, with 12 or 24 dB/octave slopes, adjustable resonance and a live frequency-response plot.

The **Register pattern** panel records a movement you make with a slider, or generates one (sine, triangle, ramps, square, pulse, breathing, and random shapes such as smooth random, steps, random walk, 1/f drift, Ornstein–Uhlenbeck and bursts), and loops it onto any setting of any sound, for example the direction of the whisper or the cutoff of a filter. Patterns are saved in the browser. A top-down map shows where every sound is at each moment, and you can drag a sound's dot to move it; its Direction and Distance sliders follow.

## Running it

Because it is a static page, you can double-click `index.html`. Some browsers restrict features on `file://` pages, so the more reliable option is a small local server:

```bash
cd hush
python3 -m http.server 8000
# then open http://localhost:8000
```

Click **Start listening**. Browsers only allow audio to start after a user gesture, so nothing plays before that click.

It works in current versions of Chrome, Edge, Firefox and Safari (14.1 or later).

## Project layout

```
hush/
├── index.html            the whole app: markup, styles and audio engine
├── README.md             this file
└── docs/
    └── how-it-works.md   technical guide to the audio engine
```

The technical guide explains the scheduler, every generator, the spatial audio and how to add a new sound: [docs/how-it-works.md](docs/how-it-works.md).
