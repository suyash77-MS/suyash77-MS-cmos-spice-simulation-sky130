# 🏆 SKY130 CMOS Inverter Design, Characterization, and PVT-Aware Low-Power Optimization

## 🚀 Overview
A **hands-on, silicon-ready** project on CMOS inverter design, simulation, and robustness evaluation using **NGSPICE** and **SKY130 PDK**.  
Focused on **Id–Vds/Vgs curves**, **VTC**, **switching threshold**, **noise margins**, **PVT corners**, and **low-power design trade-offs** — all mapped to **real-world fabrication flows**.

---

## 🔧 Tools & Technologies Used

<img height="28" src="https://img.shields.io/badge/NGSpice-1F72B5?logo=electrical-engineering&logoColor=white">
<img height="28" src="https://img.shields.io/badge/SKY130%20PDK-FF6600?logo=chip&logoColor=white">
<img height="28" src="https://img.shields.io/badge/GtkWave-4B8BBE?logo=waveform&logoColor=white">
<img height="28" src="https://img.shields.io/badge/Magic%20VLSI-6A0DAD?logo=magic&logoColor=white">
<img height="28" src="https://img.shields.io/badge/OpenLane-007ACC?logo=verilog&logoColor=white">
<img height="28" src="https://img.shields.io/badge/KLayout-FF0000?logo=layout&logoColor=white">
<img height="28" src="https://img.shields.io/badge/OpenROAD-228B22?logo=road&logoColor=white">
<img height="28" src="https://img.shields.io/badge/Yosys-FFD700?logo=logic&logoColor=black">
<img height="28" src="https://img.shields.io/badge/OpenSTA-1E90FF?logo=timing&logoColor=white">

---

## 📚 Key Concepts Learned

### 📐 **MOSFET Fundamentals**
- NMOS & PMOS structure, W/L ratios, threshold voltage \(V_t\)  
- **Id–Vds** and **Id–Vgs** plotting for linear & saturation regions  
- Channel-length modulation \(\lambda\) and mobility \(\mu\)

### ⚡ **CMOS Inverter Design**
- Constructed CMOS inverter in SPICE  
- Derived and verified **Voltage Transfer Characteristics (VTC)**  
- Balanced PMOS/NMOS sizing for symmetrical switching

### 📊 **Noise Margin & Robustness**
- Measured **NMH** & **NML**  
- Evaluated undefined logic regions  
- Optimized device ratios for robust digital operation

### ⏱ **Dynamic Performance**
- Transient simulations for rise/fall delay  
- Load-capacitance impact analysis  
- Power–delay trade-off optimisation

### 🏭 **PVT Corner & Low-Power Analysis**
- Simulated **TT, SS, FF** process corners  
- Swept supply from **1.8 V → sub-1 V**  
- Derived guard-band guidelines for high-yield silicon

---

## 🧪 Lab Work Done
- **MOSFET DC Characterisation** → Extracted \(V_t, \mu, \lambda\)  
- **CMOS Inverter VTC Analysis** → Overlaid curves for different (W/L) ratios  
- **Transient Delay Profiling** → Measured \(t_{pHL}\) & \(t_{pLH}\)  
- **Noise Margin Exploration** → Injected glitches & tested stability  
- **Supply & Corner Sweep** → Plotted gain vs VDD, analysed PVT effects  

---




## ▶️ How to Run (NGSPICE)

```bash
# DC sweeps (Id–Vgs / Id–Vds)
ngspice scripts/dc_sweep_id_vgs.sp
ngspice scripts/dc_sweep_id_vds.sp

# VTC
ngspice scripts/inverter_vtc.sp

# Transient with load
ngspice scripts/inverter_tran.sp

# PVT sweep (example: run TT/SS/FF)
bash scripts/run_pvt_sweeps.sh

* CMOS Inverter using SKY130 PDK
.include ./models/sky130_fd_pr__nfet_01v8.spice
.include ./models/sky130_fd_pr__pfet_01v8.spice

Vdd vdd 0 1.8
Vin in 0 PULSE(0 1.8 0 10p 10p 1n 2n)

* PMOS
Mp out in vdd vdd sky130_fd_pr__pfet_01v8 W=1.5u L=0.15u
* NMOS
Mn out in 0   0   sky130_fd_pr__nfet_01v8 W=1.0u L=0.15u

Cload out 0 10f

.tran 10p 10n
.control
run
plot v(in) v(out)
.endc
.end

