# Experiment 02: Private Venator Model, Codex and Universal Modder

## Objective

Test the **actual** Universal Modder image to 3D pipeline with an accurate looking, private Venator class Star Destroyer fan art model. This experiment must run only in this independent repository on the owner's Windows laptop. The original Clone Wars Command / attack cruiser repository is off limits.

**This is an experimental prototype, not a verified game quality or canon accurate ship.**

## Setup

1. Open GitHub Desktop, select `UniversalModder`, and fetch and pull the current main branch. The local path is the root of the cloned `SergiusCommodus/UniversalModder` repository.
2. Open that folder in VS Code. Open Terminal > New Terminal, choosing PowerShell.
3. Verify the existing installations with `git --version`, `codex --version`, `python --version`, `uv --version`, and `blender --version` (Blender may not be on PATH even when its app is installed).
4. If Codex is missing, install it from the official OpenAI Windows installation instructions: https://github.com/openai/codex . Do not run random installer commands from unverified websites.
5. In the ordinary PowerShell terminal (not inside the Codex prompt), run `codex plugin marketplace add rehan-remade/universal-modder`, then `codex plugin add universal-modder@universal-modder`. Review the external plugin before installing.
6. Check `um --help`. If `um` is not found, first restart the terminal. If still absent, ask before doing `uv tool install git+https://github.com/rehan-remade/universal-modder`. If uv is missing, arrange the project local setup with the human first.
7. Create local ignored output directory `generated/venator01` with `New-Item -ItemType Directory -Force generated\venator01`.
8. In the same PowerShell, start `codex`. Codex reads this repository's AGENTS.md. Tell it to inspect this guide.

## Before paying fal.ai

Only the generation API requires a fal account. In a local PowerShell terminal, after creating your fal.ai account and secret API key, run `um fal key set` and `um fal key status`. The key must only be pasted into the hidden local key prompt. Never paste API keys into Codex chat, GitHub, logs, screenshots or ChatGPT.

The Codex plugin may provide optional fal MCP access, but the `um fal` CLI can read the locally stored key without an exported environment variable. We do not require MCP for this experiment.

Verify live pricing before EVERY billable call:

```powershell
um fal price fal-ai/nano-banana-2
um fal price fal-ai/trellis-2
```

A November 2026 baseline is about $0.08 for a Nano Banana 2 1K image. Trellis 2 is billed by units, and 3D resolution/settings affect actual cost. Never infer final prices from the baseline or total a guaranteed cost. Ask the human to approve an exact spending cap first.

## Step A: Generate exactly one concept image

In the local PowerShell terminal, only after price approval, run:

```powershell
um fal image "A highly faithful Venator class Republic Star Destroyer from the Clone Wars, a single complete capital ship in a neutral grey studio background, entire ship visible from nose to stern, clean elevated front three quarter view showing the broad triangular arrowhead hull and two clearly separated long ventral and dorsal hull sections, distinctive twin raised command towers with broad bridge structures at the rear, long axial dorsal hangar doors, recessed side hangar openings, accurate symmetric aft engine clusters glowing blue, many individually defined surface panels and symmetric hull armor, red Republic identification stripes on a pale grey weathered hull, cinematic quality sharp hard surface industrial 3D model reference, realistic proportions, no fleet, no other ships, no people, no lasers, no explosion, no space background, no watermark, no text, no cropped edges" --aspect 16:9 --res 1K --n 1 --out generated/venator01 --name venator_concept
```

Check the actual resulting image filename (it may not always be .png). Open it and review the silhouette, symmetry, engines, bridge towers and hangar details. Stop if visibly incorrect. Do NOT automatically regenerate.

This artwork references a copyrighted fictional spacecraft. Treat the output as private fan art and do not commit or publish the image, mesh or derived files to the public repository.

## Step B: Convert to GLB

After reviewing the concept and getting explicit approval for a second paid call, invoke the pipeline with the **actual local concept image path**, e.g.:

```powershell
um fal model3d generated/venator01/venator_concept.png --engine trellis2 --texture 2048 --faces 40000 --out generated/venator01 --name venator_model
```

The command above assumes that the concept file is named `venator_concept.png`; Codex must check and substitute the actual path if needed.

The model target is 40,000 faces at the generation stage, not guaranteed finished triangles or clean topology. Record actual statistics and do not claim fidelity until visually reviewed.

## Step C: Blender inspection

1. Open Blender.
2. Click File > Import > glTF 2.0 (.glb/.gltf).
3. Browse to the local `generated/venator01` folder and import the actual GLB.
4. Select Material Preview (the sphere icon at the top right of the viewport).
5. Orbit with middle mouse button, zoom with the mouse wheel. Use Home to frame the imported scene.
6. Inspect top, bottom, rear, hangar openings, the bridge towers, engines, turret detail and textures.
7. If modifying it, save a NEW .blend file in the ignored `generated/venator01` directory. Do not overwrite the original GLB.

## Step D: Browser preview

Open the existing test viewer by running its `RUN_TEST.bat` in the local lab repo and opening `http://127.0.0.1:4173`. Use the Open Local GLB button to choose the generated model. Verify rotation, material rendering, FPS and scale. If the working viewer files have not yet been copied into this repo, they are in the independently extracted `universal_modder_test_lab` folder; the user should only copy them into this repo and not use or access the original game.

## Acceptance criteria

* A generated concept image and GLB file actually exist locally.
* The model opens in Blender without importer errors and can be rotated in the browser viewer.
* The report includes model file size, triangle count, texture sizes, generation endpoint versions, actual costs if available and visible defects.
* No changes to the Clone Wars Command repository.
* No commit or push of licensed ship artwork, assets, generated files or secrets.
* No unexpected paid API requests.
* If any of these fail, be explicit about what did not work.

## Codex task prompt

Read AGENTS.md and docs/EXPERIMENT_02_VENATOR_CODEX.md. This is a private Universal Modder test, not the game project. First inspect the tools installed in this local repository, check the real Universal Modder CLI commands, and show the cost of 1 concept image and 1 image to 3D model. Do not generate or spend until I approve. After I approve, make exactly 1 Venator concept, have me review it, then ask again before generating exactly 1 GLB. Keep outputs in generated/venator01, which is ignored from Git. Do not access other repositories, install software without approval, publish assets, or change my game. Then guide me through checking the GLB in Blender and the existing browser viewer. Report all completed steps, exact files, costs, quality problems and any tests.
