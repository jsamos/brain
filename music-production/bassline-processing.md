# Step-by-Step Guide to Processing Basslines

## Initial Sound Manipulation

Once you have a bassline loaded onto a MIDI track, begin manipulating the sound using the synthesizer or plugin parameters. For example, with a basic FM house bass in Ableton, adjust the device parameters—especially the filter cutoff frequencies—to shape the sound.

When shaping the filter, listen to the bass with the kick playing so you can hear how they sit together in the mix.

## Adding Swing

To add groove and a more rhythmic feel, apply swing to the bassline. In Ableton, select a swing amount that complements the rest of your track. Note that even without pressing the "commit" button for grooves, the swing is applied to the track.

## Applying Sidechain Compression

Sidechain compression creates space for the kick drum by reducing the bassline's volume whenever the kick hits. The kick track is the sidechain input; the compressor on the bass reacts to that signal so the kick and bass do not clash.

Use Ableton's built-in **Compressor** (or **Glue Compressor**) on the bass track—not a third-party plugin.

### Turn on sidechain

1. Put **Compressor** on the **bass track** (not the kick).
2. **Expand the sidechain panel** — click the **triangle / wedge** on the **left edge** of the device title bar. The panel stays hidden until you do this.
3. Click **`External`** so it is **highlighted/on** (yellow/lit). On some Live versions this button is labeled **`Sidechain`** instead of **`External`**; same function. Until this is on, the compressor only reacts to the bass itself, not the kick.
4. Under **`External Source`** (sometimes labeled **`Audio From`**), choose your **kick track**.
5. Set the tap point — usually **`Post FX`**, or **`Pre FX`** if you want a cleaner trigger unaffected by other kick processing.

Selecting a track in the dropdown without turning **`External`** on does nothing. Both steps are required.

The **headphones icon** between the External and EQ sections auditions the sidechain trigger only; useful while dialing in settings.

### Starting settings (house-style ducking)

| Control | Starting point | Why |
| --- | --- | --- |
| **Threshold** | Around **−25 dB to −15 dB** | Lower = more ducking when the kick hits |
| **Ratio** | **4:1** to **8:1** | Strong enough to clear space without sounding broken |
| **Attack** | **0.01 ms** (fast) | Bass drops right as the kick lands |
| **Release** | **80–200 ms** | Match your groove; shorter = tighter pump, longer = smoother tail |
| **Knee** | **Soft** | Often smoother on bass |
| **Dry/Wet** | **100%** to start | Pull down toward **50–70%** if it feels too aggressive |

### Tuning it

1. Play kick + bass together.
2. Watch the **Gain Reduction** meter on the Compressor — aim for roughly **3–6 dB** of reduction on each kick hit (more for heavy pump, less for subtle clearance).
3. If bass and kick still clash: lower **Threshold** or raise **Ratio**.
4. If pumping is too obvious: raise **Threshold**, lower **Ratio**, or reduce **Dry/Wet**.

**Glue Compressor** uses the same sidechain routing (`External` / `Sidechain` → kick track). Some people prefer its sound for musical pumping.

## Individual Processing

### Delay

Add a subtle delay to introduce a sense of space. Keep the dry/wet mix mostly dry with just a hint of the wet signal, and experiment with the delay width for additional effect.

### Saturation

Apply saturation to add subtle harmonics and flavor. Using Ableton's Saturator with presets such as "warm-up lows" can be a good starting point. Use the dry/wet mix sparingly to avoid over-distorting the low end, as heavy distortion can ruin the bass sound.

### EQ (Equalization)

Use EQ to clean up the low end by cutting frequencies below 120 Hertz. Consider a subtle roll-off of some mid-range frequencies if necessary. However, avoid removing desirable high and mid frequencies if the bass already sounds balanced. Corrective EQ for the kick and bass is best handled during the mixing stage rather than in sound design.

### Making the Bass Mono

Use Ableton's Utility plugin with the "base mono" preset to make frequencies below a certain threshold (for example, 120 Hz) mono. This centers the low frequencies in the stereo image, which is often desirable for basslines. Apply delay before this process if needed, ensuring that the low frequencies remain mono.

### Modulation (Using LFO)

Introduce subtle modulation to create movement and uniqueness. Use Ableton's Max for Live LFO device to map modulation to various parameters, such as the filter frequency. Keeping the LFO rate relatively low and the depth very subtle adds interesting character to the sound over time. Experiment with applying LFOs to multiple parameters.
