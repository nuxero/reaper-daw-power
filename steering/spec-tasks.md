---
inclusion: always
---

# Reaper DAW Spec Task Guidelines

When working with specs in Reaper DAW projects, focus on tool usage tasks rather than coding tasks.

## Task Creation Rules

- DO NOT create coding or implementation tasks
- DO create tool usage tasks that directly interact with Reaper
- Tasks should be action-oriented and specific to mixing, processing, or mastering

## Task Examples

### Good Tasks (Tool Usage)
- "Get current volume level of lead vocal track"
- "Set track 3 volume to -8dB"
- "Add EQ to bass track"
- "Adjust compressor ratio on drum bus to 4:1"
- "Create send from vocal track to reverb bus with -12dB level"
- "Set limiter ceiling on master to -0.3dB"
- "Pan guitar track 40% left"
- "Remove delay effect from track 5"
- "Insert new track named 'Synth Pad'"
- "Get list of all FX on master track"
- "Set EQ high-pass filter frequency to 80Hz on track 2"

### Bad Tasks (Avoid These)
- "Write a function to calculate optimal compression settings"
- "Create a script to automate track naming"
- "Implement a plugin wrapper class"
- "Build a custom EQ algorithm"

## Task Structure

Each task should:
1. Specify the exact action (get, set, add, adjust, create, remove)
2. Identify the target (track name/number, FX, parameter)
3. Include specific values when setting parameters
4. Be achievable with available MCP tools

## Workflow Organization

Group related tasks by workflow stage:
- Setup: Track creation, naming, routing
- Mixing: Volume, pan, basic FX
- Processing: Detailed FX parameter adjustments
- Mastering: Master bus processing, limiting
- Review: Getting current states and levels
