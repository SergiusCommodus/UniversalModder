# Experiment 01: Original naval command console

This is a REAL Universal Modder asset generation experiment. The separate test viewer already worked locally on Windows. We are now generating one original high quality 3D prop and evaluating it in Blender and the browser. Do not open or access the Clone Wars Command repository.

## The first asset

Name: Navy tactical command console.

A standalone, original futuristic naval bridge station with a broad angled control desk, thick industrial base, realistic machined aluminum and dark graphite body, recessed controls and switches, a central blue tactical display, small warm amber status lights, and believable exposed hardware. This is one furniture style prop designed to look convincing from front, sides and behind. No text, franchise logos or copyrighted references.

**Target:** a textured GLB that can sit convincingly inside a Three.js bridge scene, ideally 10,000 to 30,000 triangles after review. This is a target, not a guarantee.

## Safety

1. Work ONLY inside this repo and do not access the game.
2. External generators are paid services. First verify the exact official prices with `um fal price`, and wait for user approval before making generation requests.
3. Save generated material in `generated/console01/`, which is gitignored. Do not upload it to this PUBLIC GitHub repository.
4. Do not publish an image, model, screenshot or source texture without reviewing commercial licensing, provenance and visible quality.
5. When a new software tool, plugin, API key or machine permission is needed, explain it and ask before installation or configuration.

## Step 1: Prepare the isolated repo

Use GitHub Desktop to clone https://github.com/SergiusCommodus/UniversalModder.git into its own Windows directory.

The currently working viewer is still in the original local `universal_modder_test_lab` folder. Copy its `index.html`, `main.js`, `styles.css`, `server.js`, `RUN_TEST.bat`, `assets/` and `scripts/` into the cloned repo. Do not overwrite this repo's `README.md`, `CLAUDE.md` or `.gitignore`.

Test `RUN_TEST.bat` and check http://127.0.0.1:4173 opens.

## Step 2: Enable Universal Modder in Claude Code

Launch Claude Code from the root directory of this cloned repo.

Inside Claude Code, run these plugin commands one at a time:

```text
/plugin marketplace add rehan-remade/universal-modder
/plugin install universal-modder@universal-modder
```

These commands are commands for Claude Code, not PowerShell. They may install a plugin for your Claude Code environment, so review the requested permissions. Restart the Claude Code session if necessary.

Alternatively, Universal Modder's documented CLI installation is `uv tool install git+https://github.com/rehan-remade/universal-modder`; this requires uv. Do not install both methods unless needed.

Once installed and available, the local terminal command `um fal --help` should describe the asset recipes. If `um` is not available, have Claude inspect the documented plugin environment before proposing a fallback.

Blender is used for inspecting and cleaning up the resulting GLB. It is not required just to generate the model.

## Step 3: Connect fal.ai and review costs

Open https://fal.ai/dashboard/keys in your own browser. Create an API key only if you decide to use the paid generation service.

In the local terminal run:

```powershell
um fal key set
um fal key status
um fal price fal-ai/nano-banana-2
um fal price fal-ai/trellis-2
```

The key prompt is local; NEVER share the actual API key with ChatGPT, Claude messages, screenshots, or GitHub. `um fal key status` must show a masked source, not the key.

Pricing snapshot observed November 2026: Nano Banana 2 about $0.08 for a 1K image and Trellis 2 about $0.25 to $0.35 depending on resolution. Both may change. Do not run the paid commands until the live price and budget are explicitly approved.

## Step 4: Generate a clean concept image

Have Claude Code execute exactly ONE generation using the installed tool, and report the file it creates. Use a 1:1 composition, one isolated object, clean studio background, and no scene clutter.

```powershell
um fal image "A single ORIGINAL futuristic naval command console as a premium 3D game prop, shown in a clean front three quarter product view on a neutral light grey studio background, entire object clearly visible and centered. Rugged wedge shaped bridge station, brushed silver structural frame, matte dark graphite armor panels, broad sloping console deck, an integrated recessed blue tactical map screen, a handful of crisp physical buttons, twin narrow side displays, small amber indicator lights, exposed metal bolts, vents and seams, realistic manufactured construction, grounded industrial science fiction, high detail realistic materials, no humans, no environment, no floor clutter, no logos, no text, no floating displays, no wires, no watermark." --aspect 1:1 --res 1K --n 1 --out generated/console01 --name console_concept
```

Open the output image to inspect it. Stop if the object is cut off or heavily distorted. Save the actual output path.

## Step 5: Convert the concept to a real GLB

Only after the concept image is acceptable and the user approves another paid request:

```powershell
um fal model3d generated/console01/console_concept.png --engine trellis2 --texture 2048 --faces 20000 --out generated/console01 --name console_model
```

If the image extension or actual name differs, replace it using the file found in Step 4. Report the exact GLB file written, triangle count, file size, materials, texture dimensions and any visual artifacts. Automatic generation is not the same as game ready topology.

## Step 6: Inspect in Blender

1. Launch Blender and start a General project.
2. Select and delete the default cube if it is present.
3. Go to File, Import, glTF 2.0, and select the newly generated GLB file.
4. Use the middle mouse button to orbit and the mouse wheel to zoom.
5. Press Home to frame the contents of the scene, or select the model and press Numpad Decimal to frame it.
6. Open the viewport shading controls and choose Material Preview.
7. Rotate around the object to inspect all sides, its base, floating geometry, materials and silhouette.
8. Save a separate Blender file in `generated/console01/` if you make changes. Do not overwrite the original GLB.

If the model needs retopology, material fixing, disconnected part cleanup or new controls, document those issues before changing it.

## Step 7: Open the generated GLB in the local viewer

Run `RUN_TEST.bat` from the separate lab folder. In Chrome open http://127.0.0.1:4173 and use the Open Local GLB control to load the file from `generated/console01/`. Rotate and inspect it. Check that the other scenes still load.

## Deliverables

* Generated concept image in a local `generated/console01/` folder.
* Generated 3D GLB in the same folder.
* Optional cleaned Blender file, left local.
* Short experiment report with costs, asset file sizes, triangle count, texture stats, screenshots, visible defects, and suggested improvements.

## Paste to Claude Code

Read `CLAUDE.md` and `docs/EXPERIMENT_01.md`. Work strictly inside this UniversalModder repo. Set up the original command console asset experiment. First verify the local viewer and the official Universal Modder plugin and fal command versions. Do NOT access any other repo or install anything automatically. Before any paid API call, report the live price of one Nano Banana 2 concept and one Trellis 2 model, ask for approval, and then run only the approved generation. Follow the numbered steps in the experiment document. After generating the asset, walk me through opening the exact resulting GLB in Blender and the local viewer. Do not push generated binaries or private credentials to GitHub. Report the actual outcomes rather than claiming unperformed steps.
