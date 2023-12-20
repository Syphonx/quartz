---
tags: snippets, source-control, perforce
publish: true
---

# Table of contents

- [[#Useful Commands|Useful Commands]]
	- [[#Useful Commands#Check if a file is ignored|Check if a file is ignored]]
	- [[#Useful Commands#Remove files in CL, keeping workspace|Remove files in CL, keeping workspace]]
	- [[#Useful Commands#Submit with progress indicator|Submit with progress indicator]]
	- [[#Useful Commands#Submit in parallel|Submit in parallel]]
	- [[#Useful Commands#Submit in parallel and dont re-transfer files the server already has|Submit in parallel and dont re-transfer files the server already has]]
	- [[#Useful Commands#Fast Reconcile of local files that have been edited, added, deleted and with special characters in their name|Fast Reconcile of local files that have been edited, added, deleted and with special characters in their name]]
	- [[#Useful Commands#Show me files that were ignored:|Show me files that were ignored:]]
	- [[#Useful Commands#Show me files that were ignored but need to be added|Show me files that were ignored but need to be added]]
	- [[#Useful Commands#Why something was ignored:|Why something was ignored:]]
	- [[#Useful Commands#See which files are out of sync from worktree|See which files are out of sync from worktree]]
	- [[#Useful Commands#Force resync only deleted files|Force resync only deleted files]]
	- [[#Useful Commands#Find size of a depo|Find size of a depo]]

---

### Check if a file is ignored
```bash
p4 ignores -i -v the_path_to_the_file_you_want_to_check
```

### Remove files in CL, keeping workspace
```bash
p4 revert -k -c changelist# //... 
```

### Submit with progress indicator
```bash
p4 -I submit
```

### Submit in parallel
```bash
p4 -I submit -c 5 --parallel=threads=12
```

### Submit in parallel and dont re-transfer files the server already has
```bash
p4 -I submit -c 5 --noretransfer 1 --parallel=threads=12
```

### Fast Reconcile of local files that have been edited, added, deleted and with special characters in their name
```bash
p4 reconcile -meadf UnrealEngine\\Engine\\Binaries...
```

### Show me files that were ignored:
```bash
p4 reconcile -nI UnrealEngine\\Engine\\Binaries...
```

### Show me files that were ignored but need to be added
```bash
p4 reconcile -naI UnrealEngine\\Engine\\Binaries...
```

### Why something was ignored:
```bash
p4 ignores -v -i UnrealEngine\\Engine\\Binaries\\ThirdParty\\svn\\Mac\\lib\\apr.exp
```

### See which files are out of sync from worktree 
```bash
p4 status -I -mead UnrealEngine\\Engine\\...
```

### Force resync only deleted files
```bash
	p4 clean -I -ead UnrealEngine\\Engine\\Source\\Runtime...
```

> [!note]
> Note: Using -m might skip files if you copied over stuff recently
> - -a Added files: Find files in the workspace that have no corresponding files in the depot and delete them.
> - -d Deleted files: Find those files in the depot that do not exist in your workspace and add them to the workspace.
> - -e Edited files: Find files in the workspace that have been modified and restore them to the last file version that has synced from the depot.
> - -m Use fast check (file timestamps) instead of slower CRC check
> - (p4 clean => p4 reconcile -w)

### Find size of a depo
```bash
	p4 sizes -s -a -h //depot/...
	> 	//depot/... 50550 files 43.7G bytes
```