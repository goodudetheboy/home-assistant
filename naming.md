Device & Entity Naming Convention

1. Device

Description
- Device only has a friendly name, not an ID.
- Only Entities are exposed externally (e.g. to voice assistants).
- Devices are for internal development reference.
- Friendly name should contain:
  - The room the device is in.
  - The device name, always including the brand for clarity.

Format
[room name] [device name]

Requirements
- First character of each word is capitalized.
- Only alphanumerics and spaces allowed.

Legend
- [room name] → Name of the room (e.g., Living Room, Kitchen, Bedroom).
- [device name] → Generic device name + brand.
  Example: Plug TP-Link, LED Strip Govee, Echo Dot Amazon, TV Hisense, AC GE.

---

2. Entity

2.1 Entity Name

Description
- A Device contains Entities, which are variables the device controls.
- You don’t interact with Devices directly in HA, but with their Entities.
- Example: A Light device may have On/Off, Color, and Brightness entities.
- Entity name should include:
  - Room name
  - Device name (with brand)
  - Function (unless it is a “main” entity)

- If entity is labeled “main”, its name is just [room name] [device name].
- If entity is labeled “hidden main”, it means:
  - It’s also the main controller.
  - But it is hidden in favor of another entity (e.g., Plug switch hidden, Light entity shown).

Format
[room name] [device name] [function]   // omit [function] if "main"

Requirements
- First character of each word is capitalized.
- Only alphanumerics and spaces allowed.

Legend
- [room name] → Name of the room.
- [device name] → See Section 1 Device (always includes brand).
- [function] → Function of the entity (e.g., LED Indicator, Thermostat, Cloud Connection).

Examples
- Living Room AC GE Thermostat
- Bedroom Bulb Philips Power Switch
- "main" → Bedroom Bulb Philips

---

2.2 Entity ID

Description
- Entity ID is the unique identifier for each variable a device controls.
- Format always begins with the domain (e.g., light, switch, climate).
- After domain, it should contain:
  - Room name
  - Device name (with brand)
  - Function (unless it is a “main” entity)

- Including the room name in the Entity ID helps disambiguate devices in different rooms, makes automations clearer and safer, and immediately flags broken references if a device is moved. This ensures proper automation behavior and easier maintenance.

- If entity is labeled “main”, [function] is omitted.
- If entity is labeled “hidden main”, use the same convention, but note it in internal docs for clarity.

Format
[domain].[room name]_[device name]_[function]   // omit [function] if "main"

Requirements
- Convert spaces to underscores.
  Example: Living Room → living_room
- Only lowercase alphanumerics and underscores allowed.
- Entity IDs do not preserve capitalization or spaces from Device/Entity names.

Legend
- [domain] → One of HA’s fixed domains (e.g., light, switch, climate). Cannot usually be changed.
- [room name] → Room name, lowercase with underscores.
- [device name] → Device name with brand, lowercase with underscores.
- [function] → Function of the entity, lowercase with underscores (e.g., led_indicator, thermostat, cloud_connection).

Examples
- climate.living_room_ac_ge_thermostat
- switch.bedroom_bulb_philips_power_switch
- "main" → light.bedroom_bulb_philips

