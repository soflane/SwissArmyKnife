# Home Assistant

> Setup references, useful integrations, troubleshooting habits, and dashboard
> customizations for a locally controlled smart home.

## Getting started

[Home Assistant](https://www.home-assistant.io/) is an open-source home
automation platform that centralizes lights, sensors, thermostats, cameras, and
other devices. It prioritizes local control, privacy, and flexible automation.

## Recommended hardware

- **Raspberry Pi** — A practical starting point for small installations. Prefer
  reliable storage over an inexpensive SD card for long-running systems.  
  `Home Assistant` `Hardware`
- **Virtual machine** — A flexible choice when a Proxmox, VMware, or other
  virtualization host is already available.  
  `Home Assistant` `Virtualization`

## Installation methods

- **Home Assistant OS** — Use the managed operating system for Supervisor,
  add-ons, backups, and the simplest update path.  
  `Recommended` `Managed`
- **Home Assistant Container** — Run Home Assistant with Docker while managing
  updates, networking, and companion services separately.  
  `Docker` `Advanced`
- **Home Assistant Supervised** — Add the managed Supervisor experience to a
  supported Debian system when its additional maintenance is acceptable.  
  `Debian` `Advanced`
- **Home Assistant Core** — Run the Python application directly for a minimal,
  manually managed installation.  
  `Python` `Advanced`

Use the [official installation documentation](https://www.home-assistant.io/installation/)
to select a currently supported method and platform.

## Essential add-ons and integrations

- **File editor or Studio Code Server** — Edit YAML and configuration files
  from the Home Assistant interface.  
  `Add-on` `Configuration`
- **Samba share** — Access the configuration directory from another computer on
  the local network.  
  `Add-on` `Files`
- **Mosquitto broker** — Connect devices and services that communicate over
  MQTT.  
  `Add-on` `MQTT`
- **[HACS](https://hacs.xyz/)** — Install community integrations, themes, and
  dashboard cards.  
  `Community` `Integrations`

## Automation and templating

Use the built-in automation editor for triggers, conditions, and actions. YAML
mode is useful for reviewing or sharing larger automations. For dynamic values
and conditions, consult the
[templating documentation](https://www.home-assistant.io/docs/configuration/templating/).

## Dashboards and customization

Home Assistant dashboards can combine built-in cards with community cards from
HACS. Keep entity names and reusable variables easy to identify before sharing
configuration snippets.

- **[Custom card examples](custom-cards.md)** — Reusable Lovelace YAML and CSS
  patterns, including a Mushroom light card with a glowing slider.  
  `Dashboard` `YAML` `card-mod`
- **[Community resources](resources.md)** — Home Assistant documentation,
  repositories, and specialized dashboard projects.  
  `Reference` `Community`

## Smart device utilities

Desktop utilities for Xiaomi and other connected devices are listed under
[smart home and media devices](../tools/README.md#smart-home-and-media-devices).

## Troubleshooting habits

- Create backups frequently and store at least one copy outside the Home
  Assistant host.
- Check system and integration logs before changing configuration.
- Change one variable at a time, then reload or restart only the affected
  component.
- Search the official documentation and community forum with the exact error
  message and integration name.
