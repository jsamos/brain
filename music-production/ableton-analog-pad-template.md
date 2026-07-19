# Stage 1 — Analog Pad

**Part of:** [Music Production Process](ableton-house-production-workflow.md)

Build **House Pad.adg** from Ableton 12 **Analog** on a track named **Pad**. This is the from-scratch version of the synth pad path: one simple pad sound, saved once, ready for writing chords later.

## Examples
- **Analog** with one saw oscillator, slow fade in, slow fade out
- A soft background chord sound under the **Stab**
- No reverb or delay on the device

## Done when
- [ ] **Pad** MIDI track exists
- [ ] **Analog** is loaded on **Pad**
- [ ] Only **Osc1** is making the main sound
- [ ] **Osc1 Shape** is set to saw
- [ ] **Amp1** fades in slowly and fades out slowly
- [ ] **Fil1** is lowered so the sound is soft, not buzzy
- [ ] No device reverb or delay is on the sound
- [ ] One MIDI clip holds a chord for 1-2 bars
- [ ] Preset is saved as **House Pad.adg**

## Build

**Analog from scratch**

1. New MIDI track -> rename it **Pad**.
2. Browser -> **Instruments** -> **Analog** -> drag **Analog** onto **Pad**.
3. In **Analog**, use **Osc1** only for now.
4. Open **Osc1 Shape**.
5. Choose the saw shape: the diagonal ramp icon, usually the third shape in the menu.
6. Leave **Osc1 Octave** at `0`, **Semi** at `0 st`, and **Detune** at `0.00`.
7. Turn **Noise** down or leave it unused.
8. Turn **Osc2** down or leave it unused.
9. Create one MIDI clip with one note or chord held for 1-2 bars.
10. Start with one long `C3` note if chords feel like too much right now.
11. Loop the clip so you can hear changes while you adjust **Analog**.
12. Click **Amp1**.
13. Set **Attack** around `1-3s`.
14. Set **Sustain** high, around `80-100%`.
15. Set **Release** around `2-4s`.
16. Leave **Decay** alone for the first version.
17. Click **Fil1**.
18. Set the filter type to **LP24** if it is not already there.
19. While the clip plays, turn **Fil1 Freq** down from `22.0k` until the pad sounds softer; start around `1k-4k`.
20. If it sounds buzzy, lower **Freq**.
21. If it sounds hidden or dull, raise **Freq** a little.
22. Keep **Reso** low, around `0-10%`.
23. Play the clip and listen for three things: slow fade in, steady held note or chord, slow fade out.
24. Keep the track quieter than **Stab**, about `-6 to -12 dB` lower when both play.
25. Save the preset as **House Pad.adg**.

## Beginner Checks

| Control | Plain meaning | Good first setting |
|---------|---------------|--------------------|
| **Osc1 Shape** | Basic tone source | Saw |
| **Attack** | How slowly the sound starts | `1-3s` |
| **Sustain** | How loud it stays while held | `80-100%` |
| **Release** | How slowly it ends after release | `2-4s` |
| **Fil1 Freq** | Bright vs soft | `1k-4k` |
| **Reso** | Extra whistle near the filter | `0-10%` |

## Reference

A pad is a long background chord sound. For this stage, it should feel soft and steady, not sharp or attention-grabbing. The **Stab** is the shorter, louder chord hit; the **Pad** is the quieter held layer underneath it.
