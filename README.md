[![rebol](https://github.com/user-attachments/assets/9088597c-7018-49d5-a31d-81950288c945)](https://rebol.tech)

[![Test Rebol installer](https://github.com/Oldes/install-rebol/actions/workflows/test.yml/badge.svg)](https://github.com/Oldes/install-rebol/actions/workflows/test.yml)

# Rebol Install Action

This Action can install
    [Rebol](https://github.com/Siskin-framework/Rebol)
to a virtual machine of GitHub Actions. 


## Usage

Include this in your workflow:

```yml
 - uses: oldes/install-rebol@v3.18.0
```

These inputs are allowed:

 - `version` -- an available Rebol release version (for example: `3.18.0`)
   _Default:_ empty; installs Rebol version `3.18.0`.
 - `product` -- one of available product build types (`base`, `core` or `bulk`)
   _Default:_ empty; installs the `core` version.

### Working Example

```yml
name: Rebol Demo

on:
  push:
    branches:
      - master

jobs:
  build:
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        os: ["ubuntu-latest", "windows-latest", "macos-latest"]
    steps:
    - uses: actions/checkout@v3
    - uses: oldes/install-rebol@v3.18.0
    - name: Test Rebol
      run: ./rebol3 -v
      shell: bash
```

Real life usage example can be seen for example at this [Build Rebol workflow](https://github.com/Siskin-framework/Builder/actions/runs/759470676/workflow).
