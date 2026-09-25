![Rating](https://img.shields.io/jetbrains/plugin/r/stars/34429) ![Downloads](https://img.shields.io/jetbrains/plugin/d/34429) ![Version](https://img.shields.io/jetbrains/plugin/v/34429)

# Flexible Sim

Block diagrams and simulation runs for Dyad, Julia/ModelingToolkit, Modelica, and Python/SciPy models, inside JetBrains IDEs. Canvas edits write back to Dyad, Julia/ModelingToolkit, and Modelica sources; Python, plain Julia, and URDF diagrams are read-only. Flexible Sim turns the source files into live, editable block diagrams, runs them with the Julia, Python, or OpenModelica runtime, and plots the results in a Scope. The source file stays the single source of truth: every code edit updates the diagram, and for Dyad and Julia models every diagram edit writes back to the code.

**Flexible Sim is under active development.** Please leave a review on the [plugin page](https://plugins.jetbrains.com/plugin/34429-flexible-sim), open an issue, or drop us an email — your feedback shapes the roadmap.

**Free and Pro.** The free version shows and edits models of any size and runs models with up to 5 blocks, which covers every getting-started demo. Flexible Sim Pro runs models of any size and adds the Analysis, Tests, and Dashboard tabs, model diff, FMU import and run, code export, and the 3D view. Start the 30-day trial from any locked tab.

**Documentation:** the [tutorial](tutorial) walks through the editor, the canvas, and every tool window tab. The [adapter reference](reference/index.md) lists the syntax, the diagram output, and the write-back support for each language.

## Core Features

### Diagram Editor
* **Split editor** — source on the left, block diagram on the right, with the standard editor / both / preview toggle
* **Hierarchy** — double-click into subsystems, breadcrumb navigation
* **Navigation** — minimap, zoom, pan, fit to view, auto-layout, signal path tracing, go to type definition
* **Validation** — unconnected ports, algebraic loops, dimensional and unit consistency, parameter bounds, with overlays on the canvas
* **Runtime banner** — offers Detect and Settings when an open model's runtime is not configured

### Canvas Editing
* Drag blocks from the library next to the canvas, drag from a port to a port to connect them
* Ctrl+R rotate, Ctrl+I flip, F2 rename, notes, Create Subsystem from a selection
* Shift+click multi-select, rubber-band select, Ctrl+A, Esc, arrow-key nudge
* Ctrl+C/V/X, Ctrl+Z/Y, align and distribute for a multi-selection as one undo step
* Space or middle or right drag to pan, mouse wheel or Ctrl+=/-/0 to zoom, Ctrl+Shift+F to fit
* Right-click a connection for Trace Signal Path
* Double-click a block for its parameters, double-click a subsystem to enter it

### Simulation Runtimes
* **Dyad, Julia/ModelingToolkit, plain Julia DifferentialEquations.jl, Python/SciPy, and Modelica** through OpenModelica
* Adapter builds the model, a script generator writes a runtime script, the runtime process runs it, results stream into the Scope
* Settings page (File > Settings > Tools > Flexible Sim) with Browse, Detect, and Test for each runtime

### Scope and Analysis
* **Scope** — 1x1 to 4x4 subplots, a filterable signal tree with per-signal style, dual cursors with measurements, spectrum with a transfer estimate, scatter, data table, PNG/SVG/CSV export, an IDE or oscilloscope theme
* **Runs** — a run archive: pin, rename, overlay, and compare with absolute, relative, and time tolerances, with HTML/CSV reports
* **Solver** — step size over time, timing and evaluation counts, solver hints; a full solver list per runtime with a one-line hint
* **Live mode** for Julia, Dyad, and Python models, **REPL** for Julia and Dyad models
* **Simulation debugger** (Julia, Dyad, and Python) — pause, continue, step, signal breakpoints, live parameter changes
* **Linear Analysis** (Julia, Dyad, Python, and Modelica) — analysis points marked on the diagram, an operating point, Bode, Nyquist, Nichols, root locus, pole-zero, step and impulse response, a model view with matrix and code export
* **Parameter studies and optimization** (Julia, Dyad, Python, and Modelica) — sweeps, sensitivity, Monte Carlo, response optimization, parameter estimation from a measured CSV file

### Tests and Dashboard
* **Tests** — signal assertions (range, rate, settling, overshoot), baselines, regression runs, block coverage
* **Dashboard** — resizable gauges, charts, tables, a lamp, a knob, a slider, and a toggle bound to simulation signals; a knob, a slider, and a toggle tune a live run

### State Machines
* Hierarchy: composite states with a default child, parallel states, a shallow history junction
* Entry, during, and exit actions in Julia, and temporal guards (`after`, `before`, `every`)
* Validation, and code generation as plain Julia or an MTK-compatible model

### 3D View
* Multibody animation with STL, OBJ, and glTF geometry, and URDF robots assembled from their links and joints (needs JCEF)
* A transport bar (play, pause, step, loop, speed), a measure tool, a section plane, and front/top/right/isometric camera views
* PNG screenshot and WebM video export

### Interoperability
* **FMU** import as a library block and co-simulation (FMI 2.0/3.0). Export builds a real, loadable FMU for a Modelica model through OpenModelica, or an FMU source package for the other four languages. **URDF** robots open as a block diagram with the assembled robot in the 3D View
* **Simulink import (experimental)** — an `.slx` model becomes a Julia/ModelingToolkit file
* **Model diff** — coloured diff against a git revision, SVG export, review checklist
* **C code generation** through ModelingToolkit
* **Extensible** — third-party plugins add language adapters through the `com.flexible.sim.simLanguageAdapter` extension point

### Getting Started Tools
* Welcome and tutorial dialog (7 parts) on first start, reopen from Help > Flexible Sim > Welcome and Tutorial
* Guided tour: 5 steps in the live IDE, from the dialog or Help > Flexible Sim > Guided Tour
* Demo project (File > New > Project > Flexible Sim Demo) with twelve ready-to-run models in three sets

### What Runs Where

| Feature | Dyad | Julia/ModelingToolkit | Plain Julia | Modelica | Python/SciPy |
|---|---|---|---|---|---|
| View the diagram | Yes | Yes | Yes | Yes | Yes |
| Edit the diagram, write back to source | Yes | Yes | No | Yes | No |
| Run and plot in the Scope | Yes | Yes | Yes | Yes | Yes |
| Live mode | Yes | Yes | No | No | Yes |
| Debugger: pause, step, breakpoints | Yes | Yes | No | No | Yes |
| Linear Analysis: Bode, Nyquist, root locus, step | Yes | Yes | No | Yes | Yes |
| Parameter studies and optimization | Yes | Yes | No | Yes | Yes |
| FMU export | Source package | Source package | Source package | Real FMU | Source package |
| State machines and C code | Yes | Yes | No | No | No |

## Getting Started

### Quick Start
1. Install the plugin from the JetBrains Marketplace
2. Create a demo project, or run Help > Flexible Sim > Add Demo Models to This Project
3. Open a `.dyad`, `.jl`, `.mo`, or `.py` model file — the split editor opens with the diagram on the right
4. Set the Julia, Python, or OpenModelica executable under Settings > Tools > Flexible Sim, or click Detect on the runtime banner
5. Run Tools > Flexible Sim > Run Simulation (Ctrl+Shift+R) and read the results in the Scope tab

### Productivity Tips
* **Ctrl+Shift+L** Auto Layout, **Ctrl+Shift+V** Validate Model, **Ctrl+Shift+E** Export Diagram
* **Ctrl+T** trace a signal path, **Ctrl+B** go to a type definition
* **Ctrl+Shift+R** run the simulation

### Troubleshooting
* **File not recognized?** Check Settings > Editor > File Types for `.mo`, `.fmu`, `.slx`, `.urdf`
* **Runtime not found?** Click Detect on the runtime banner, or set the path under Settings > Tools > Flexible Sim
* **No Dyad or Julia diagram?** Install the Flexible Julia plugin


## Made by Developers with a Passion for Simulation

The integration is the work of [Ilscipio](https://www.ilscipio.com/):

<p style="text-align:center">
<img src="https://www.ilscipio.com//wp-content/uploads/2018/11/ilscipio_soldier2-2.svg" width="200" alt="The Ilscipio Logo - A roman soldier"/>
</p>

We develop software solutions and understand the needs of engineers who model, simulate, and control physical systems. We created this plugin to make simulation work more productive in JetBrains IDEs.

* Flexible Sim is free for students and open source projects, and non-profits get a 50% discount.

## Bugs & Feature Requests

If you have any questions, feature requests, or stumble upon the occasional bug, come leave us a message:

- **Email:** info@ilscipio.com
- **Website:** [ilscipio.com](https://www.ilscipio.com/)
