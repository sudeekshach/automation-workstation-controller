# 🛠️ Automation Workstation Control Using Studio 5000

An industrial automation project built using Rockwell Automation’s Studio 5000 and a workstation powered by Allen-Bradley PLCs. This project includes routines to automate a box handling process with precision using structured ladder logic and diagnostics.

## 📌 Overview

This project simulates the logic for a semi-automated vacuum-head-based box transfer workstation. The system has three core components:

1. **Main Routine** - Orchestrates execution and manages system mode.
2. **Reset Subroutine** - Resets the workstation to a predefined safe home state.
3. **Production Subroutine** - Controls a complete automated production cycle.

Each routine is built using modular ladder logic and includes timers, diagnostics, and interlocks to ensure smooth, controlled operation.

## 🤖 Workstation Overview

- **Robot Used:** Vacuum Pick-and-Place Head
- **Control Software:** [Studio 5000 Logix Designer](https://www.rockwellautomation.com/en-us/products/software/factorytalk/logix.html)
- **Controller:** Allen-Bradley CompactLogix PLC
- **Sensors and Actuators:**
  - Proximity sensors
  - Vacuum sensor
  - Indicator tower lamps
  - Barcode stop actuator
  - Box ejector
  - Conveyor motor

---

## 📂 Ladder Logic Routines

### 🔁 Main Routine

- **Function:** Controls system start, stop, and state transitions.
- **Features:**
  - Monitors stop and reset inputs.
  - Calls respective subroutines based on input and system state.
  - Activates auto mode logic.

📄 [View Main Routine](ladder_logic/Main_Routine.pdf)

---

### 🧹 Reset Routine

- **Function:** Moves all actuators and components to a known home state safely.
- **Step Highlights:**
  - Turns off all tower lights.
  - Blinks amber light to indicate reset mode.
  - Retracts all moving parts safely with delays.
  - Sets `AT_HOME` flag when complete.

📄 [View Reset Routine](ladder_logic/Reset_Routine.pdf)

---

### ⚙️ Production Routine

- **Function:** Executes a full pick-and-place cycle.
- **Step Highlights:**
  - Eject box.
  - Extend vacuum head and capture box.
  - Transfer to conveyor and release.
  - Detect box exit with proximity sensor.
  - Reset latches and return to idle.

📄 [View Production Routine](ladder_logic/Production_Routine.pdf)

---

### 🚦 Auto Process Routine

- **Function:** Manages automatic transitions when the system is in Auto Mode.
- **Highlights:**
  - Synchronizes Reset and Production routines.
  - Ensures smooth transitions using flags and timers.

📄 [View Auto Process Routine](ladder_logic/AutoProcess_Routine.pdf)

---

## 🧪 Testing & Debugging Strategies

- **Step Flags:** Used to ensure that each routine step completes before advancing.
- **Diagnostic Bits:** Allow the logic to be analyzed rung-by-rung.
- **Timers:** Smooth component motion using delay timers (250ms–2s) between steps.

---

## 🚀 How to Run

1. Open the `.ACD` file in Studio 5000.
2. Use MainRoutine to trigger reset and production cycles.
3. Monitor inputs/outputs using I/O configuration in Logix Designer.
4. Use `Test Bits` to simulate inputs if hardware is unavailable.

---

## 👨‍💻 Team & Course

- **Course:** EGR 550 - Advanced Automation Systems
- **Institution:** Arizona State University
- **Team:** Team 4 

---

## 🏷 License

This project is educational and shared under the MIT License.

---

