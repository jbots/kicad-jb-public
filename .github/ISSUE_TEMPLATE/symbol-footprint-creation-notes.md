---
name: Symbol/footprint creation notes
about: Not for public use
title: ''
labels: ''
assignees: ''

---

Please check or create these parts:

PARTS

**Stages**

This ticket will track the six stages of making the part(s).

Each time you start a new stage, please **cut and paste** the comment box for that stage into a new comment. After submitting the comment use your mouse to click the tickboxes, and use the "edit" button the comment to fill in the answers as you go. Please don't create duplicate comments.

## Stage 1: Check for symbols and footprints in official libraries

Check for existing parts in [kicad-symbols](https://github.com/KiCad/kicad-symbols) and [kicad-footprints](https://github.com/KiCad/kicad-footprints)

Cut and paste comment box for stage 1:
```
Write here any symbols for this part (or write NO_EXISTING_SYMBOL):
Write here any alternative parts that are pin-compatible and could be added as an alias (or write NO_PIN_COMPATIBLE):
Write here any footprints that could already be used (or write NO_EXISTING_FOOTPRINT):

 - [ ] For any parts written above, carefully verify against the datasheet (or tick if no parts)
```

## Stage 2: Create/modify required parts

Cut and paste comment box for stage 2:
```
- [ ] Check whether the footprint could be created by modifying some values in [kicad-footprint-generator](https://github.com/pointhi/kicad-footprint-generator/) (or tick if no footprints needed)

Write here any footprints to be created/modified normally (or write NO_FOOTPRINT):
Write here any footprints to created/modified with scripting (or write NO_SCRIPTING):

Write here any symbols to be created/modified as new parts (or write NO_SYMBOL):
Write here any symbols to be added as an alias (or write NO_ALIAS):

- [ ] Make or modify the parts
- [ ] Satisfy **all** parts of the [Kicad Library Conventions](https://kicad-pcb.org/libraries/klc/)
```

## Stage 3: Create pull request in kicad-jb-public

For the [kicad-jb-public](https://github.com/jbots/kicad-jb-public) repository, both symbol and footprint are added to the **same repository**.

The rules for where to place the parts are different to those for the official libraries:

**Symbols**:
* create a new `.lib`/`.dcm` file for the parts directly in the `sym` directory (and not in any subdirectory)
* there shouldn't be any other parts in this library
* name the lib by appending the part number to the usual library name from kicad-symbol
* For example: if the parts are "ISL328x" and they are designed to be added to Interface_UART.lib in kicad-symbols, they should be added to a new library at the path:
`sym/Interface_UART_ISL328x.lib` (and `.dcm`)

**Footprints**:
* create a new `.kicad_mod` file directly in the `fp.pretty` directory (and not in any subdirectory)
* For example: if the package is "QFN-28_4x4mm_P0.5mm" it should be added at the path:
`fp.pretty/QFN-28_4x4mm_P0.5mm.kicad_mod`

Create a pull request (PR) in [kicad-jb-public](https://github.com/jbots/kicad-jb-public) (this repository) with the part number in the title. Make sure your branch is up to date with the repository first.

Cut and paste comment box for stage 3:
```
- [ ] Create a new branch in your fork of this repository (don't work on "main" branch)
Link to pull request in this repository:
```

## Stage 4: Make any changes to allow merging into this repository

Automatic checks will be run when you create your pull request in this repository.

The parts have not passed until you see "Check symbol _name_" or "Check footprint _name_" next to the name of **each** symbol or footprint you have created, with a green tick.

The Kicad Library Conventions can be found [here](https://kicad-pcb.org/libraries/klc/).

Any KLC rule failures must be fixed. Click on "Details" next to the failing rule for more information. If the automatic check should be ignored in this specific case, explain it below.

**Important**: Not all rules have an automatic test, so a part passing does **not** mean that it doesn't violate any rules - they must be read carefully.

Cut and paste comment box for stage 4:
```
Explanation of any failing checks that should be ignored (or write NO_IGNORE):
- [ ] All symbols and footprints are listed as passing, or failing checks explained
```

## Stage 5: Create pull requests in kicad official libraries

If you've created a footprint and a symbol, a pull request will be required in both  [kicad-symbols](https://github.com/KiCad/kicad-symbols) and [kicad-footprints](https://github.com/KiCad/kicad-footprints)

Cut and paste comment box for stage 5:
```
**Before** you create a pull request(s) tick off all the following

- [ ] Create a new branch in your fork of kicad-symbols or kicad-footprints (don't work on "master" branch)
- [ ] Make sure your branch is up to date
- [ ] Place the part in the correct `.pretty` directory (for a footprint) or inside the correct **existing** `.lib` file (for a symbol). Do not create a new symbol library unless it is absolutely unavoidable.
- [ ] Create screenshots of your parts for your Pull Requests [like this](https://kicad-pcb.org/img/klc/adding_screenshot.png).
- [ ] If the footprint was created with [kicad-footprint-generator](https://github.com/pointhi/kicad-footprint-generator/), create a pull request with the new values in [that repository](https://github.com/pointhi/kicad-footprint-generator/) **first**.

Then:

- [ ] Create pull request using template text, filling in the details and adding screenshots
- [ ] Add link to pull request for footprint in the pull request for the symbol, and vice versa

Link to kicad-footprint-generator pull request (or NO_GENERATOR_PR):
Link to footprint pull request (or NO_FOOTPRINT_PR):
Link to symbol pull request (or NO_SYMBOL_PR):
```

## Stage 6: Make required changes for parts to be merged in official libraries

At the bottom of the PR in kicad-symbols or kicad-footprints, click "Details" next to "continuous-integration/travis-ci/pr" to see any automatic recommendations for fixes to the parts.

Make any changes requested by the Kicad librarians.

Do not request a review, or send comments asking for your part to be checked. If nobody is checking the part, add more details to the pull request, including screenshots from the datasheet (of pin tables, package dimensions etc).

Cut and paste comment box for stage 6:
```
**Each time you push changes to the pull request**:
- [ ] Make any changes required by the Kicad librarians to make the part suitable for inclusion in the official libraries.
- [ ] Update the part screenshots in the **same place as the originals** by editing your comment (don't create a new comment)
- [ ] Update the PR in [kicad-jb-public](https://github.com/jbots/kicad-jb-public) (this repository) along with a comment explaining what has changed
```
