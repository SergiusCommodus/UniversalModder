# Universal Modder Lab

A standalone experimental workspace for evaluating 3D assets, textures, sounds, and AI workflows. **This is NOT the Clone Wars Command game repository.**

## Status

The local browser viewer has already been tested successfully on Windows. The files for that viewer are still local and must be copied into this repository if you want the viewer tracked on GitHub.

This repository is PUBLIC. Only publish original or appropriately licensed test assets. Never publish game extractions, private files, credentials, or material from another repository.

## Stage 1: Put the working lab in GitHub

1. Open GitHub Desktop and clone this repository into a new directory of its own.
2. Open the downloaded and extracted `universal_modder_test_lab` folder from the previous ChatGPT test.
3. Copy `index.html`, `main.js`, `styles.css`, `server.js`, `RUN_TEST.bat`, `assets/`, and `scripts/` into your new cloned repository directory.
4. In GitHub Desktop review ONLY the changes inside this repository. Commit with the summary `Add standalone model viewer` and push.
5. Run `RUN_TEST.bat` from the cloned repository and make sure `http://127.0.0.1:4173` still opens correctly.

Do not copy the original lab's `README.md` over this one. Preserve this project's `CLAUDE.md`, `.gitignore` and `docs/` instructions.

## Stage 2: Test a genuinely new generated asset

Open `docs/EXPERIMENT_01.md` and give its instructions to Claude Code **while Claude is running inside this repository**. The experiment is an original futuristic naval command console in a GLB file, independent of any Star Wars asset.

Claude should use the [Universal Modder toolkit](https://github.com/rehan-remade/universal-modder) only after confirming installed tools and asking for approval before paid API use or software changes.

The experiment succeeds if a new GLB exists, renders in the local viewer, has acceptable material quality and polygon count, and its generation cost and provenance are documented.

## Safety rules

* Never access, edit, copy or search the Clone Wars Command repository or its assets.
* Never install software, plugins or other tools without the owner's approval.
* No paid generation before the owner approves the exact service and estimated price.
* No upload of personal data, third-party game files, or credentials.
* Generated files remain in the separate lab folder. A human decides what can move to other projects.
* Do not commit secrets or generated bulk data.

## Current implementation

The initial work is instructions only. The functioning viewer remains on the owner's laptop until its files are copied here.
