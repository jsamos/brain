# Capture MIDI in Ableton Live 12

Follow these steps in order. Each step ends with something you can **see or hear** before moving on.

**End result:** A MIDI clip in Session View that loops what you just played.

**Live 12.4+:** **Cmd+Shift+C does not capture MIDI** (it is **Copy Time** now). Use the control-bar button, or remap with **Cmd+K**.

---

## 1. Reveal the Capture button

1. Widen the Live window until the top control bar shows every icon.
2. Find **Play** / **Stop** (triangle / square).
3. Look **to the right** in the next button group for a small **frame / four-corner brackets** icon (no text label).
4. Hover it — tooltip must say **Capture MIDI**.

If you cannot find it, the window is still too narrow. Widen more.

---

## 2. Prepare the track

1. Open **Session View** (**Tab** if you are in Arrangement).
2. Click an **empty clip slot** on your MIDI track (the slot highlights).
3. On that track:
   - **Arm** (red record button on).
   - **Monitor → Auto** (not **In**, not **Off**).
   - **MIDI From** = your keyboard (or **All Ins** if that already works).
   - Fader **above -inf** — you must hear the instrument when you test.

**Check:** Play one note. You hear the instrument. The Capture icon is **grey** (normal before you play a phrase).

---

## 3. Capture

1. Play a short phrase — at least **4–8 notes** in rhythm.
2. Stop touching the keyboard.
3. Look at the Capture icon:
   - Still **grey** → see [Icon stays grey](#icon-stays-grey) below. Do not continue until it turns **black**.
   - **Black** → click the icon **once**.

**Check:** A new clip appears in the slot on that MIDI track (or in Arrangement at the playhead if you clicked in the timeline last — use Session View to avoid that).

---

## 4. Clip shorter than what you played

Normal. Capture picks a **loop phrase**, not your full take. The extra notes are usually still in the clip.

1. **Double-click** the clip.
2. In the piano roll, **zoom out** horizontally.
3. Drag the **loop brace** (top bar) to cover all notes you want.
4. Drag the **clip end marker** right if notes sit past the loop.
5. Optional: right-click clip → **Crop Clip**.

**Check:** All your notes are inside the loop region in the piano roll.

---

## 5. Hear it back

1. **Monitor → Auto** (if you changed it to **In** earlier, change it back now).
2. Click the clip **launch button** (triangle), or select the slot and press **Enter**.

**Check:** The clip loops and you hear your phrase.

If the clip is **grey** and will not launch: select it, press **0**, launch again.

---

## 6. Optional: assign a shortcut

1. **Cmd+K** (Key Map mode on).
2. Click the **Capture MIDI** icon in the control bar.
3. Press the key combo you want.
4. **Cmd+K** again to exit.

---

## If something fails

### Icon stays grey

Live is not buffering MIDI on that track.

| Check | Fix |
| --- | --- |
| Track not armed | Turn **Arm** on |
| Monitor **Off** | Set **Monitor → Auto** and keep **Arm** on |
| No sound when you play | Fix **MIDI From**; in **Settings → Link, Tempo & MIDI**, enable **Track** on your controller port |
| Computer keyboard | **Cmd+Shift+K** on; MIDI track selected |

### Icon turns black but no clip

| Check | Fix |
| --- | --- |
| Last click was Arrangement timeline | **Tab** to Session; click an empty slot; capture again |
| Clip landed in Arrangement | Find the playhead; unfold the track lane |

### Clip appears but silent on launch

| Check | Fix |
| --- | --- |
| Monitor **In** | **Monitor → Auto** |
| Fader at **-inf** | Raise fader |
| Clip deactivated (grey) | Select clip, press **0** |

---

## When Capture is the wrong tool

Need the **full length** of everything you play, not a guessed loop? Skip Capture:

1. Arm the track.
2. Click the **record circle** in an empty Session slot.
3. Play.
4. Click **Launch** to stop and keep the take.

---

## Related

- [ableton-one-percent-improvement-thread.md](ableton-one-percent-improvement-thread.md)
- [bassline-processing.md](bassline-processing.md)
