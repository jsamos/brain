# Ableton Analog: acid / tek “siren” style sound (step-by-step)

**Goal:** Build a hypnotic, filter-driven line in the spirit of hard tek and acid: resonant low-pass, envelope on the cutoff, then saturation, delay, and reverb.

**Instrument:** This is a **synth patch**, not a sampled acoustic instrument. In Ableton you use **Analog** (or any subtractive synth with a resonant filter and a filter envelope) on a **MIDI track**, with **audio effects after** the synth in the same device chain.

**Signal chain:**

```text
[MIDI Track]  →  Analog  →  Saturator  →  Delay  →  Reverb
```

**Context:** A short [r/ableton thread](https://www.reddit.com/r/ableton/comments/1snuxcu/synth_sound_help_please/) discussed a similar atmospheric tek sound; this note turns that advice into a reproducible Analog workflow and adds concrete UI guidance for Live’s Analog layout.

---

## 1. MIDI track and test clip

1. In **Session View**, right-click an empty slot in a MIDI column → **Insert MIDI Track**, or menu **Create → Insert MIDI Track** (macOS shortcut **Cmd + Shift + T**).
2. Click an **empty clip slot** on that track to create a MIDI clip; **double-click** the clip to open the **MIDI Note Editor** at the bottom.
3. Draw a few **short notes** around **C4–C5** so you can hear changes while tweaking.
4. Press **space** to play.

---

## 2. Load Analog

1. Open the **Browser** (**View → Show Browser**, or **Cmd + Option + B** on macOS).
2. Search **Analog**; under **Instruments**, drag **Analog** onto the **track title bar**, or **double-click** Analog with the track selected.
3. **Analog** appears in **Device View** under the session, in that track’s horizontal device chain.

---

## 3. How Analog is organized (shell map)

Analog is one tall device made of **stacked sections**. Expand or collapse sections with the **triangles** next to their titles.

Rough **top-to-bottom** map:

```text
┌─────────────────────────────────────┐
│  Global / Quality / Unison / Glide  │  ← voices, mono, glide
├─────────────────────────────────────┤
│  Osc 1  │  Noise  │  Osc 2           │  ← start with Osc 1 only
├─────────────────────────────────────┤
│  Fil 1  │  Fil 2                   │  ← main acid filter
├─────────────────────────────────────┤
│  Amp 1  │  Amp 2                   │
├─────────────────────────────────────┤
│  Central display                     │  ← Global, or Fil/Osc detail (ADSR, Freq Mod…)
├─────────────────────────────────────┤
│  (same center area when Fil selected)│  ← filter ADSR graph + Freq Mod / Res Mod
└─────────────────────────────────────┘
```

The **center display** changes depending on what you last selected (for example **Global** vs **Fil 1** vs **Osc 1**). **Envelope amount to filter cutoff** is **not** on the oscillator pages. **Click Fil 1** (orange / highlighted) so the middle panel shows **Filter 1**: filter **ADSR** (Attack, Decay, Sustain, Release), then **Freq Mod** and **Res Mod** underneath.

---

## 3a. Typical default shell (read your meters, not assumptions)

After load, many presets or the default shell look **“open and clean”**: both oscillators on, **Fil 1 Freq** fully clockwise (**~22 kHz**), **Reso** at **0%**. That is a valid starting device, but it will **not** sound like acid yet because the filter is barely closing and resonance is off.

If your Analog matches that state:

1. **Osc 2**  
   Click **Osc 2** so its active state turns **off** (inactive / gray), or pull **Osc 2** level to silence. Keep **Osc 1** on **Saw** at a sensible level.

2. **Fil 1 → Freq**  
   Drag **Freq** **left** from the fully open position into a **dark** range. A practical first pass is roughly **hundreds of Hz to a couple of kHz** on the readout; by ear, long notes should sound **dull**, not silent.

3. **Fil 1 → Reso**  
   Raise **Reso** from **0%** in **small steps** until the cutoff **emphasizes** and **rings** a little when notes play. If the filter **self-oscillates** into constant squeal, reduce **Reso** slightly.

4. **Center display**  
   Click **Fil 1** (not **Global**) so the **central panel** shows Filter 1: **filter ADSR** and **Freq Mod** / **Res Mod**.

5. **Scroll only if needed**  
   If the center panel is cropped, **scroll inside the Analog device** in the chain until you see **Freq Mod**. The control that moves cutoff with the envelope is **Freq Mod → Env**, not a knob on **Osc 1** or **Osc 2**.

6. **Amp 1 Level**  
   If output is quiet (for example **Amp 1** at **−18 dB**), that is fine while designing; raise level later after the motion reads clearly.

7. **Optional motion for lines**  
   In **Global**, try **Voices** at **1** for strict mono lines. On the right, enable **Glide (Gli)** with a **short** glide time and use **Legato** if you want slide only between overlapping notes.

After **Freq down**, **Reso up**, and **Osc 2 off**, you are in the right region before touching the filter envelope.

---

## 4. Oscillator 1 as the only source

1. **Osc 1:** waveform **Saw** (classic acid). **Square** is valid for a harder, hollower line once saw is working.
2. **Osc 1** level: high enough that the track meter moves when the clip plays.
3. **Osc 2:** off or silent so one oscillator feeds the filter.

---

## 5. Filter 1: resonant low-pass

1. **Fil 1** active (yellow / on).
2. **Type:** **LP24** or **LP12** (**LP24** is sharper).
3. **Freq:** closed enough that the raw tone is dark (see §3a).
4. **Reso:** high enough to whistle at the edge of **Freq**, without runaway squeal (see §3a).
5. **Drive** (if shown on Fil 1): a little extra grit is optional; you can also wait for **Saturator**.

**Fil 2 / routing:** If **Fil 2** is off and you use a **To F2** style control, prefer a simple path while learning: one active filter, predictable volume. If something sounds missing or phase-weird, revisit routing after the patch speaks on **Fil 1** alone.

Next: **§6** sets the **filter ADSR** and the **Freq Mod → Env** amount in the **Fil 1** center panel (not on **Osc 1** / **Osc 2**).

---

## 6. Filter envelope and “Env → cutoff” (squelch)

### Where “Env → filter frequency” is (and where it is not)

- **It is filter-stage modulation, not oscillator modulation.** Anything routed into **Fil 1** (including **Osc 1** or **Osc 2** when on and sent to **F1**) is shaped by the **same** Filter 1 envelope and **Freq Mod** amounts.
- **Do not look under Osc 2** (or Osc 1) for envelope-to-cutoff. Oscillator panels choose waveform, pitch offsets, level, and routing to **F1** / **F2**; they do not host **Freq Mod → Env**.

**Exact path on screen**

1. In the shell, click **Fil 1** so it is selected (highlighted). The **large center panel** is now the Filter 1 editor.
2. At the top of that panel you see the **filter envelope** with **Attack**, **Decay**, **Sustain**, **Release** (often with a small envelope graphic).
3. Lower in the same panel, open the **Freq Mod** (frequency modulation) section.
4. In **Freq Mod**, the parameter named **Env** is **envelope → filter cutoff** (how many semitones or units the filter envelope pushes the cutoff). Increase **Env** in the **positive** direction until each note **opens bright** then **falls darker**. Example starting range: a moderate value such as **2–6** is common; exact numbers depend on **Freq**, **Reso**, and note range.
5. **Res Mod → Env** is **envelope → resonance**. Keep that **low** until cutoff motion is stable; envelope on resonance gets sharp quickly.

After this step, play the clip: you should hear **motion per note**, not a static bright saw.

### If you use Filter 2

Click **Fil 2** in the shell; the center panel switches to **Filter 2’s** own ADSR and **Freq Mod → Env**. That is a **separate** cutoff modulation path from Fil 1.

---

## 7. Mono and glide (optional, very “tek”)

**Where this lives:** The **big black center panel** has tabs **Global** and **MPE** on its **top left**. **Voices**, **Glide Mode**, **Quick Routing**, **Keyboard**, and related settings are on the **Global** tab. That is the same physical panel as the **Fil 1** editor, but a **different page** — switch with the tabs (or, if you still see only the filter, click **Fil 1** off by selecting **Global** there, or click **Volume** on the far-right strip, or the **Quick Routing** diagram at the top of the black area until **Global** shows).

**Voices**

Set **Voices** to **1** in the **Keyboard** section of the **Global** tab when you want glide and pitch motion to **reuse one voice** (polyphony above **1** often makes **Time** feel ineffective because new notes can **steal** a fresh voice at target pitch).

**Glide shell (`Gli`) vs Glide Mode**

- **Orange far-right column:** **Gli** turns glide on or off; **Time** (%) and **Legato** live here. Widen the device if this column is clipped.
- **Black Global tab (still left of that orange column):** **Glide Mode** — **Const** keeps glide duration **similar** across interval sizes; **Prop** scales duration with interval so **small** steps can make **Time** feel pointless. Pick **Const** unless you want proportional behavior.

**Legato — two ways to hear glide**

- **Test A — overlap + Legato on:** In the piano roll, overlap notes so the next starts **before** the previous ends. With **Legato** on, glide only runs on those overlaps (Ableton’s Analog wording).
- **Test B — gaps + Legato off (recommended default here):** Set **Voices** to **1**, **Gli** on, **Glide Mode** to **Const**, **Legato** **off**. Play a line with a **small gap** between notes (e.g. **C3** then **C4**), then sweep **Time** from low to high on **wide** intervals. This is the setup that was easier to hear and control in practice.

Turn **Uni** off while you verify glide so stacked detunes do not mask the pitch slide.

You can do **§8** (effects) without changing **Voices** or glide; this step only changes how successive notes **connect**.

---

## 8. Effects (same track, same device row)

Signal order is left to right: **Analog → Saturator → delay → reverb**.

### Saturator

1. In the **Browser**, search **Saturator**.
2. **Drag Saturator** so it sits **after Analog** (to the **right** of the Analog box in the device row).
3. Open Saturator. In the **curve / model** menu, start with **Soft Sine** or **Analog Clip** (smooth grit); avoid the harshest fold shapes until you know the sound.
4. Turn **Drive** up until you hear extra grit; back off if it fizzes or gets too loud.

### Delay

1. Search **Echo** or **Ping Pong Delay**, drag it **after Saturator**.
2. Turn **sync** on, pick a short time (e.g. **1/8**), keep **feedback** moderate, keep **dry/wet** low (try **~20%**) so it is space, not a wash.

### Reverb

1. Search **Reverb**, drag it **after** the delay.
2. Medium **decay** (about **1–2 s**), low **dry/wet** (try **~20%**).

---

## 9. Tuning by ear

- **Too dull:** raise the **baseline cutoff** slightly, or increase **Env → Freq** amount, or shorten **Filter Decay** for a faster reopening.
- **Too harsh:** lower **Reso**, reduce **Saturator** drive, or reduce **Env → Freq**.
- **More “siren” pitch height:** transpose **MIDI** **up an octave or two**; this kind of line is often written high.

---

## 10. If you do not own Analog

Any **subtractive** synth (**Wavetable**, **Operator**, **Serum**, hardware with **OSC + LP filter + filter env**) follows the same recipe: **saw → resonant LP → envelope on cutoff → distortion → delay → reverb**. Only the **panel names** change.

---

## Related

- [beginner-reference-track-guide.md](beginner-reference-track-guide.md) — level-matching and referencing habits when you compare this line to a finished track.
