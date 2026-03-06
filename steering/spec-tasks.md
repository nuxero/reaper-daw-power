---
inclusion: always
---

# Reaper DAW Spec Task Guidelines

**CRITICAL**: When creating specs for Reaper DAW projects, you MUST create tool-based tasks that use MCP tools to interact with Reaper. DO NOT create coding, scripting, or software implementation tasks.

## Core Principle

Reaper DAW specs are about USING TOOLS to manipulate audio projects, not writing code. Every task must be executable through available MCP tool calls.

## Task Creation Rules

**FORBIDDEN - Never Create These:**
- Coding tasks (writing functions, classes, modules)
- Script development tasks (Python, Lua, ReaScript)
- Algorithm implementation tasks
- Software architecture tasks
- Plugin development tasks
- Automation script creation
- File I/O or data processing code
- Any task requiring writing or modifying code files

**REQUIRED - Always Create These:**
- MCP tool invocation tasks that directly control Reaper
- Audio processing tasks using Reaper's built-in FX
- Track manipulation tasks (create, rename, route, adjust)
- Mix parameter adjustment tasks (volume, pan, FX settings)
- Project state inspection tasks (get levels, list FX, check routing)
- MIDI composition tasks (create items, add notes, edit velocities)
- Audio editing tasks (import, split, fade, duplicate)
- Automation tasks (create envelopes, add points)
- Marker and region tasks (create, navigate, render)

## Available MCP Tools Reference (130 tools)

When creating tasks, you can ONLY use these MCP tools:

**Track Operations (19 tools):**
- `get_track_count`, `get_track`, `get_all_tracks`, `get_master_track`
- `insert_track`, `delete_track`, `set_track_name`
- `set_track_volume`, `set_track_pan`, `set_track_width`, `get_track_peak`
- `set_track_mute`, `set_track_solo`, `set_track_phase`, `set_track_color`
- `set_track_as_folder`, `arm_track`, `set_track_input`, `set_track_monitor`

**FX Operations (15 tools):**
- `track_fx_add_by_name`, `track_fx_delete`, `track_fx_get_list`, `track_fx_get_count`
- `track_fx_get_name`, `track_fx_get_enabled`, `track_fx_set_enabled`
- `track_fx_get_num_params`, `track_fx_get_param_name`, `track_fx_get_param`, `track_fx_set_param`
- `get_fx_presets`, `get_fx_preset`, `set_fx_preset`, `save_fx_preset`

**Routing (9 tools):**
- `create_send`, `delete_send`, `set_send_volume`, `get_track_num_sends`
- `set_send_dest_channels`, `set_send_source_channels`
- `setup_sidechain_send`, `configure_reacomp_sidechain`, `setup_sidechain_compression`

**Transport (10 tools):**
- `play`, `stop`, `pause`, `record`, `get_play_state`
- `get_cursor_position`, `set_cursor_position`, `get_play_position`
- `toggle_repeat`, `get_repeat_state`

**Project (15 tools):**
- `get_project_summary`, `save_project`, `create_project`, `open_project`
- `get_project_path`, `get_project_name`, `get_project_length`
- `get_tempo`, `set_tempo`, `get_time_signature`, `set_time_signature`
- `render_project`, `render_region`, `zoom_to_selection`, `zoom_to_project`

**MIDI Operations (8 tools):**
- `create_midi_item`, `get_midi_item`
- `add_midi_note`, `add_midi_notes_batch`, `get_midi_notes`, `delete_midi_note`
- `clear_midi_item`, `set_midi_note_velocity`

**Audio Items (17 tools):**
- `insert_audio_file`, `get_track_items`, `get_item_info`
- `set_item_position`, `set_item_length`, `delete_item`, `duplicate_item`, `split_item`
- `set_item_mute`, `set_item_volume`, `set_item_fade_in`, `set_item_fade_out`
- `select_all_items`, `unselect_all_items`, `get_selected_items`
- `copy_selected_items`, `paste_items`

**Markers & Regions (8 tools):**
- `add_marker`, `add_region`, `get_markers`, `get_regions`
- `delete_marker`, `delete_region`, `go_to_marker`, `go_to_region`

**Automation (8 tools):**
- `get_track_envelope`, `get_envelope_point_count`, `get_envelope_points`
- `add_envelope_point`, `delete_envelope_point`, `clear_envelope`
- `set_track_automation_mode`, `arm_track_envelope`

**Selection & Editing (11 tools):**
- `undo`, `redo`, `get_undo_state`
- `select_track`, `select_all_tracks`, `unselect_all_tracks`, `get_selected_tracks`
- `set_time_selection`, `get_time_selection`, `clear_time_selection`
- `delete_selected_items`

**Mixing Helpers (6 tools):**
- `add_mastering_chain`, `add_parallel_compression`, `create_bus`
- `add_eq`, `add_compressor`, `add_limiter`

**Advanced (4 tools):**
- `run_action`, `run_action_by_name`, `get_track_fx_chunk`, `cut_selected_items`

## Task Examples

### ✅ CORRECT Tasks (MCP Tool Usage)

**Track Management:**
- "Get current volume level of lead vocal track"
- "Set track 3 volume to -8dB"
- "Insert new track named 'Synth Pad'"
- "Delete track 5"
- "Rename track 2 to 'Background Vocals'"
- "Get total track count in project"
- "Mute track 3"
- "Solo drum track"
- "Set track 1 color to red"
- "Arm track 2 for recording"

**Effects Processing:**
- "Add EQ to bass track"
- "Add compressor to drum bus"
- "Add limiter to master track"
- "Remove delay effect from track 5"
- "Get list of all FX on master track"
- "Bypass compressor on vocal track"
- "Load preset 'Vocal Warmth' on track 1 EQ"
- "Save current compressor settings as preset"

**FX Parameter Adjustment:**
- "Set EQ high-pass filter frequency to 80Hz on track 2"
- "Adjust compressor ratio on drum bus to 4:1"
- "Set limiter ceiling on master to -0.3dB"
- "Get current compressor threshold value on vocal track"

**Routing and Sends:**
- "Create send from vocal track to reverb bus with -12dB level"
- "Create bus named 'Drums' for drum submix"
- "Set send volume from snare to drum bus to -6dB"
- "Setup sidechain compression from kick to bass"
- "Delete send 0 from track 2"

**Panning & Width:**
- "Pan guitar track 40% left"
- "Pan background vocal 1 to 30% right"
- "Set lead vocal pan to center (0%)"
- "Set stereo width to 1.5 on synth track"

**MIDI Composition:**
- "Create 4-bar MIDI item on track 0 at position 0"
- "Add C4 note at 0 seconds with velocity 100"
- "Add batch of notes for C major chord"
- "Get all notes in MIDI item 0"
- "Set velocity of note 0 to 80"
- "Delete note 2 from MIDI item"
- "Clear all notes from MIDI item 0"

**Audio Editing:**
- "Import audio file 'vocal.wav' to track 1 at 10 seconds"
- "Split item 0 on track 2 at 30 seconds"
- "Add 2-second fade in to item 0"
- "Add 1-second fade out to item 1"
- "Duplicate item 0 on track 3"
- "Set item volume to -3dB"
- "Move item to position 45 seconds"

**Automation:**
- "Add volume automation point at 30 seconds with value 0.5"
- "Get all automation points for volume envelope on track 1"
- "Set track automation mode to latch"
- "Clear all automation on track 2 volume envelope"
- "Arm volume envelope for recording on track 3"

**Markers & Regions:**
- "Add marker 'Chorus' at current position"
- "Create region from 30 to 60 seconds named 'Verse 1'"
- "Jump to marker 2"
- "Get all markers in project"
- "Delete region 0"
- "Render region 1 to 'verse1.wav'"

**Transport & Playback:**
- "Play the project"
- "Stop playback"
- "Set cursor to 45 seconds"
- "Toggle repeat mode"
- "Start recording"
- "Get current play state"

**Project Management:**
- "Get project summary"
- "Set tempo to 120 BPM"
- "Save the project"
- "Render project to 'mix.wav' from 0 to 180 seconds"
- "Set time signature to 3/4"
- "Get project length"
- "Zoom to time selection"

**Selection & Editing:**
- "Select track 3"
- "Select all tracks"
- "Undo last action"
- "Set time selection from 10 to 30 seconds"
- "Delete selected items"
- "Copy selected items"

**Mixing Helpers:**
- "Add mastering chain to master track"
- "Add parallel compression to drums at -6dB"
- "Create bus 'Vocals' with tracks 1, 2, 3"

### ❌ INCORRECT Tasks (Coding/Implementation)

**Never create tasks like these:**
- "Write a function to calculate optimal compression settings"
- "Create a script to automate track naming"
- "Implement a plugin wrapper class"
- "Build a custom EQ algorithm"
- "Develop a Python module for audio analysis"
- "Create a ReaScript to batch process tracks"
- "Write code to parse project files"
- "Implement a gain staging calculator"
- "Build a mixing automation system"
- "Create a custom DSP algorithm"

Group related tasks by workflow stage:

**1. Setup Phase:**
- Track creation and naming
- Initial routing setup
- Bus creation
- Audio file import

**2. Gain Staging Phase:**
- Getting current track levels
- Setting initial volumes
- Checking headroom
- Setting track colors for organization

**3. Mixing Phase:**
- Panning tracks
- Setting stereo width
- Adding basic FX (EQ, compression)
- Creating sends to effect buses
- Setting basic FX parameters

**4. Processing Phase:**
- Detailed FX parameter adjustments
- Fine-tuning compression ratios
- Adjusting EQ frequencies and gains
- Setting send levels
- Sidechain compression setup

**5. MIDI Composition Phase:**
- Creating MIDI items
- Adding notes and chords
- Editing velocities
- Clearing and reorganizing MIDI data

**6. Audio Editing Phase:**
- Splitting items
- Adding fades
- Duplicating items
- Adjusting item positions and volumes

**7. Automation Phase:**
- Creating volume/pan envelopes
- Adding automation points
- Setting automation modes
- Arming envelopes for recording

**8. Mastering Phase:**
- Master bus EQ
- Master bus compression
- Final limiting
- Setting output ceiling
- Using mastering chain helper

**9. Markers & Navigation Phase:**
- Adding markers for song sections
- Creating regions for rendering
- Navigating between sections

**10. Review & Finalize Phase:**
- Getting current states
- Listing all FX
- Checking routing
- Verifying levels
- Rendering project or regions
- Saving project

## Example Spec Task List

Here's how a proper Reaper spec should look:

```markdown
## Setup
- [ ] 1.1 Insert new track named 'Lead Vocal'
- [ ] 1.2 Insert new track named 'Reverb Bus'
- [ ] 1.3 Create bus named 'Drums'

## Gain Staging
- [ ] 2.1 Get current volume of Lead Vocal track
- [ ] 2.2 Set Lead Vocal track volume to -12dB
- [ ] 2.3 Get all track levels to check headroom

## Mixing
- [ ] 3.1 Pan Lead Vocal to center (0%)
- [ ] 3.2 Add EQ to Lead Vocal track
- [ ] 3.3 Set EQ high-pass filter to 80Hz on Lead Vocal
- [ ] 3.4 Add compressor to Lead Vocal track
- [ ] 3.5 Set compressor ratio to 3:1 on Lead Vocal

## Effects Routing
- [ ] 4.1 Create send from Lead Vocal to Reverb Bus at -12dB
- [ ] 4.2 Add reverb FX to Reverb Bus track

## Mastering
- [ ] 5.1 Get master track
- [ ] 5.2 Add EQ to master track
- [ ] 5.3 Add compressor to master track
- [ ] 5.4 Set master compressor ratio to 2:1
- [ ] 5.5 Add limiter to master track
- [ ] 5.6 Set limiter ceiling to -0.3dB

## Finalize
- [ ] 6.1 Save project
```

## Common Mistakes to Avoid

**❌ Creating implementation tasks:**
```
- [ ] Implement automatic gain staging algorithm
- [ ] Write script to analyze frequency content
- [ ] Build custom compressor plugin
```

**✅ Create tool usage tasks instead:**
```
- [ ] Get all track volumes to assess gain staging
- [ ] Add EQ to bass track and set high-pass to 40Hz
- [ ] Add compressor to drum bus with 4:1 ratio
```

**❌ Vague or non-executable tasks:**
```
- [ ] Improve vocal sound
- [ ] Make drums punchier
- [ ] Optimize mix balance
```

**✅ Specific, executable tasks:**
```
- [ ] Add compressor to vocal track
- [ ] Set vocal compressor ratio to 3:1 and threshold to -18dB
- [ ] Create parallel compression send from drums to drum crush bus
- [ ] Set drum parallel bus compressor ratio to 8:1
```

## Validation Checklist

Before finalizing a spec, verify each task:
- [ ] Uses an available MCP tool (check tool list above)
- [ ] Specifies exact target (track name/number, FX, parameter)
- [ ] Includes specific values where needed (dB, Hz, ratio, %)
- [ ] Is action-oriented (verb + target + value)
- [ ] Contains NO coding, scripting, or implementation work
- [ ] Can be executed by calling MCP tools through the Reaper power
