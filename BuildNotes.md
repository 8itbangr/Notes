---
tags:
  - make
  - aliases
  - .bash_profile
  - GEA
---

## Optimizer
  - Global:  `OPTIMIZE=s` / `OPTIMIZE=0`
  - Single file `#pragma GCC optimize ("Og")`.  Can also do push/pop. "O0" is no optimization.
  - https://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html
  - `SOURCE_FILES_TO_NOT_OPTIMIZE`

## Compiler options
 - RX: https://gcc.gnu.org/onlinedocs/gcc/RX-Options.html

## GEA Aliases (come into [.bash_profile](~/.bash_profile) from applcommon via ~/.gea_bash_profile_bootstrap)
 - `make` will run a make on 8 cores
 - `makey` builds for release
 - `maken` builds for not release
 - `subup` updates all submodules recursively

## Other useful build things
 - `make -j8 distclean` thoroughly cleans a build, using 8 cores
 - `lcov` TDD + coverage
 - `lcov_silent` just re-runs coverage

 ## Parametric/Framework
 - Build: `dmake -f pyramid.mk -j7 DEBUG=Y RELEASE=N framework`
 - Copy from RC17 `build` directory to parametric repo
 - Wipe `build` directory from parametric
 - Then you can build the parametric

## ERD lock
If you get the message that you've changed a locked ERD, but haven't, use the build command 'erd_lock_update`
