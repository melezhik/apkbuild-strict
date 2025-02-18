# apkbuild-strict

Example of validation of APKBUILD files using Sparrow6 Tack Checl DSL

# Install

```bash
% zef install Sparrow6 --/test

```
# How to run

```bash
% s6 --task-run .
```

# Report examples


## Maintainer ok

![maintainer-ok](reports/maintainer-ok.jpeg)

## Maintainer broken

Extra angle bracket 

![maintainer-negative](reports/maintainer-negative.jpeg)

Missing name

![maintainer-missing-name](reports/maintainer-missing-name.jpeg)

