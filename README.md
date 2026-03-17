# KWB Modbus for Home Assistant

[English](README.md) | [Deutsch](README.de.md)

Custom integration to connect KWB heating systems via Modbus TCP in Home Assistant.

## Features

- Config Flow setup in Home Assistant (no YAML required)
- Entities for `sensor`, `select`, and `button`
- Automatic derived pellet consumption sensors for `day`, `week`, `month`, and `year` (calculated from total fuel counter)
- Automatic detection of active add-on module instances (for example heating circuits, buffer tanks)
- Custom instance names (for example `HC 1.1` -> `Living room`)
- Expert mode for additional control selects that are disabled by default
- `Re-run Sensor Discovery` button to trigger discovery again
- Firmware profile auto-detection with manual override

## Supported Heating Devices

| Heating Device | Tested |
| --- | --- |
| KWB EasyFire | ✓ |
| KWB MultiFire | X |
| KWB PelletFire+ | X |
| KWB CombiFire | X |
| KWB CF 2 | X |
| KWB CF 1.5 | X |
| KWB CF 1 | X |

## Supported Add-on Modules

| Add-on Module | Tested |
| --- | --- |
| Buffer storage tank | ✓ |
| Solar | X |
| Heating circuits | ✓ |
| Domestic hot water (DHWC) | X |
| Circulation | X |
| Secondary heating sources | X |
| Heat quantity meter | X |
| Boiler master-slave circuit | X |
| WMM autonom | X |

## Tested With

- System/Firmware versions: `22.4.0` and `25.4.1`
- Legend: `✓` = tested, `X` = not tested

## Requirements

- Home Assistant with HACS installed
- KWB controller with Modbus TCP enabled
- Network connectivity from Home Assistant to the KWB system
- Default port: `502`

## Installation via HACS

1. Open HACS.
2. Go to `Integrations`.
3. Open `Custom repositories`.
4. Add repository URL: `https://github.com/Tobim99/homeassistant-kwb-modbus`
5. Select category `Integration`.
6. Install the integration.
7. Restart Home Assistant.

## Manual Installation

1. Copy `custom_components/kwb_modbus` into your Home Assistant config directory.
2. Restart Home Assistant.

## Setup

1. In Home Assistant, go to `Settings -> Devices & Services -> Add Integration`.
2. Select `KWB Modbus`.
3. Enter connection details: host (IP/hostname), port (default `502`), and polling interval (seconds).
4. Select your heating device.
5. Select installed add-on modules.
6. Review auto-detected instances and adjust if needed.
7. Optionally set friendly names for instances.

## Reconfiguration

You can update connection settings later from the integration menu (`...` -> `Reconfigure`).

## Troubleshooting

- `cannot_connect` error:
  Check IP/hostname, port, firewall, and whether Modbus TCP is enabled on the system.
- Missing or implausible values:
  Verify the selected heating device and add-on modules.
- Missing entities for add-on modules:
  Use the `Re-run Sensor Discovery` button.
- Writable options not visible:
  Check whether `Expert mode` was enabled during setup.

## Enable Debug Logging

```yaml
logger:
  default: info
  logs:
    custom_components.kwb_modbus: debug
```

## Known Limitations

- Uses Modbus TCP only (no serial Modbus RTU).
- Registers/entities may vary depending on KWB firmware and system configuration. Please report differences as an issue including firmware version, device type, and affected modules: https://github.com/Tobim99/homeassistant-kwb-modbus/issues

## Support and Issues

- Issue tracker: https://github.com/Tobim99/homeassistant-kwb-modbus/issues

When reporting bugs, please include:

- Home Assistant version
- Integration version
- KWB device model
- Relevant debug logs
- Steps to reproduce

## Notice

This project is a community custom integration and is not officially affiliated with KWB or Home Assistant.

Use at your own risk. No warranty is provided for functionality, availability, compatibility, or fitness for a particular purpose. The author is not liable for direct or indirect damages, consequential damages, data loss, or malfunctions of system, hardware, or software resulting from installation, configuration, or use of this integration.
