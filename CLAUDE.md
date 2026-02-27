# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Home Assistant configuration repository running version 2026.1.0.dev. The setup includes Zigbee2MQTT integration, custom components via HACS, and various automations for home automation control.

## Configuration Structure

Home Assistant uses a split configuration approach:

- **`configuration.yaml`**: Main config file that includes other YAML files
- **`automations.yaml`**: All automation definitions
- **`scripts.yaml`**: Script definitions
- **`scenes.yaml`**: Scene definitions
- **`files/`**: Additional configuration files
  - `scrape.yaml`: Web scraping sensors for fuel prices
  - `notify.yaml`: Notification configurations
  - `groups.yaml`: Entity groupings (e.g., person tracking)
- **`themes/`**: Frontend theme configurations
- **`blueprints/`**: Automation and script blueprints

## Custom Components

Located in `custom_components/`:
- **HACS**: Home Assistant Community Store for managing custom integrations
- **Life360**: Location tracking integration
- **LLMVision**: AI vision integration
- **Spook**: Extended Home Assistant functionality

## Zigbee2MQTT Integration

Configuration is in `zigbee2mqtt/configuration.yaml`:
- MQTT broker: `10.10.2.51:1883`
- Serial adapter: TCP connection to `10.10.2.182:6638` (ZStack adapter)
- Frontend: Enabled on port 8099
- Channel: 11
- All Zigbee devices are defined with friendly names (lights, motion sensors, remotes)

## Working with Automations

Automations follow two patterns:

1. **Blueprint-based** (simpler automations):
```yaml
- id: 'unique_id'
  alias: Human-readable name
  description: What it does
  use_blueprint:
    path: blueprint/path.yaml
    input:
      entity: sensor.example
```

2. **Full definitions** (complex automations):
```yaml
- id: 'unique_id'
  alias: Human-readable name
  description: What it does
  triggers:
    - platform: ...
  conditions:
    - condition: ...
  actions:
    - action: ...
  mode: single|parallel|queued
```

### Automation Naming Convention

**IMPORTANT**: All automation aliases MUST use emoji prefixes based on their type:

- 🚶 **Motion** - For motion/occupancy detection automations
  - Example: `🚶 Motion - Hallway`

- 🎛️ **Remote** - For remote control automations
  - Example: `🎛️ Remote - Attic/Elyza`

- 🚪 **Entrance** - For door/entrance related automations (non-media triggers)
  - Example: `🚪 Entrance - Back Door Lights (Sunset)`

- 👤 **Presence** - For presence/zone/home-away automations
  - Example: `👤 Presence - Home/Away Lights`

- ⏰ **Schedule** - For time/schedule based automations
  - Example: `⏰ Schedule - Garden LED Lights`

- 🔔 **Notify** - For notification automations
  - Example: `🔔 Notify - System Updates`

- 🤖 **AI** - For AI-powered automations
  - Example: `🤖 AI - Weather Report`

- 🔊 **Media** - For media/audio related automations
  - Example: `🔊 Media - Volume Control`

**When creating or modifying automations, always apply the appropriate emoji prefix to the alias.**

## Home Assistant Commands

Since this is a configuration repository, typical commands depend on where Home Assistant is running:

**Validation:**
```bash
# If HA CLI is available
ha core check

# Manual YAML validation
python -c "import yaml; yaml.safe_load(open('configuration.yaml'))"
```

**Reloading configurations** (done through Home Assistant UI or REST API, not CLI):
- Developer Tools > YAML > Check Configuration
- Developer Tools > YAML > Restart/Reload specific components

## Entity Naming Conventions

**IMPORTANT**: All entities follow a standardized English naming schema (implemented 2025-12-08):

### Naming Format
```
{floor}_{room}_{function}_{device_type}
```

### Floor Prefixes
- `gf_` = Ground Floor (begane grond)
- `ff_` = First Floor (eerste verdieping)
- `bf_` = Basement Floor (kelder)
- `at_` = Attic (zolder)
- `out_` = Outside (buiten)

### Device Type Suffixes
- `light` - Individual light or main light
- `spots` - Spotlight group
- `ceiling` - Ceiling light
- `motion` - Motion/occupancy sensor
- `contact` - Door/window contact sensor
- `switch` - Physical or smart switch

### Room Names (English)
- `kitchen` (keuken)
- `living` (woonkamer)
- `bedroom_main` (grote slaapkamer)
- `bedroom_elyza` (slaapkamer Elyza)
- `bedroom_santi` (slaapkamer Santi)
- `toilet` (WC)
- `hallway` (hal)
- `landing` (overloop/trap)
- `basement` (kelder)
- `attic` (zolder)
- `shed` (schuur)
- `conservatory` (serre)
- `garden` (tuin)

### Examples
- `light.gf_kitchen_light` - Ground floor kitchen light
- `light.gf_living_spots` - Ground floor living room spotlights (group)
- `light.ff_bedroom_elyza_light` - First floor Elyza's bedroom light
- `binary_sensor.bf_basement_motion_occupancy` - Basement motion sensor
- `binary_sensor.gf_door_front_contact` - Ground floor front door contact sensor
- `light.out_conservatory_spots` - Outside conservatory spotlights

### Multiple Devices of Same Type
Use function/location descriptors:
- `light.gf_living_ceiling_1` / `light.gf_living_ceiling_2` - Ceiling lights
- `light.gf_living_spot_1` through `light.gf_living_spot_6` - Individual spots
- `light.gf_living_spots` - Automatically created group of all spots

### Seasonal/Special Devices
Format: `{floor}_{room}_{season}_{item}`
- `light.gf_living_christmas_tree`
- `light.gf_living_christmas_garland`

**When adding new devices, always follow this naming schema for consistency.**

## Important Configuration Details

- **Secrets**: Stored in `secrets.yaml` - never commit sensitive data
- **Network path**: Configuration is on a network share `\\10.10.2.51\config\`
- **Database**: SQLite database `home-assistant_v2.db` stores history
- **Allowed external dirs**: `/config` and `/config/tmp` for file operations

## VSCode Configuration

The `.vscode/settings.json` configures:
- YAML files as `home-assistant` type for syntax validation
- Custom YAML tags: `!include`, `!secret`, `!include_dir_*`
- ESPHome file associations

## Common Tasks

**Adding a new automation:**
1. Edit `automations.yaml`
2. Use existing automations as templates
3. Ensure unique ID and descriptive alias
4. Reload automations in HA UI

**Adding a new Zigbee device:**
1. Put Zigbee2MQTT in pairing mode (via frontend on port 8099)
2. Device will auto-discover
3. Rename in `zigbee2mqtt/configuration.yaml` under `devices:` section

**Web scraping sensors:**
Edit `files/scrape.yaml` for fuel price monitoring from Dutch/Belgian gas stations
