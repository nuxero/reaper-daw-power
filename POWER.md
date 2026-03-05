---
name: "reaper-daw-power"
displayName: "Produce music on Reaper"
description: "Produce music on Reaper leveraging MCP servers"
keywords: ["reaper", "daw", "music", "audio", "mixing", "mastering", "production", "tracks", "fx", "effects", "eq", "compressor", "limiter"]
author: "Héctor Zelaya"
---

# Reaper DAW Power

This power enables music production workflows in Reaper DAW with integrated Linux system tools.

## Overview

The Reaper DAW power provides direct control over your Reaper projects through MCP tools, allowing you to:

- Manage tracks (create, rename, adjust levels)
- Add and configure effects (EQ, compression, limiting)
- Control routing and sends
- Adjust mix parameters (volume, pan, FX settings)
- Monitor system resources during production

## Available Tools

### Reaper Tools
- Track management: `get_track`, `get_all_tracks`, `get_track_count`, `insert_track`, `set_track_name`
- Volume & Pan: `set_track_volume`, `set_track_pan`
- Effects: `add_eq`, `add_compressor`, `add_limiter`, `track_fx_add_by_name`, `track_fx_delete`
- FX Parameters: `track_fx_get_list`, `track_fx_get_num_params`, `track_fx_get_param_name`, `track_fx_get_param`, `track_fx_set_param`
- Routing: `create_send`, `set_send_volume`, `create_bus`
- Project: `save_project`

### Linux System Tools
- System monitoring: CPU, memory, disk usage
- Process management
- Service status
- Log inspection
- Network information

## Workflow Examples

### Mixing Tasks
- "Get track 2 volume level"
- "Set lead vocal track volume to -6dB"
- "Add EQ to bass track"
- "Adjust compressor threshold on drum bus"
- "Create send from vocal to reverb bus"

### Mastering Tasks
- "Add limiter to master track"
- "Set limiter ceiling to -0.3dB"
- "Check all track levels"

### Production Tasks
- "Insert new track named 'Guitar'"
- "Create bus for all drum tracks"
- "Pan guitar left 30%"
- "Remove reverb from track 5"

## Important Notes

- Reaper must be running with the MCP bridge script active
- All FX operations use Reaper's native plugin names
- Track indices are 1-based (track 1, track 2, etc.)
- Volume values are in dB
- Pan values range from -100 (left) to +100 (right)
