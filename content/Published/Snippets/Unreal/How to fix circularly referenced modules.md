---
tags: snippets, unreal, cs
publish: true
---

```cs
// ModuleA.Build.cs
CircularlyReferencedDependentModules.AddRange
(
	new string[]
	{
		"ModuleB"
	}
);

// ModuleB.Build.cs
CircularlyReferencedDependentModules.AddRange
(
	new string[]
	{
		"ModuleA"
	}
);
```