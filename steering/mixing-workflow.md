---
inclusion: always
---

# Mixing Workflow Guide

This guide provides best practices for mixing workflows using Reaper MCP tools.

## Standard Mixing Order

1. Gain Staging
   - Get all track levels
   - Set initial volumes for proper headroom
   - Aim for -18dB to -12dB on individual tracks

2. Panning
   - Set pan positions for stereo width
   - Keep bass and kick centered
   - Pan supporting elements for space

3. EQ
   - Add high-pass filters to remove rumble
   - Cut problem frequencies
   - Boost for presence and character

4. Compression
   - Add compressors to control dynamics
   - Set ratio, threshold, attack, release
   - Typical ratios: 2:1 to 4:1 for mixing

5. Effects
   - Add reverb and delay sends
   - Create effect buses for efficiency
   - Keep effects subtle in the mix

6. Master Bus
   - Add gentle compression (2:1 ratio)
   - Add limiter for final level control
   - Set ceiling to -0.3dB to -1.0dB

## Common Tool Sequences

### Setting Up Vocal Chain
```
1. get_track (find vocal track)
2. set_track_volume (set to -12dB)
3. add_eq (add EQ)
4. track_fx_set_param (high-pass at 80Hz)
5. add_compressor (add compression)
6. track_fx_set_param (set ratio to 3:1)
7. create_send (send to reverb bus)
```

### Creating Drum Bus
```
1. create_bus (create "Drums" bus)
2. create_send (from kick to drum bus)
3. create_send (from snare to drum bus)
4. create_send (from hi-hat to drum bus)
5. add_compressor (on drum bus)
6. track_fx_set_param (set for glue compression)
```

### Master Chain Setup
```
1. get_track (get master track)
2. add_eq (add master EQ)
3. add_compressor (add gentle compression)
4. track_fx_set_param (ratio 2:1, threshold -6dB)
5. add_limiter (add final limiter)
6. track_fx_set_param (ceiling -0.3dB)
```

## Tips

- Always save project after major changes
- Check levels frequently with get_track
- Use buses for parallel processing
- Keep master peak below -1dB
- Reference commercial tracks for balance
