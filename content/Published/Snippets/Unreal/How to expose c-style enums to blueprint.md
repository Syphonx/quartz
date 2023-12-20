---
tags: snippets, unreal, cpp, blueprint
publish: true
---

```cpp
// EnumFile.h
namespace EAxis
{
	enum Type
	{
		None,
		X,
		Y,
		Z,
	};
}

// File.h
UPROPERTY(EditDefaultsOnly)
TEnumAsByte<EAxis::Type> BoxAxis;
```