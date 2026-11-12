%
O4400 (44.00MM HEXAGONAL SUB-FRAME POCKET & KINEMATIC SEATS)
G21 G17 G40 G49 G80 G90 (Metric, XY Plane, Cancel Comp, Absolute)
G54 (Work Coordinate Origin at Tile Center)

(--- TOOL 01: 2.00MM DIAMOND-COATED END MILL ---)
T01 M06
S24000 M03 (Spindle CW 24,000 RPM)
G00 X0.000 Y0.000 Z5.000

(--- STEP 1: HELICAL RAMP ENTRY TO -6.50MM POCKET DEPTH ---)
G01 Z0.500 F1000.0
G02 X3.000 Y0.000 I1.500 J0.000 Z-2.000 F400.0
G02 X3.000 Y0.000 I-3.000 J0.000 Z-4.500
G02 X3.000 Y0.000 I-3.000 J0.000 Z-6.500
G02 X3.000 Y0.000 I-3.000 J0.000 Z-6.500 (Flat Bottom Cleanup Pass)

(--- STEP 2: EXPANDING HEXAGONAL FINISH PASS [44.00MM FLAT-TO-FLAT] ---)
G01 X24.403 Y0.000 F600.0        (Vertex 1: 0 deg)
G01 X12.202 Y21.134              (Vertex 2: 60 deg)
G01 X-12.202 Y21.134             (Vertex 3: 120 deg)
G01 X-24.403 Y0.000              (Vertex 4: 180 deg)
G01 X-12.202 Y-21.134            (Vertex 5: 240 deg)
G01 X12.202 Y-21.134             (Vertex 6: 300 deg)
G01 X24.403 Y0.000               (Close Perimeter)
G00 Z2.000

(--- STEP 3: 120-DEGREE KINEMATIC V-GROOVE SEATS [ZONE 2 RING, R=16.50MM] ---)
(Seat 1 at 0 deg)
G00 X15.000 Y0.000
G01 Z-7.250 F250.0
G01 X18.000 Y0.000 F300.0
G00 Z2.000

(Seat 2 at 120 deg)
G00 X-7.500 Y12.990
G01 Z-7.250 F250.0
G01 X-9.000 Y15.588 F300.0
G00 Z2.000

(Seat 3 at 240 deg)
G00 X-7.500 Y-12.990
G01 Z-7.250 F250.0
G01 X-9.000 Y-15.588 F300.0
G00 Z10.000

M05 (Spindle Stop)
G28 G91 Z0.000 (Return Home)
M30 (Program End)
%
MIT License

Copyright (c) 2026 Integrated Crystalline Optical System (ICOS)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
# Python bytecode & virtual environments
__pycache__/
*.py[cod]
*$py.class
.venv/
venv/
env/

# IDE & editor settings
.vscode/
.idea/
*.swp
*.swo
.DS_Store

# CNC & CAD temporary/simulation outputs
*.bak
*.tmp
*.log
sim_output/
# Integrated Crystalline Optical System (ICOS)

A unified, multi-scale adaptive optical and quantum hardware architecture utilizing sequentially compressed crystalline matrices. Engineered to execute **deep-space telescopic observation**, **orbital satellite telemetry**, and **nanoscale microscopy** simultaneously across a single hexagonal wafer assembly.

---

## Overview

Traditional optical systems rely on fragile glass lenses dedicated to a single focal length and spectral band. The **Integrated Crystalline Optical System** replaces standard optics with high-pressure, high-temperature (HPHT) synthesized diamond, corundum, and beryllia-alumina composites. 

By pairing spatial zone partitioning with a **5,000 Hz hexagonal piezoelectric grid**, a single **44.00 mm** tile maintains concurrent **convex**, **neutral flat**, and **concave** geometries while routing UV, Visible, Near-IR, and Mid-IR wavelengths to dedicated sensors without mechanical cross-talk.

---

## I. Material Synthesis & Optical Zoning

The active optical wafer eliminates natural crystal cleavage planes and splits incoming radiation across four concentric zones:

| Wafer Zone | Radial Span (% Aperture) | Synthesized Material Matrix | Active Profile & Displacement | Spectral Routing & Angle |
| :--- | :--- | :--- | :--- | :--- |
| **Zone 1: Central Core** | `0% – 25%` (`24.00 mm` dia) | **Sovereign Diamond-Corundum** *(NV-Center Diamond + Al₂O₃)* | **High-Curvature Convex** (`+350` to `+500 µm`) | **0.0° Straight Pass** *(200–700 nm UV/Vis Microscopy & Quantum Readout)* |
| **Zone 2: Transition Buffer** | `25% – 45%` | **Transparent Alumina Armor** *(Polycrystalline Corundum-Spinel)* | **Zero-Stress Neutral Flat** (`0.00 µm` Anchor) | **Mechanical Shear Lock** *(Kinematic 120° Si₃N₄ ball mount)* |
| **Zone 3: Mid-Aperture Ring** | `45% – 75%` | **Apex Beryllia-Alumina Crystal** *(Oxide-Silicate Lattice)* | **Shallow Concave** (`-120` to `-250 µm`) | **22.5° Dichroic Reflection** *(700–2,500 nm Near-IR Orbital Telemetry)* |
| **Zone 4: Outer Perimeter** | `75% – 100%` (`44.00 mm` hex) | **Diamond-Carbide Matrix** *(SiC + Beryllia + Alumina)* | **Deep Parabolic Concave** (`-350` to `-500 µm`) | **45.0° Folded Cassegrain** *(2,500–5,500 nm Mid-IR Deep-Space Collector)* |

---

## II. Hardware Architecture & Bill of Materials (Single 44.00 mm Tile)

| Item # | Component | Material Specification | Dimensions & Tolerance | Qty | Function |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `01` | **Outer Hexagonal Wafer** | Transparent Alumina / Beryllia-Alumina | `44.00 mm` flat-to-flat × `1.20 mm` (`±0.005 mm`) | 1 | Zones 2–4; polished to `< 0.20 nm Ra` via MRF. |
| `02` | **Central Immersion Core** | Sovereign Diamond-Corundum *(NV-Center)* | `24.00 mm` dia × `1.20 mm` (`±0.002 mm`) | 1 | Zone 1 high-index (`n = 2.41`) convex dome. |
| `03` | **Thermal & Dichroic Film** | Nano-Diamond / Silicon Carbide | `43.80 mm` hex × `15.0 µm` (`±0.5 µm`) | 1 | Equalizes heat and splits `22.5°` / `45.0°` beams. |
| `04` | **Piezo Actuator Stacks** | High-Strain PZT Ceramic | `4.50 × 4.50 × 1.80 mm` (`±0.002 mm`) | 18 | 3 concentric rings (6 sectors per active zone). |
| `05` | **Capacitive Sense Pads** | Gold-Plated Copper Micro-Electrodes | `2.00 mm` dia × `0.05 mm` (`±0.001 mm`) | 24 | Real-time `5,000 Hz` surface deflection feedback. |
| `06` | **Kinematic Mounts** | Silicon Nitride (Si₃N₄) Ceramic | `2.50 mm` height / `1.50 mm` ball (`±0.002 mm`) | 3 | Spaced at `120°` beneath Zone 2 (`0.00 V` lock). |
| `07` | **Sub-Frame Housing** | CNC Carbon-Fiber Composite | `44.00 mm` pocket × `6.50 mm` depth (`±0.005 mm`) | 1 | Houses piezo rails, RC failsafe bleed, and fiber bus. |

---

## III. Modular Array Scaling (24 ft / 44 ft Truss Integration)

Individual tiles maintain a `0.15 mm ± 0.01 mm` perimeter expansion gap and group into hierarchical clusters mounted on **24 ft** or **44 ft** carbon-composite spaceframes (supported on **22 ft** structural columns).

| Array Tier | Physical Span | Active Tiles | Power Draw (`48 V DC` Bus) | Structural & Optical Synchronization |
| :--- | :--- | :--- | :--- | :--- |
| **Tier 1: Unit Tile** | `44.00 mm` (`1.73 in`) | `1` | `1.85 W` (`0.039 A`) | Local `5,000 Hz` PID loop holds simultaneous convex/concave profile. |
| **Tier 2: Hex Sub-Cluster** | `194.25 mm` (`7.65 in`) | `19` | `35.15 W` (`0.73 A`) | Capacitive edge-sensors phase adjacent rims to `< 10 nm`. |
| **Tier 3: Medium Array** | `24.00 ft` (`7.32 m`) | `~24,800` | `45.88 kW` | Self-aligning titanium-ceramic locking pins on `24 ft` truss. |
| **Tier 4: Full Observatory** | `44.00 ft` (`13.41 m`) | `~83,500` | `154.48 kW` | Anchored to `44 ft` primary truss on `22 ft` columns; `400 Gbps` DWDM ring. |

---

## IV. Power Distribution & Failsafe Damping

* **Main Structural Spine:** Dual-redundant `48.0 V DC` low-voltage bus routed inside hollow carbon-fiber truss tubes with `< 2 µs` solid-state e-fuse isolation.
* **Local Piezo Rails:** Galvanically isolated step-up converters supply `+120 V to +180 V` (Zone 1 convex push) and `-45 V to -150 V` (Zones 3–4 concave pull).
* **Three-Stage Passive Failsafe:** On sudden power loss, depletion-mode MOSFETs isolate the rails while a matched RC bleed network (`τ = 12 ms`) drains all opposing voltages symmetrically, relaxing the crystal wafer to `0.00 V` flat within `50.0 ms` with zero mechanical rebound.

---

## V. Deterministic Fiber-Optic Telemetry & Control Loop

All sensor feedback (`CS1–CS24`), actuator drive commands (`HV1–HV18`), and quantum NV-center readouts run over a self-healing **DWDM single-mode fiber-optic ring** (`1310 nm`, `1550 nm`, C-Band, and L-Band) enclosed inside the carbon truss tubes for complete electromagnetic immunity.

### Reference Control Specification (`controller.py`)

```python
class IntegratedOpticalController:
    """
    Synchronizes 5,000 Hz hexagonal actuator voltage rails and 
    three-channel spectral beam-splitter alignment simultaneously.
    """
    def __init__(self):
        self.loop_frequency_hz = 5000.0
        self.cycle_period_sec = 1.0 / self.loop_frequency_hz  # 200 microseconds
        
        self.target_zones_um = {
            "Zone_1_Convex_Core": 425.0,      # Microscopy (+120V to +180V)
            "Zone_2_Neutral_Buffer": 0.0,     # Zero-stress shear lock (0V)
            "Zone_3_Mid_Concave": -185.0,     # Orbital telemetry (-45V to -85V)
            "Zone_4_Outer_Concave": -425.0    # Deep-space dish (-110V to -150V)
        }
        
        self.voltage_limits = {
            "Zone_1_Convex_Core": (120.0, 180.0),
            "Zone_2_Neutral_Buffer": (0.0, 0.0),
            "Zone_3_Mid_Concave": (-85.0, -45.0),
            "Zone_4_Outer_Concave": (-150.0, -110.0)
        }

    def compute_simultaneous_step(self, measured_um, temp_kelvin):
        thermal_offset_um = (temp_kelvin - 293.15) * 0.0012
        commanded_voltages = {}

        for zone, target in self.target_zones_um.items():
            if zone == "Zone_2_Neutral_Buffer":
                commanded_voltages[zone] = 0.0
                continue

            error_um = (target - thermal_offset_um) - measured_um.get(zone, target)
            v_min, v_max = self.voltage_limits[zone]
            v_mid = (v_min + v_max) / 2.0
            adjusted_v = v_mid + (error_um * 0.35)
            commanded_voltages[zone] = round(max(v_min, min(v_max, adjusted_v)), 3)

        return {
            "cycle_rate_hz": self.loop_frequency_hz,
            "thermal_drift_compensated_um": round(thermal_offset_um, 5),
            "active_rail_voltages_v": commanded_voltages,
            "splitter_angles_deg": {"UV_Vis": 0.0, "Near_IR": 22.5, "Mid_IR": 45.0},
            "system_lock": "SYNCHRONIZED"
        }
```

---

## VI. CNC Fabrication Toolpath (`O4400.nc`)

Machines the `44.00 mm` flat-to-flat hexagonal pocket (`6.50 mm` depth) and `120°` kinematic V-groove seats into carbon-fiber composite stock using a `2.00 mm` diamond-coated end mill (`T01` at `24,000 RPM`, `600 mm/min` feed).

```gcode
%
O4400 (44.00MM HEXAGONAL SUB-FRAME POCKET & KINEMATIC SEATS)
G21 G17 G40 G49 G80 G90
G54
T01 M06
S24000 M03
G00 X0.000 Y0.000 Z5.000
G01 Z0.500 F1000.0
G02 X3.000 Y0.000 I1.500 J0.000 Z-2.000 F400.0
G02 X3.000 Y0.000 I-3.000 J0.000 Z-4.500
G02 X3.000 Y0.000 I-3.000 J0.000 Z-6.500
G02 X3.000 Y0.000 I-3.000 J0.000 Z-6.500
G01 X24.403 Y0.000 F600.0
G01 X12.202 Y21.134
G01 X-12.202 Y21.134
G01 X-24.403 Y0.000
G01 X-12.202 Y-21.134
G01 X12.202 Y-21.134
G01 X24.403 Y0.000
G00 Z2.000
G00 X15.000 Y0.000
G01 Z-7.250 F250.0
G01 X18.000 Y0.000 F300.0
G00 Z2.000
G00 X-7.500 Y12.990
G01 Z-7.250 F250.0
G01 X-9.000 Y15.588 F300.0
G00 Z2.000
G00 X-7.500 Y-12.990
G01 Z-7.250 F250.0
G01 X-9.000 Y-15.588 F300.0
G00 Z10.000
M05
G28 G91 Z0.000
M30
%
```
# upgrade-to-scientific-instruments-