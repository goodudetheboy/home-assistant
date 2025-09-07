Device & Entity Naming Convention

1. Device
Description: Device only has a friendly name and not ID. As I read online, only Entities are exposed to the outside world for voice assistant, so that's why Device is only identified with only a friendly name because it's only for internal development. Regarding the format of the friendly name, it should contains a Room where the actual device connecting is from, and the name of the device, if possible, with the brand for better discriminability, but this is not required


Format: "[room name] [device name]"
Requirements:
	- All first character of each word is capitalized
	- Only alphanumerics and spaces are allowed
Legend:
	- [room name]: The name of room in which the device is in, e.g. Living Room, Kitchen, Bedroom...
	- [device name]: The name of the device, with the generic name of the device first (optionally) AND THEN the brand name e.g. (no brand example) Plug, Led Strip, Echo Dot, TV, (brand example) AC GE, TV Google, TV Hisense.

2. Entity
2.1 Entity Name
Description: Device contains Entity, which are variable that that Device controls. From what I read in HA docs, you're not interfacing the Device directly, but rather through Entity. So a Light Device can contains On/Off Entity, Color Entity, and/or Brightness Entity. Anyway, it should contain Room name, the name of the device, and the function of the device.
	One more thing, if the entity is identified to be the main controller of the device (by having "main" label), then the name should basically be the device name. So only room name and device name, no function.

Format: "[room name] [device name] [(not needed if is "main") function]"
Requirements:
	- All first character of each word is capitalized
	- Only alphanumerics and spaces are allowed
Legend:
	- [room name]: The name of room in which the device is in, e.g. Living Room, Kitchen, Bedroom...
	- [device name]: See Section 1 Device above.
	- [function]: If the entity is not the "main" device, this should be the function of the entity within the device e.g. LED Indicator, Thermostat, Cloud Connection.

Example:
	- Living Room [room name] AC GE [device name] Thermostat [function] => Living Room AC GE Thermostat
	- Bedroom [room name] Bulb 1 [device name] Power Switch [function] => Bedroom Bulb 1 Power Switch
	- "main" [label] 

Special case:
	- If the Entity is also tagged as "hidden main", it means that that Entity is ALSO the main controller of the Device, but is hidden in favor of another Entity for better UX and control. For example, if a Plug is controlling a lamp, then the main controller of that Plug, whose main controller is a Switch Entity. Now, if I want that Entity to appear on the dashboard as a Light instead of a Switch, I would have to change the "Show switch as..." option in the Entity settings. This would effectively hide the Switch and create a new Light Entity dependent on the status of the Switch. That's why, to differentiate this, for ease of development later, I label the Switch as "hidden main" and the Light as "main".

2.2 Entity ID
Description: Entity ID is the ID of each variable that a Device controls (that's how I understood it from the HA docs). By definition, each ID contains a domain, which is a fixed set of device-ish stuff that HA supports, and I don't think we can change this honestly. After the domain, it should contain the room, function, and the name of the device, not the Device Name, just the [device name] in Section 1. More on this in the format.

Format: "[domain].[room name]_[function]_[device name]"
Requirements:
    - If the term has spaces, convert all of them to underscore e.g. Living Room => living_room
	- Only lowercased alphanumerics and underscores are allowed

Legend:
	- [domain]: one of the domains provided by HA. From what I read, I don't think I can change this, other than going deep into the database and change some configs. For my own home now, I think the list they have is perfectly fine.
	- [room name]: The name of room in which the device is in, e.g. living_room, kitchen, bedroom... 
	- [function]: The function of the entity within the device e.g. led_indicator, thermostat, cloud_connection...
	- [device name]: The name of the device.

