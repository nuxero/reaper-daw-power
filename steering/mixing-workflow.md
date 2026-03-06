---
inclusion: always
---

# Mixing Workflow Guide

This guide provides best practices for mixing workflows using Reaper MCP tools.

## Standard Mixing Order

1. Gain Staging
   - Use volume faders, automation, and plugin output controls together
   - Get all track levels first to assess headroom
   - Set initial volumes for proper headroom: aim for -18dB to -12dB on individual tracks
   - Keep master bus peaking around -6dB before mastering
   - Use volume automation for dynamic control throughout the track
   - Group related tracks to buses for collective gain control

2. Panning
   - Set pan positions for stereo width and separation
   - Keep bass, kick, and lead vocals centered (0%)
   - Pan supporting elements for space (guitars 30-50% L/R, percussion 20-40%)
   - Use wider panning for ambient elements and effects

3. EQ (Subtractive then Additive)
   - Start with high-pass filters to remove rumble (typically 80-100Hz for most instruments)
   - Cut problem frequencies first (200-600Hz for muddiness, 2-4kHz for harshness)
   - Boost for presence and character sparingly (2-3dB maximum)
   - Key frequency ranges:
     * Sub-bass: 20-70Hz (kick, bass fundamentals)
     * Bass: 70-250Hz (warmth, body)
     * Low-mids: 250-600Hz (can cause muddiness if excessive)
     * Mids: 600Hz-2kHz (clarity, presence)
     * High-mids: 2-8kHz (definition, articulation)
     * Highs: 8-20kHz (air, sparkle)

4. Compression
   - Add compressors to control dynamics and add cohesion
   - Set ratio, threshold, attack, release based on material
   - Typical ratios: 2:1 to 4:1 for mixing, 1.5:1 to 2:1 for gentle glue
   - Fast attack (1-10ms) for controlling transients, slow attack (20-30ms) to preserve punch
   - Monitor gain reduction: aim for 3-6dB on individual tracks, 1-3dB on buses

5. Parallel Compression (New York Technique)
   - Create sends to parallel compression buses for drums and vocals
   - Apply heavy compression on the parallel track (8:1 to 10:1 ratio)
   - Blend compressed signal with dry signal for punch and sustain
   - Keeps transients intact while adding body and thickness

6. Effects and Routing
   - Add reverb and delay sends to effect buses
   - Create effect buses for efficiency and cohesion
   - Keep effects subtle in the mix (start at -12dB send level)
   - Use pre-fader sends for consistent effect levels
   - Group instruments by type (drums bus, vocal bus, instrument bus)

7. Master Bus Processing
   - Add gentle compression (1.5:1 to 2:1 ratio, 1-3dB gain reduction)
   - Use slow attack and release for transparent glue
   - Add subtle EQ for final tonal shaping
   - Add limiter for final level control
   - Set limiter ceiling to -0.3dB to -1.0dB to prevent clipping and allow for mastering headroom

## Common Tool Sequences

### Setting Up Vocal Chain
```
1. get_track (find vocal track)
2. set_track_volume (set to -12dB for headroom)
3. add_eq (add EQ)
4. track_fx_set_param (high-pass at 80-100Hz to remove rumble)
5. track_fx_set_param (cut 200-400Hz if muddy, boost 2-5kHz for presence)
6. add_compressor (add compression)
7. track_fx_set_param (ratio 3:1, attack 10ms, release 100ms, 3-6dB reduction)
8. create_send (send to reverb bus at -12dB)
9. create_send (optional: parallel compression bus for thickness)
```

### Creating Drum Bus with Parallel Compression
```
1. create_bus (create "Drums" bus)
2. create_send (from kick to drum bus)
3. create_send (from snare to drum bus)
4. create_send (from hi-hat to drum bus)
5. create_send (from toms to drum bus)
6. add_compressor (on drum bus for glue: ratio 2:1, slow attack/release)
7. create_bus (create "Drums Parallel" bus)
8. create_send (from drum bus to parallel bus, pre-fader)
9. add_compressor (on parallel bus: ratio 8:1, fast attack, heavy compression)
10. set_send_volume (blend parallel bus to taste, start at -6dB)
```

### Master Chain Setup
```
1. get_track (get master track)
2. add_eq (add master EQ for subtle tonal shaping)
3. track_fx_set_param (gentle high-pass at 30Hz, subtle adjustments only)
4. add_compressor (add gentle glue compression)
5. track_fx_set_param (ratio 1.5:1 to 2:1, threshold -6dB, slow attack/release)
6. add_limiter (add final limiter)
7. track_fx_set_param (ceiling -0.3dB to -1.0dB, preserve dynamics)
8. save_project (save after master chain setup)
```

### Bass Processing Chain
```
1. get_track (find bass track)
2. set_track_volume (set to -12dB)
3. add_eq (add EQ)
4. track_fx_set_param (high-pass at 40Hz, boost 60-80Hz for weight)
5. track_fx_set_param (cut 200-300Hz if muddy, boost 2-3kHz for definition)
6. add_compressor (control dynamics)
7. track_fx_set_param (ratio 4:1, medium attack to preserve transients)
```

### Guitar Stereo Spread
```
1. get_track (get guitar track 1)
2. set_track_pan (pan 40% left)
3. get_track (get guitar track 2)
4. set_track_pan (pan 40% right)
5. add_eq (on both: high-pass at 100Hz, cut 200-400Hz for clarity)
6. create_bus (create "Guitars" bus for collective processing)
7. create_send (from guitar 1 to guitars bus)
8. create_send (from guitar 2 to guitars bus)
```

## Mastering Workflow

When mastering in Reaper, work with the final stereo mixdown:

1. **Preparation**
   - Import stereo WAV file of final mix into new project
   - Ensure mix peaks around -6dB to -3dB for mastering headroom
   - Reference commercial tracks in similar genre

2. **Mastering Chain Order**
   ```
   1. add_eq (corrective EQ: fix any tonal imbalances)
   2. add_compressor (gentle compression: 1.5:1 ratio, 1-2dB reduction)
   3. add_eq (creative EQ: enhance character, add air above 10kHz)
   4. add_limiter (final loudness: ceiling -0.3dB to -1.0dB)
   5. track_fx_set_param (set limiter for target loudness without distortion)
   ```

3. **Loudness Targets**
   - Streaming platforms: -14 LUFS to -16 LUFS integrated
   - CD/Digital release: -8 LUFS to -10 LUFS integrated
   - Avoid over-compression: preserve dynamics and transients
   - Use two-stage limiting for transparent loudness (split gain reduction across two limiters)

4. **Final Checks**
   - Check for inter-sample peaks (set ceiling below -0.3dB)
   - A/B compare with reference tracks
   - Listen on multiple playback systems
   - Ensure consistency across album tracks

## Tips and Best Practices

- Always save project after major changes using save_project
- Check levels frequently with get_track to monitor headroom
- Use buses for parallel processing and collective control
- Keep master peak below -1dB before mastering
- Reference commercial tracks for balance and loudness
- Use subtractive EQ before additive EQ (cut before boost)
- Compress in stages rather than heavy compression on one plugin
- Monitor at low volumes to check balance (if it sounds good quiet, it sounds good loud)
- Take breaks every 30-60 minutes to avoid ear fatigue
- Use sends pre-fader for consistent effect levels regardless of track volume changes
- Group similar instruments to buses for efficient processing and cohesion
