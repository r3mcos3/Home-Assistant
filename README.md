# 🏠 Home Assistant Configuration

[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-2026.2.0.dev202601281710-41BDF5.svg?style=flat-square&logo=home-assistant)](https://www.home-assistant.io/)
[![GitHub Last Commit](https://img.shields.io/github/last-commit/r3mcos3/Home-Assistant?style=flat-square)](https://github.com/r3mcos3/Home-Assistant)
[![GitHub Stars](https://img.shields.io/github/stars/r3mcos3/Home-Assistant?style=flat-square)](https://github.com/r3mcos3/Home-Assistant/stargazers)

This is my personal Home Assistant configuration. This repository contains all automations, scripts, and custom integrations that power my smart home.

## 📋 Table of Contents

- [Overview](#-overview)
- [Custom Components](#-custom-components)
- [Integrations](#-integrations)
- [Automations](#-automations)
- [Folder Structure](#-folder-structure)
- [Entity Naming Convention](#-entity-naming-convention)
- [Credits](#-credits)

## 🎯 Overview

This configuration runs on **Home Assistant 2026.2.0.dev202601281710** (development version) and uses a mix of official integrations and custom components to create a fully automated smart home experience.

### Key Features

- 🤖 **AI-powered automations** with LLMVision
- 📍 **Location tracking** via Life360
- 💡 **Zigbee devices** via Zigbee2MQTT
- 🎨 **Custom themes** for the interface
- 🔔 **Advanced notifications**
- 📊 **Web scraping** for external data

## 🔌 Custom Components

| Component | Description |
|-----------|-------------|
| [HACS](https://hacs.xyz/) | Home Assistant Community Store |
| [Life360](https://github.com/pnbruckner/ha-life360) | Life360 device tracking |
| [LLMVision](https://github.com/valentinfrlch/ha-llmvision) | AI vision analysis with LLM |
| [Spook](https://github.com/frenck/spook) | Extra developer tools and services |

## 🌐 Integrations

### Official Integrations

- 🏠 **Default Config** - Base Home Assistant functionality
- 📱 **Frontend** - Dashboard and UI
- 🔔 **Notify** - Notification services
- 📊 **Scrape** - Web scraping sensors

### Third-party Integrations

- 🐝 **Zigbee2MQTT** - Zigbee devices
- 📍 **Life360** - Family location tracking

## 🤖 Automations

All automations can be found in [`automations.yaml`](automations.yaml). The configuration includes automations for:

- Lighting and climate control
- Notifications and alerts
- Device tracking and presence detection
- And more...

## 📁 Folder Structure

```
.
├── automations.yaml          # All automations
├── blueprints/              # Automation blueprints
├── configuration.yaml       # Main configuration
├── custom_components/       # Custom integrations
├── files/                   # Additional config files
│   ├── groups.yaml         # Groups
│   ├── notify.yaml         # Notification config
│   └── scrape.yaml         # Scrape sensors
├── scripts.yaml            # Scripts
├── scenes.yaml             # Scenes
├── themes/                 # Custom themes
├── www/                    # Frontend files
└── zigbee2mqtt/           # Zigbee2MQTT config
```

## 🎨 Themes

Custom themes are available in the `themes/` folder and are automatically loaded via the frontend configuration.

## 🏷️ Entity Naming Convention

All entities in this configuration follow a standardized English naming schema for consistency and clarity.

### Naming Format

```
{floor}_{room}_{function}_{device_type}
```

### Floor Prefixes

| Prefix | Floor | Dutch |
|--------|-------|-------|
| `gf_` | Ground Floor | begane grond |
| `ff_` | First Floor | eerste verdieping |
| `bf_` | Basement Floor | kelder |
| `at_` | Attic | zolder |
| `out_` | Outside | buiten |

### Device Type Suffixes

- `light` - Individual light or main light
- `spots` - Spotlight group
- `ceiling` - Ceiling light
- `motion` - Motion/occupancy sensor
- `contact` - Door/window contact sensor
- `switch` - Physical or smart switch

### Room Names

| English | Dutch |
|---------|-------|
| `kitchen` | keuken |
| `living` | woonkamer |
| `bedroom_main` | grote slaapkamer |
| `bedroom_elyza` | slaapkamer Elyza |
| `bedroom_santi` | slaapkamer Santi |
| `toilet` | WC |
| `hallway` | hal |
| `landing` | overloop/trap |
| `basement` | kelder |
| `attic` | zolder |
| `shed` | schuur |
| `conservatory` | serre |
| `garden` | tuin |

### Examples

- `light.gf_kitchen_light` - Ground floor kitchen light
- `light.gf_living_spots` - Ground floor living room spotlights
- `light.ff_bedroom_elyza_light` - First floor Elyza's bedroom light
- `binary_sensor.bf_basement_motion_occupancy` - Basement motion sensor
- `binary_sensor.gf_door_front_contact` - Ground floor front door contact
- `light.out_conservatory_spots` - Outside conservatory spotlights

### Multiple Devices

For multiple devices of the same type, use numbered suffixes:
- `light.gf_living_ceiling_1` / `light.gf_living_ceiling_2`
- `light.gf_living_spot_1` through `light.gf_living_spot_6`
- `light.gf_living_spots` - Group containing all spots

### Seasonal Devices

Format: `{floor}_{room}_{season}_{item}`
- `light.gf_living_christmas_tree`
- `light.gf_living_christmas_garland`

## Screenshot

<img width="1348" height="1550" alt="screenshot" src="https://github.com/user-attachments/assets/d8f2ee31-7574-43c1-8aa8-f1877bdcc73b" />


## 🙏 Credits

- [Home Assistant Community](https://community.home-assistant.io/)
- [HACS](https://hacs.xyz/)
- All developers of the custom components used in this configuration

## 📝 License

This project is available under the MIT License. See the [LICENSE](LICENSE) file for more information.

---

<div align="center">

**⭐ If you find this configuration useful, please give it a star!**

Made with ❤️ and Home Assistant

</div>
