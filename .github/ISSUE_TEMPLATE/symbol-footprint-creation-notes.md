---
name: Symbol/footprint creation notes
about: Not for public use
title: ''
labels: ''
assignees: ''

---

Please check or create these parts:

PARTS

Please click "quote reply" on this message then click "Comment" to save your copy.

Then click each checkbox after each stage is complete.

## Checklist

- [x] Make sure your name and email address are set up in git on your computer.

### Step 1: Check for symbols and parts in official libraries

- [ ] Check whether the required parts exist.
- [ ] Check whether an identical part exists with a different part number. These should be added as an [alias](https://kicad-pcb.org/libraries/klc/S6.2/).

If either the symbol or footprint already exists, check that:

- [x] Symbol and footprint are correct and suitable according to the datasheet.
- [x] Symbol has the [footprint filter properly set](https://kicad-pcb.org/libraries/klc/S5.2/).
- [x] Symbol and footprint pin mapping is correct for this part.
- [x] Footprint has a [3D model set](https://kicad-pcb.org/libraries/klc/F9.3/).

### Step 2: Create/modify required parts

- [ ] Make or modify the parts according to the [Kicad Library Conventions](https://kicad-pcb.org/libraries/klc/).
- [ ] **symbols**: add a link to the datasheet.
- [ ] **symbols**: fully set the [footprint filter](https://kicad-pcb.org/libraries/klc/S5.2/).
- [ ] **symbols**: set any pin-identical parts in the same datasheet as an [alias](https://kicad-pcb.org/libraries/klc/S6.2/).
- [ ] **footprints**: check whether the footprint should be created by modifying some values in [kicad-footprint-generator](https://github.com/pointhi/kicad-footprint-generator/) (also see [here](https://kicad-pcb.org/libraries/contribute/#_footprint_creation_scripts)).
- [ ] **footprints**: set a 3D model [even if the model doesn't exist](https://kicad-pcb.org/libraries/klc/F9.3/).

### Step 3: Create Pull Request in kicad official libraries

- [ ] Follow instructions for [making a Pull Request](https://kicad-pcb.org/libraries/contribute/#_making_a_pull_request) using your own fork of [kicad-symbols](https://github.com/KiCad/kicad-symbols) or [kicad-footprints](https://github.com/KiCad/kicad-footprints).

If you've created a footprint and a symbol, a Pull Request will be required in each one.

- [ ] Place the part in the correct `.pretty` directory (for a footprint) or inside the correct new or existing `.lib` file (for a symbol).
- [ ] Add a screenshot to your Pull Request.
- [ ] Add a **link to this issue** in the Pull Request.
- [ ] Fix any detected problems when you create the Pull Request, and commit the changes.
- [ ] If the footprint was created with [kicad-footprint-generator](https://github.com/pointhi/kicad-footprint-generator/), create a Pull Request with the new values in [that repository](https://github.com/pointhi/kicad-footprint-generator/) first.

### Step 4: Create Pull Request in kicad-jb-public

For the [kicad-jb-public](https://github.com/jbots/kicad-jb-public) repository, both symbol and footprint are added to the **same repository**.

The rules for where to place the parts are different to those for the official libraries:

- [ ] **symbols**: create a **new** `.lib` file for the part in the `sym` directory.
- [ ] **footprints**: create a new `.kicad_mod` file in the `fp.pretty` directory.

- [ ] Create a Pull Request in this repository with the part number as the title and a link to this issue in the text.

### Step 5: Follow instructions of Kicad librarians

- [ ] Make any changes required by the Kicad librarians to make the part suitable for inclusion in the official libraries.
