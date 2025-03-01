# apkbuild-strict

Example of validation of APKBUILD files using Sparrow6 Task Check DSL

# Install

```bash
% zef install Sparrow6 --/test

```
# How to run

```bash
% s6 --task-run .@pkgrel=10
```

# Parameters

Check against current pkgrel version, pkgrel inside APKFILE should be greater

# Report examples


## Maintainer ok

![maintainer-ok](reports/maintainer-ok.jpeg)

## Maintainer broken

Extra right angle bracket 

![maintainer-broken-extra-right-angle-bracket](reports/maintainer-broken-extra-right-angle-bracket.jpeg)

Extra left angle bracket 

![maintainer-broken-extra-left-angle-bracket](reports/maintainer-broken-extra-left-angle-bracket.jpeg)

Missing name

![maintainer-missing-name](reports/maintainer-missing-name.jpeg)

Email is not valid

![maintainer-broken-email-not-valid](reports/maintainer-broken-email-not-valid.jpeg)
