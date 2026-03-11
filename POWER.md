---
name: "reaper-daw"
displayName: "Produce music on Reaper"
description: "Produce music on Reaper leveraging MCP servers"
keywords: ["reaper", "daw", "music", "audio", "mixing", "mastering", "tracks", "fx", "effects", "eq", "compressor", "limiter"]
author: "Héctor Zelaya"
---

# Reaper DAW Power

This power enables music production workflows in Reaper DAW.

## Onboarding

### Step 1: Validate Reaper Setup

Before using Reaper MCP tools, ensure the following:

- **Reaper DAW**: Must be running and have a project open
  - Verify Reaper is running before attempting any operations
  - **CRITICAL**: If Reaper is not running, DO NOT proceed with MCP tool calls
  
- **MCP Bridge Script**: The Reaper MCP bridge must be active
  - Bridge data directory: `~/.config/REAPER/Scripts/mcp_bridge_data/`
  - Verify the bridge is responding before complex operations
  
- **Python Environment**: The MCP server requires Python
  - Server location: `~/Projects/reaper-mcp/reaper_mcp_server.py`

### Step 2: Understanding the Workflow

This power provides direct control over your Reaper projects through MCP tools, allowing you to:

- Manage tracks (create, rename, adjust levels)
- Add and configure effects (EQ, compression, limiting)
- Control routing and sends
- Adjust mix parameters (volume, pan, FX settings)
- Monitor system resources during production

## When to Load Steering Files

- Working on mixing tasks (gain staging, EQ, compression, effects) → `mixing-workflow.md`
- Creating or executing specs for Reaper projects → `spec-tasks.md`

## Available Tools

The Reaper MCP server provides **130 tools** across 11 categories for comprehensive DAW control.

### Track Operations (19 tools)
- Basic info: `get_track_count`, `get_track`, `get_all_tracks`, `get_master_track`
- Track management: `insert_track`, `delete_track`, `set_track_name`
- Levels & routing: `set_track_volume`, `set_track_pan`, `set_track_width`, `get_track_peak`
- State control: `set_track_mute`, `set_track_solo`, `set_track_phase`, `set_track_color`
- Folder & recording: `set_track_as_folder`, `arm_track`, `set_track_input`, `set_track_monitor`

### FX Operations (15 tools)
- FX management: `track_fx_add_by_name`, `track_fx_delete`, `track_fx_get_list`, `track_fx_get_count`
- FX control: `track_fx_get_enabled`, `track_fx_set_enabled`, `track_fx_get_name`
- Parameters: `track_fx_get_num_params`, `track_fx_get_param_name`, `track_fx_get_param`, `track_fx_set_param`
- Presets: `get_fx_presets`, `get_fx_preset`, `set_fx_preset`, `save_fx_preset`

### Routing (9 tools)
- Sends: `create_send`, `delete_send`, `set_send_volume`, `get_track_num_sends`
- Channel routing: `set_send_dest_channels`, `set_send_source_channels`
- Sidechain: `setup_sidechain_send`, `configure_reacomp_sidechain`, `setup_sidechain_compression`

### Transport (10 tools)
- Playback: `play`, `stop`, `pause`, `record`, `get_play_state`
- Position: `get_cursor_position`, `set_cursor_position`, `get_play_position`
- Loop: `toggle_repeat`, `get_repeat_state`

### Project (15 tools)
- Project state: `get_project_summary`, `save_project`, `create_project`, `open_project`
- Project info: `get_project_path`, `get_project_name`, `get_project_length`
- Tempo & time: `get_tempo`, `set_tempo`, `get_time_signature`, `set_time_signature`
- Rendering: `render_project`, `render_region`
- View: `zoom_to_selection`, `zoom_to_project`

### MIDI Operations (8 tools)
- Items: `create_midi_item`, `get_midi_item`
- Notes: `add_midi_note`, `add_midi_notes_batch`, `get_midi_notes`, `delete_midi_note`
- Editing: `clear_midi_item`, `set_midi_note_velocity`

### Audio Items (17 tools)
- Import & info: `insert_audio_file`, `get_track_items`, `get_item_info`
- Position & length: `set_item_position`, `set_item_length`
- Item management: `delete_item`, `duplicate_item`, `split_item`
- Item state: `set_item_mute`, `set_item_volume`, `set_item_fade_in`, `set_item_fade_out`
- Selection: `select_all_items`, `unselect_all_items`, `get_selected_items`
- Clipboard: `copy_selected_items`, `paste_items`

### Markers & Regions (8 tools)
- Create: `add_marker`, `add_region`
- Query: `get_markers`, `get_regions`
- Delete: `delete_marker`, `delete_region`
- Navigate: `go_to_marker`, `go_to_region`

### Automation (8 tools)
- Envelopes: `get_track_envelope`, `get_envelope_point_count`, `get_envelope_points`
- Points: `add_envelope_point`, `delete_envelope_point`, `clear_envelope`
- Modes: `set_track_automation_mode`, `arm_track_envelope`

### Selection & Editing (11 tools)
- Undo: `undo`, `redo`, `get_undo_state`
- Track selection: `select_track`, `select_all_tracks`, `unselect_all_tracks`, `get_selected_tracks`
- Time selection: `set_time_selection`, `get_time_selection`, `clear_time_selection`
- Item editing: `delete_selected_items`

### Mixing Helpers (6 tools)
- Workflow shortcuts: `add_mastering_chain`, `add_parallel_compression`, `create_bus`
- Quick FX: `add_eq`, `add_compressor`, `add_limiter`

### Advanced (4 tools)
- Actions: `run_action`, `run_action_by_name`
- Raw data: `get_track_fx_chunk`, `cut_selected_items`

## Workflow Examples

### Mixing Tasks
- "Get track 2 volume level"
- "Set lead vocal track volume to -6dB"
- "Add EQ to bass track"
- "Adjust compressor threshold on drum bus"
- "Create send from vocal to reverb bus"
- "Set up sidechain compression from kick to bass"
- "Add parallel compression to drums at -6dB"

### Mastering Tasks
- "Add limiter to master track"
- "Set limiter ceiling to -0.3dB"
- "Check all track levels"
- "Add mastering chain to master track"

### Production Tasks
- "Insert new track named 'Guitar'"
- "Create bus for all drum tracks"
- "Pan guitar left 30%"
- "Remove reverb from track 5"
- "Arm track 3 for recording"
- "Set track 2 input to input 1"

### MIDI Composition
- "Create a 4-bar MIDI item on track 0"
- "Add a C major chord starting at 0 seconds"
- "Get all notes in the MIDI item"
- "Set velocity of note 0 to 100"
- "Add multiple notes in batch"

### Audio Editing
- "Import audio file to track 1 at 10 seconds"
- "Split item 0 on track 2 at 30 seconds"
- "Add 2-second fade in to item 0"
- "Duplicate item 1 on track 3"
- "Set item volume to -3dB"

### Automation
- "Add volume automation point at 30 seconds with value 0.5"
- "Get all automation points for volume envelope"
- "Set track automation mode to latch"
- "Clear all automation on track 2"

### Markers & Navigation
- "Add marker 'Chorus' at current position"
- "Create region from 30 to 60 seconds named 'Verse 1'"
- "Jump to marker 2"
- "Render region 0 to output.wav"

### Transport & Playback
- "Play the project"
- "Stop playback"
- "Set cursor to 45 seconds"
- "Toggle repeat mode"
- "Start recording"

### Project Management
- "Get project summary"
- "Set tempo to 120 BPM"
- "Save the project"
- "Render project to mix.wav"
- "Set time signature to 3/4"

## Important Notes

### Track Indexing
- Regular tracks use 0-based indexing (first track = 0, second track = 1)
- Master track uses index -1
- Example: "Set master track volume to -3dB" → track_index = -1

### Common Plugin Names
Use these names with `track_fx_add_by_name`:
- EQ: `ReaEQ`
- Compressor: `ReaComp`
- Limiter: `ReaLimit`
- Gate: `ReaGate`
- Delay: `ReaDelay`
- Reverb: `ReaVerbate` or `ReaVerb`
- Third-party plugins: Use full name as shown in REAPER's FX browser

### Value Ranges
- Volume: dB values (e.g., -6, -12, 0)
- Pan: -1 (full left) to +1 (full right), or -100 to +100
- Stereo width: 0 to 2 (1 = normal)
- MIDI velocity: 0 to 127
- MIDI pitch: 0 to 127 (60 = middle C)

### Prerequisites
- Reaper must be running with the MCP bridge script active
- Bridge script location: `~/.config/REAPER/Scripts/reaper_mcp_bridge.lua`
- Bridge data directory: `~/.config/REAPER/Scripts/mcp_bridge_data/`
- Python MCP server: `~/Projects/reaper-mcp/reaper_mcp_server.py`
