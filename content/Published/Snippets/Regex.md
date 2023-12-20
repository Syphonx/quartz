---
tags: snippets, regex, software
publish: true
---

# Table of contents 

- [[#Replace all strings in the format *L"Content"* with *TEXT("Content")*|Replace all strings in the format *L"Content"* with *TEXT("Content")*]]
- [[#Replace all single line c-style comments in format */** comment */* with *// comment*|Replace all single line c-style comments in format */** comment */* with *// comment*]]

---

#### Replace all strings in the format *L"Content"* with *TEXT("Content")*
> `(L"([^"]*)")` and replace with `TEXT("$2")`

#### Replace all single line c-style comments in format */** comment */* with *// comment*
> `\/\*\*([^\n\r]+?)(?:\s\*\/|[\n\r])` and replace with `//$1`