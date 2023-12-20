---
tags: source-control, software, perforce
publish: true
---

# Table of contents

- [[#Performance Options|Performance Options]]
- [[#Resources|Resources]]

## Performance Options

```
p4 property -a -n P4V.Performance.ServerRefresh -v 60 
p4 property -a -n filesys.bufsize -v 2M 
p4 property -a -n net.tcpsize -v 2M
```

## Resources
- https://ikrima.dev/ue4guide/source-control/perforce-source-version-control-setup/?h=perforce
- https://articles.assembla.com/using-perforce/speed-up-your-perforce-repo-with-p4v