---
tags: how-to, unreal-engine
publish: true
---

# Overview

- Create setting class based on `UObject`
	- Define `Config=ConfigName` in `UCLASS` meta-data specifiers
	- Create and add variables
- Call `ISettingsModule::RegisterSettings` in `StartupModule` to register
- Call `ISettingsModule::UnregisterSettings` in `ShutdownModule` to unregister

Note: Only bind settings in editor module, keep settings object in non-editor module

---

# Links

https://www.programmersought.com/article/28727637398/
https://docs.unrealengine.com/4.26/en-US/ProductionPipelines/Plugins/