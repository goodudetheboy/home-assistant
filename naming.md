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
2.2 Entity ID
Description: Entity ID is the ID of each variable that a Device controls (that's how I understood it from the HA docs). By definition, each ID contains a domain, which is a fixed set of device-ish stuff that HA supports, and I don't think we can change this honestly. After the domain, it should contain the room, function, and type. More on this in the format.

Format: "[domain].[room]_[function]_[type]"
Requirements:
    - If the term has spaces, convert all of them to underscore e.g. Living Room => living_room
	- Only lowercased alphanumerics and underscores are allowed

Legend:
	- [domain]: one of the domains provided by HA. From what I read, I don't think I can change this, other than going deep into the database and change some configs. For my own home now, I think the list they have is perfectly fine.
	- [room]: The name of room in which the device is in, e.g. living_room, kitchen, bedroom... 
	- [function]: The function of the entity within the device e.g. led_indicator, thermostat, cloud_connection...
	- [type]: The variant of the device in the Room, if there are more than two. Optional, but encouraged e.g. main, 1, 2, ceiling...

