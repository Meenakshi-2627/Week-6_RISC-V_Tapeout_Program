## Day 1 — Directory structure and OpenLane quick start

<img src="Images/openlane_logo.png" alt="OpenLane logo" width="400" height="120" />

Displayed at 400×120 px (replace `Images/openlane_logo.png` with a higher-resolution logo if you have one).

### Directory structure

If you'd like to view the directory structure --> [click here](Files/Directory_Structure)

> Note: The link above opens the `Files/Directory_Structure` file inside this `Day-1` folder.

---

### Terminal commands (images expected)

Below are the terminal commands you provided. Next to each command I list the image filename you should place under `Day-1/Images/` so the README can show the screenshots or illustrations.

1) export PDK_ROOT=/home/vsduser/Desktop/work/tools/openlane_working_dir/pdks
	- image: `Images/cmd_export_PDK_ROOT.png`
	- explanation: Sets the `PDK_ROOT` environment variable to the path where the process design kits (PDKs) live. This tells OpenLane, PDK tools, and containerized flows where to find technology files (GDS, LEF, liberty, etc.).
	- imaginative note: Picture a toolbox location tag—this command pins the PDK toolbox to a known shelf so the flow can fetch the right parts.

2) cd ~/Desktop/work/tools/openlane_working_dir/openlane
	- image: `Images/cmd_openlane_dir.png`
	- explanation: Moves your shell into the OpenLane repository directory. From here you invoke the flow scripts and run the environment that expects the OpenLane tree.
	- imaginative note: This is like stepping onto the factory floor before turning on the machines.

3) alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
	- image: `Images/cmd_alias_docker.png`
	- explanation: Creates a shell alias so the `docker` command actually runs the OpenLane container with the current directory mounted at `/openLANE_flow`, the `PDK_ROOT` mounted as well, and the environment variable passed through. It also maps the container user to your host UID/GID so generated files have correct ownership.
	- imaginative note: Think of it as wiring the container into your project folder and telling it who the owner is.

4) docker
	- image: `Images/cmd_docker.png`
	- explanation: Runs the alias above (starts the OpenLane container interactively). Once started, you'll be inside the container with the OpenLane flow available.
	- imaginative note: Entering the workshop—the tools and scripts become available inside a self-contained environment.

5) cd designs
	- image: `Images/cmd_cd_designs.png`
	- explanation: Switch into the `designs` folder inside the OpenLane flow where you create or import specific designs to run through the flow.
	- imaginative note: Going to the specific workbench for each chip project.

6) %package require openlane 0.9
	- image: `Images/cmd_tcl_package_require_openlane_0_9.png`
	- explanation: A Tcl command used within the OpenLane TCL environment (or `flow.tcl`) to ensure the `openlane` package v0.9 is available. It locks the flow to a compatible package version.
	- imaginative note: Like checking that the correct model of the machine is installed before you start.

7) %prep -design picorv32a
	- image: `Images/cmd_tcl_prep_design_picorv32a.png`
	- explanation: Prepares the `picorv32a` design inside the OpenLane environment—fetches sources, runs initial setup, and arranges the project structure the flow expects.
	- imaginative note: Prepping the blueprint and raw materials for assembly.

8) %run_synthesis
	- image: `Images/cmd_tcl_run_synthesis.png`
	- explanation: Starts the synthesis stage of the flow. The toolchain converts RTL (Verilog) into a gate-level netlist mapped to the chosen PDK.
	- imaginative note: The design's skeleton is forged into a machine language blueprint.

---

### How to add images

1. Place your screenshots or image files in `Day-1/Images/` with the exact filenames listed above.
2. Replace `Images/openlane_logo.png` with the OpenLane logo file.
3. If you want the README to show the command images inline, open the README and add Markdown image lines like:

	<img src="Images/cmd_export_PDK_ROOT.png" alt="export PDK_ROOT" width="900" />

4. Commit and push the images so collaborators can view them on GitHub.

---

If you'd like, I can also embed the command screenshots into this README now (using the filenames above) once you upload them into `Day-1/Images/`.

