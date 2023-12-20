---
tags: snippets, unreal, cpp, blueprint
publish: true
---

```cpp
template<typename T>
static FString EnumToString(const FString& InEnumName, const T InEnumValue)
{
	UEnum* FoundEnum = FindObject<UEnum>(ANY_PACKAGE, *InEnumName);
	return *(FoundEnum ? FoundEnum->GetNameStringByIndex(static_cast<uint8>(InEnumValue)) : "null");
}
```