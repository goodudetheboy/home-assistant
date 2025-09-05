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


