# 🏠 Home Assistant Configuration

[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-2026.1.0dev-41BDF5.svg?style=flat-square&logo=home-assistant)](https://www.home-assistant.io/)
[![GitHub Last Commit](https://img.shields.io/github/last-commit/USERNAME/REPO?style=flat-square)](https://github.com/USERNAME/REPO)
[![GitHub Stars](https://img.shields.io/github/stars/USERNAME/REPO?style=flat-square)](https://github.com/USERNAME/REPO/stargazers)

This is my personal Home Assistant configuration. This repository contains all automations, scripts, and custom integrations that power my smart home.

## 📋 Table of Contents

- [Overview](#-overview)
- [Custom Components](#-custom-components)
- [Integrations](#-integrations)
- [Automations](#-automations)
- [Folder Structure](#-folder-structure)
- [Credits](#-credits)

## 🎯 Overview

This configuration runs on **Home Assistant 2026.1.0** (development version) and uses a mix of official integrations and custom components to create a fully automated smart home experience.

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
