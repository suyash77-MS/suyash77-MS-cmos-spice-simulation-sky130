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
[CMOS Spice Simulations project (1).pdf](https://github.com/user-attachments/files/22001121/CMOS.Spice.Simulations.project.1.pdf)

# CMOS Circuit Design and SPICE Simulation

# using SKY130 Technology Workshop

#### Brief Description of the course:

Thisthe workshopis focused is towards divided CMOS across circuitthe five design days andin aSPICE smart simulationway which using allows SKY130 the learner technology to grasp organized all the by concepts VLSI System if the Design. workshop The is content attended of
dedicatedly. On the first day of the workshop the emphasis was on the basics of NMOS Drain current (Id), Drain-to-source Voltage (Vds) and the

plotand betweenVgs and (^) thethe twoplot offor them. determining The second the value day focuses of Vt. The primarily third was on velocityconcentrated saturation on CMOS and basics switching of CMOS threshold inverter and VTCdynamic and simulations,the plots between where Id a (^)
lotOn ofthe equations fourth day were of thederived workshop, to find Noisethe relationships margins and between CMOS the inverter (W/L) robustness ratios of the with PMOS respect and to NMOS them was and discussed. the switching On thethreshold fifth and voltage final day(Vm). of (^)
the workshop the emphasis was on Power supply variation and Device variation. In the power supply variation, the effects of using various power
suppliesnot used. on In thethe inverterdevice variation, were observed the impact and ofwe manufacturing discussed the processesadvantages on and a single disadvantages inverter and of inverterusing a chainsmall werepower discussed. supply and the reason that it is

#### Tools Covered:

```
● NGSpice + SKY130 PDK – Open-source SPICE simulator with accurate 130 nm device models.
● NGSpice Built-in Plotter – For waveform visualization.
● VS Code / Vim – Netlist editing with syntax highlighting.
● Bash & Make Scripts – Automating multi-corner sweeps and parameter studies.
● Git & GitHub – Version control, sharing lab results, reproducibility.
```
#### Projects Covered:

1. Design & Characterization of a CMOS Inverter
    ○ Sizing PMOS/NMOS pairs
    ○ Generating VTC plots
    ○ Optimizing switching threshold and rise/fall delays
2. Noise-Margin & Delay Analysis of an Inverter Chain


```
○ Evaluating NMH/NML
○ Timing analysis through TT/SS/FF corners
○ Sub-1 V supply sweeps
```
3. PVT-Aware Low-Power Standard Cell
    ○ Building process-tolerant library cells
    ○ Parametric sweeps using scripts
    ○ Documenting guard-band guidelines for tape-out

#### What I Learned

```
● Setting up the SKY130 PDK and NGSpice for CMOS simulations.
● Extracting Id–Vds and Id–Vgs curves, understanding channel-length modulation, μ, λ, and Cox.
● Designing CMOS inverters and deriving switching-threshold equations.
● Analyzing noise margins (NMH/NML) and robustness under glitches.
● Performing transient simulations to measure rise/fall delays and power consumption.
● Sweeping VDD for low-power design and running PVT corner simulations.
● Using Bash/Make automation for large-scale SPICE sweeps.
● Integrating SPICE-verified designs into OpenLane/VSDFlow for digital implementation.
● Applying learned concepts to create silicon-ready, low-power, robust designs.
```

## INDEX:

#### 1. Basics of MOSFET

#### 2. Modes of Operation:

#### o Accumulation Mode

#### o Depletion Mode

#### o Inversion Mode

#### 3. Transfer characteristics in triode and saturation regions

#### 4. Transconductance gm in triode vs saturation

#### 5. Region conditions recap

#### 6. p-type enhancement MOSFET: modes, equations, characteristics

#### 7. Non-Ideal Effects of MOSFET:

#### o Channel Length Modulation

#### o Body Effect

#### o Effects on Threshold Voltage

#### o Subthreshold Conduction

#### 8.Introduction To SPICE Simulations

#### 9.Velocity Saturation & Basics of CMOS Inverter

#### 10.CMOS Voltage Transfer Characteristics

#### 11.Static Behavior Evaluation of CMOS

#### 12.Conclusion

#### 13.References



### MOSFET

```
Full Form: Metal Oxide Semiconductor Field Effect Transistor
● S: Source
● D: Drain
● G: Gate (metallic contact with SiO₂ insulation layer)
● B: Body (p-type substrate for n-MOS)
● L: Channel length
● W: Channel width
● tₒₓ: Oxide thickness
● SiO₂ acts as a perfect insulator
```
Why it is called Field Effect Transistor?
Indirection MOSFET, of the the current current flow. that flows between Drain (D) and Source (S) terminals is controlled by an electric field which is perpendicular to the

```
● This perpendicular control is why it is called a Field Effect Transistor (FET).
● The Gate (G) terminal is separated from the channel by a perfect insulating layer (SiO₂), hence no current (negligible) flows through the
gate terminal.
```
#### Regions (Modes) of Operation

### 1.Enhancement MOSFET:

1. Accumulation Mode
2. Depletion Mode
3. Inversion Mode


**1. Accumulation Mode**

```
Condition:Where: VGS < 0 (for n-MOS)
```
```
𝑉𝐺𝑆=𝑉𝐺−𝑉𝑆
Explanation:
● Gate connected to negative voltage ⇒ negative charges develop on the metallic gate plate.
● These negative charges attract holes (majority carriers in p-type substrate) toward the Si–oxide interface.
● This increases hole concentration near the surface ⇒ Accumulation Mode.
Capacitor Analogy:
● MOS structure behaves like a parallel plate capacitor:
o Negative charge on Gate plate.
o Positive charge (holes) on semiconductor plate.
Capacitance in accumulation mode:
𝐶𝑀𝑂𝑆=ε𝑜𝑡𝑥𝑜·𝑥𝐴, 𝐴=𝑊·𝐿
```
Equilibrium:When fully charged, (^)
𝑄−(𝐺𝑎𝑡𝑒)=𝑄+(𝑆𝐶−𝑝𝑙𝑎𝑡𝑒)
𝑄=𝐶𝑀𝑂𝑆·𝑉𝐺𝑆
If VDS > 0:
● Accumulated holes form a barrier between source and drain.
● This barrier prevents conduction ⇒
𝐼𝐷𝑆= 0 𝑓𝑜𝑟 𝑎𝑛𝑦 𝑎𝑝𝑝𝑙𝑖𝑒𝑑 𝑉𝐷𝑆


```
For n-type MOSFET:
𝑉𝐺𝑆< 0 ⇒ 𝐴𝑐𝑐𝑢𝑚𝑢𝑙𝑎𝑡𝑖𝑜𝑛 𝑀𝑜𝑑𝑒, 𝐼𝐷𝑆= 0
```
### 2. Depletion Mode

```
Condition: VGS > 0 (small positive voltage, below threshold)
Explanation:
● Positive charges develop on the Gate plate.
● These positive charges repel holes from p-type substrates near the Si–oxide interface.
● This creates a depletion region containing:
o Negative acceptor ions (fixed)
o Minority carriers (electrons)
● As VGS increases ⇒ depletion region width (W_dep) increases.
Capacitor Analogy:
● Stored charges:
o +ve on Gate metallic plate
o −ve (acceptor ions & electrons) in depletion region
● Equivalent capacitance:
𝐶𝑀𝑂𝑆=𝐶𝐶𝑜𝑜𝑥𝑥+·𝐶𝐶𝑑𝑑𝑒𝑒𝑝𝑝
```

```
Where:
𝐶𝑜𝑥=ε𝑜𝑡𝑥𝑜·𝑥𝐴, 𝐶𝑑𝑒𝑝=ε𝑊𝑠𝑐𝑑·𝑒𝐴𝑝
Observation:
● In depletion mode, 𝐶𝑀𝑂𝑆<𝐶𝑀𝑂𝑆 (𝑖𝑛 𝑎𝑐𝑐𝑢𝑚𝑢𝑙𝑎𝑡𝑖𝑜𝑛 𝑚𝑜𝑑𝑒)
● As 𝑉𝐺𝑆↑ ⇒ 𝑊𝑑𝑒𝑝↑, 𝐶𝑑𝑒𝑝↓, hence 𝐶𝑀𝑂𝑆↓
● MOS capacitance here behaves as a voltage-variable capacitor (VVC).
If VDS > 0:
● Depletion region has high resistance between source and drain ⟹ negligible current:
𝐼𝐷𝑆≈ 0
Thus,
𝑉𝐺𝑆 𝑖𝑛 𝑑𝑒𝑝𝑙𝑒𝑡𝑖𝑜𝑛 𝑚𝑜𝑑𝑒: 𝐶𝑀𝑂𝑆=𝐶𝐶𝑜𝑜𝑥𝑥+·𝐶𝐶𝑑𝑑𝑒𝑒𝑝𝑝, 𝐼𝐷𝑆≈ 0
```
**Depletion Mode of Operation**

Structure and Bias
● Considerchannel geometry an n-MOS W×L. structure with p-type substrate (Body B), n+ Source (S), n+ Drain (D), Gate (G) over oxide of thickness t_ox, and
● Apply a small positive gate bias: VGS > 0 (but below threshold Vth).

Physical Process
● Positivedepletion charge region oncontaining the metallic mainly gate negative plate repels acceptor holes ions (majority and some carriers) minority from electrons. the p-type substrate near the Si–oxide interface, creating a
● As VGS increases above 0V, more positive charge forms on the gate, repelling more holes; depletion width W_dep increases with VGS.

Capacitor Analogy and Charge Balance
● Theacceptor MOS ions structure + minority behaves electrons) like a appears capacitor in thewhere semiconductor positive charge (SC) is plate. stored on the gate plate and corresponding negative charge (fixed
● At electrostatic equilibrium: Q+(gate) = |Q−|(semiconductor).
● Voltagethe note’s across context). the MOS capacitor equals the applied VGS in quasi-static consideration (ignoring flat-band/work-function differences as per


Capacitance in Depletion
● TheCMOS effective = (Cox MOS · Cdep) capacitance / (Cox + inCdep) depletion is the series combination of oxide and depletion capacitances:
CoxCdep = = ε ox·Aεsc·A / /tox, W_dep with A = W·L
● Observations with increasing VGS (below Vth):
o W_dep ↑ ⇒ Cdep ↓ ⇒ CMOS ↓
o CMOS in depletion is less than CMOS in accumulation
o MOS capacitance behaves as a voltage-variable capacitor (VVC)

Conduction with Applied VDS in Depletion

● Ifpath; a potential current betweendifference drain is applied and source between is negligible: drain and IDS source ≈ 0 for (VDS any (^) applied> 0) while VDS in indepletion, depletion the mode. depletion region presents a high resistance
Transition Toward Inversion and Threshold
Minority Electron Attraction
● As VGS increases further above 0V, in addition to hole repulsion, minority electrons are increasingly attracted toward the Si–oxide
interface.[2][1]
● Thesignificant. continued[1][2] electron attraction accompanies depletion-region growth until a point where electron concentration at the surface becomes
Threshold Voltage and Inversion Onset
● Atthat VGS electron = Vth, concentration depletion width at the reaches surface approximatelyequals the hole its concentration maximum, and in the a very p-type thin bulk inversion (strong layer inversion of electrons condition). forms at the interface such
● At VGS = Vth, the inversion layer thickness is extremely small, so its conductive cross-sectional area A → 0; channel resistance R ∝ 1/A
→ ∞; hence IDS tends to zero for any applied VDS at the exact threshold point.
● AroundCMOS(min) this point, = Cox the · Cdep(min) minimum MOS/ (Cox capacitance + Cdep(min)). can[ be described by the series combination with the minimum depletion capacitance:


### 3. Inversion Mode (VGS > Vth):

Channel Formation and Capacitance
● For VGS > Vth, repelling additional holes becomes progressively harder, while attracting more electrons becomes easier; thus, the
inversion-layer (n-type channel) thickness increases with VGS.
● DepletionMOS capacitance width ceases in inversion to increase becomes appreciably dominated with by furtherthe oxide: VGS CMOS in strong ≈ Cox inversion (independent (approximately of VGS). at its maximum), so the small-signal
Cox = εox·A / tox

Finite Channel Resistance and Current Flow

● Withresistance VGS and > Vthnonzero and drainVDS current> 0 applied, flow from the draininversion to source layer through has finite the (^) n-typethickness inversion and finite channel. cross-sectional area; hence, finite channel
Channel Potential, Reverse-Biased Junctions, and Tapering
Body Diodes and Reverse Bias
● Then-regions), p–n junctions causing (body-to-source depletion penetration and body-to-drain) into both p and are n sides.reverse-biased in normal operation (with body at 0V and positive potentials near


```
● Thedrain local than potentialnear the source.along the channel decreases from the drain toward the source (VD > VB > VC > VS), so reverse bias is greater near the
```
Depletion Penetration and Channel Shape
● Due to stronger reverse bias near the drain, depletion extends more into the n-type inversion layer near the drain than near the source,
making the channel cross-section taper: thicker near source, thinner near drain.
● Asincreasing VDS increases channel resistance;from 0V, currentcurrent stillincreases rises with while VDS the but channel’s with decreasing tapering incrementalintensifies, rate.reducing the effective cross-sectional area and

Pinch-Off and Saturation Condition

Pinch-Off Criterion
● Withthickness increasing at the drainVDS approaches at fixed VGS zero >(pinch-off Vth, the at channel the drain thickness end). at the drain end keeps reducing; at VDS = VGS − Vth, the channel
● At pinch-off, the incremental resistance at the drain end tends to infinity (local area → 0), and the incremental current gain with further
increases in VDS tends to zero.

Beyond Pinch-Off
● Forcurrent VDS remains > VGS approximately − Vth, the pinch-offunchanged, point leading shifts to slightly a near-constant toward theIDS source; (current the saturation). effective channel length shortens, but the incremental


#### Conclusion from all Modes

```
● VGS<0 → Accumulation mode → IDS=0 for any applied VDS
● VGS<Vth → Depletion mode → IDS=0 for any applied VDS
● VGS>Vthdrain to source, → Inversion increasing mode; with for VDS 0<VDS<(VGS−Vth), (triode region) a conductive channel (inversion layer) forms between D and S and IDS flows from
```
**Triode Region (Linear Region) Behavior:**
● Condition: VGS>Vth and 0<VDS<(VGS−Vth)

● DrainIDS = current Kn [2(VGS−Vth)·VDS equation in triode − region: VDS²], (^) where Kn = μn·Cox·W/L
● Alternativeμn: electron form mobility; (emphasizing Cox: oxide aspect capacitance ratio and per parameters): unit area (= (^) εox/tox); W/L: aspect ratio; Vov=(VGS−Vth): overdrive voltage
● IDS increases with VDS with diminishing incremental gain as VDS grows (due to the −VDS² term
**Saturation Region and Pinch-Off:**
● Pinch-off condition: VDS = VGS − Vth
● At VDS ≥ (VGS−Vth), incremental current with further VDS is approximately zero; current becomes nearly constant → saturation region
● Saturation boundary is the common point between triode and saturation regions: VDS = VGS − Vth[3]
● Drain current at the boundary (from triode equation) gives the saturation current expression:
IDS(sat) = Kn (VGS − Vth)²
● Formodel, any ignoring VDS greater channel-length than (VGS−Vth), modulation) current remains at approximately IDS(sat) and is largely independent of VDS (ideal long-channel
Practical Notes on Entering Saturation
● For smaller VGS values just above Vth, only a small VDS is required to reach saturation; thus, probability of operating in saturation is high
● For higher VGS values, a larger VDS is required to reach saturation; probability of being in saturation is lower at the same VDS

### Characteristics of N channel MOSFET and GRAPHS:

```
Drain Characteristics (IDS vs VDS at constant VGS):
● Example threshold noted: Vth=0.75V
● Regions:
o VGS<0.75V → IDS=0 (cutoff)
o For VGS>Vth:
▪ 0<VDS<(VGS−Vth) → triode (linear) region
▪ VDS≥(VGS−Vth) → saturation region
● Qualitativepinch-off plots show increasing IDS curves for higher VGS, with linear-like behavior at very small VDS and saturation plateaus beyond
● Inconstant), triode regionbut the and slope for depends very small on VGS; VDS, hence IDS–VDS the device is approximatelybehaves as a VVR linear (voltage-variable with nearly constant resistor) conductance (i.e., resistance roughly
Formulas emphasized in this context:
```

```
● IDS ≈ Kn·2(VGS−Vth)·VDS for very small VDS (linear approximation)
● VVR interpretation: VDS = R(VGS)·IDS, where R varies with VGS
```
```
Drain Characteristics of MOSFET
```
**Transfer Characteristics (IDS vs VGS at constant VDS, with device in saturation)**
● Consider VDS sufficiently large so MOSFET remains in saturation across the sweep
● IDS–VGS curve is non-linear and parabolic in saturation according to IDS(sat) = Kn (VGS−Vth)²
● Indicates how effectively input voltage VGS controls output current IDS


```
● AtIDS smaller changes VGS (just above Vth), changes in VGS produce relatively small IDS changes; at higher VGS, small VGS changes produce large
```
```
Transconductance:
● gm = ∂IDS/∂VGS in saturation = 2·Kn·(VGS−Vth)
● This gm expression is valid in saturation region
```
**Key Parameters and Notation**
● μn: mobility of electrons
● Cox: oxide capacitance per unit area (= εox/tox)
● W/L: aspect ratio
● Kn = μn·Cox·W/L: conduction parameter
● Vov = (VGS−Vth): overdrive voltage

Recap: Saturation Region (n-MOS)
● IDS(sat) = Kn [VGS − Vth]²
● Transconductancegm = ∂IDS/∂VGS in= 2Knsaturation: [VGS − Vth]
⇒ gm ∝ √IDS since IDS = Kn(VGS − Vth)² ⇒ gm = 2√(Kn·IDS)
● As VGS ↑ ⇒ IDS ↑ and gm ↑; and vice versa.
Where Kn = μn·Cox·W/L, and Cox = εox/tox.


**Transfer Characteristics in Triode Region (n-MOS):**
● Condition: VGS > Vth and 0 < VDS < (VGS − Vth)

● DrainIDS = current: Kn [2(VGS (^) − Vth)·VDS − VDS²]
● Forgm =small-signal ∂IDS/∂VGS slope = 2Kn·VDS with respect to VGS at constant VDS:
o Note: In triode, gm depends on VDS (not on VGS directly), so at fixed VDS, gm is constant versus VGS.
● Linearized form (y = m x + c) at constant VDS treating IDS vs VGS:
ym ≡ = IDS, 2Kn·VDS x ≡ VGS
c = −2Kn·Vth·VDS − Kn·VDS²
o Slope increases with VDS; intercept set by Vth and VDS² term.
Graphical notes:
● For VGS > Vth, IDS–VGS in triode is an affine line at fixed VDS with slope 2Kn·VDS.
● IDS–VDS in triode is approximately linear at very small VDS, then curves downward due to −VDS² term.
Comparing gm in Regions (n-MOS)
● Triodegm = 2Kn·VDS (0 < VDS ⇒ < VGSindependent − Vth): of VGS at fixed VDS
● Saturationgm = 2Kn(VGS (VDS − ≥ Vth)VGS ⇒ − Vth):increases (^) linearly with VGS and equals 2√(Kn·IDS)


Key takeaways:
● In saturation, both IDS and gm depend on VGS.
● In triode, IDS depends on VGS, but gm at constant VDS does not depend on VGS; it depends on VDS.
Region conditions (n-MOS):
● Triode: VDS < VGS − Vth
● Saturation: VDS ≥ VGS − Vth

### p-Type Enhancement MOSFET (pMOS, enhancement type):

Convention used: body at reference; source at higher potential than drain; for pMOS, VSD > 0, VDS < 0; use VSG = −VGS ≥ 0.
Modes:
● Accumulation (pMOS): VGS > 0 (i.e., VSG < 0)
o GatenMOS positive text but w.r.t. keep source sign conventions de-accumulates consistent holes; in with equations the provided below. note convention, the accumulation/depletion labeling mirrors
● Depletion: Vth < VGS < 0 (i.e., 0 < VSG < |VTP|)
o EffectiveCMOS = depletion,(Cdep·Cox)/(Cdep no conduction + Cox) channel; CMOS in depletion is series:
o AtCMOS(min) VGS = Vth = (VSG(Cdep(min)·Cox)/(Cdep(min) = |VTP|), CMOS reaches + minimum: Cox)
● Inversion (ON): VGS < Vth ⇔ VSG > |VTP|
o Channel forms; current flows for applied source–drain bias.
o For pMOS in normal operation: source at higher potential, drain at lower ⇒ VSD > 0 and VSG > 0.
Capacitance references:
● CMOS(inversion) ≈ Cox = εox·A/tox (strong inversion)
● CMOS(accumulation) ≈ Cox
● Depletion uses series formula above.
pMOS conduction (using pMOS-friendly variables):


```
● ON condition: VSG > |VTP|
● TriodeISD = Kp(linear) [2(VSG region: + VTP)·VSD 0 < VSD < − (VSG VSD²] + VTP)
● Saturation:ISD(sat) = KpVSD [VSG ≥ (VSG + VTP]² + VTP)
● Parameter: Kp = μp·Cox·W/(2L)
Notes:
● DrainVDS ↔characteristics VSD, (VGS ISD–VSD− Vth) ↔ (VSGmirror +nMOS VTP) with variable substitutions:
● Transfer characteristic in saturation (ISD vs VSG at sufficiently large VSD):
```
ISDThis =is Kp a mirror [VSG image+ VTP]² of nMOS= Kp [−VGS transfer + characteristics.VTP]² (^)
pMOS region conditions summary:
● OFF: VSG < |VTP| ⇒ ISD = 0 (no inversion)
● Triode: VSG > |VTP| and VSD < (VSG + VTP)
● Saturation: VSG > |VTP| and VSD ≥ (VSG + VTP)
Transconductance for pMOS:
● Triode (constant VSD): gm = ∂ISD/∂VSG = 2Kp·VSD
● Saturation: gm = ∂ISD/∂VSG = 2Kp (VSG + VTP) = 2√(Kp·ISD)
Sign conventions reminder:
● For pMOS, typical signs: VSG ≥ 0, VSD ≥ 0, VTP < 0 (magnitude |VTP|).
● Mapping to nMOS forms: replace (VGS − Vth) with (VSG + VTP).

### Quick Equation Box:

```
● nMOS triode: IDS = Kn [2(VGS − Vth)·VDS − VDS²]
● nMOS saturation: IDS = Kn (VGS − Vth)²
● nMOS gm:
o Triode: gm = 2Kn·VDS
o Saturation: gm = 2Kn(VGS − Vth) = 2√(Kn·IDS)
● pMOS triode: ISD = Kp [2(VSG + VTP)·VSD − VSD²]
● pMOS saturation: ISD = Kp (VSG + VTP)²
● pMOS gm:
o Triode: gm = 2Kp·VSD
o Saturation: gm = 2Kp(VSG + VTP) = 2√(Kp·ISD)
```

### 2. Depletion MOSFET Basics

n‑Type Depletion MOSFET
● n‑type channel exists even at VGS = 0 → current flows for VDS > 0.
● Applying −ve VGS repels electrons → channel width reduces (depletion).
● At VGS = Vth (negative) → channel fully depleted → IDS = 0 for any VDS.
● Vth is negative for n‑type depletion MOSFET.
● Modes:
o VGS < Vth → OFF (no channel)
o VGS > Vth, VDS < (VGS − Vth) → Triode
o VGS > Vth, VDS ≥ (VGS − Vth) → Saturation
Equations:
● Triode:
𝐼𝐷𝑆=𝐾𝑛[ 2 (𝑉𝐺𝑆−𝑉𝑡ℎ)𝑉𝐷𝑆−𝑉𝐷^2 𝑆]
● Saturation:
𝐼𝐷𝑆=𝐾𝑛(𝑉𝐺𝑆−𝑉𝑡ℎ)^2
● With positive VGS, electron density in the channel increases → enhancement mode.
● Drain characteristics:
o VGS < 0 → depletion mode curves

o VGS(similar > (^0) to → enhancement enhancement MOSFET mode curves but Vth is negative)


p‑Type Depletion MOSFET
● Vth positive.
● Modes:
o VGS > 0 → Depletion mode
o VGS < 0 → Enhancement mode
● Transfer characteristic = mirror image (about y‑axis) of n‑type.

### Enhancement vs Depletion MOSFET:

```
● Enhancement type: Normally OFF at VGS = 0 (needs inversion to conduct).
● Depletion type: Normally ON at VGS = 0 (already has channel).
● n‑type enhancement: Vth > 0
● n‑type depletion: Vth < 0
● p‑type enhancement: Vth < 0
● p‑type depletion: Vth > 0
```
2. MOSFET Symbol Representation
    ● Arrow shows p–n junction direction between body and inversion layer.
    ● Symbol variations for:
       o n‑type enhancement
       o n‑type depletion
       o p‑type enhancement
       o p‑type depletion


### 3. Non ‑ Ideal Effects

**3.1 Channel Length Modulation (λ)**
● In saturation (VDS ≥ VGS − Vth):
o Increasing VDS moves pinch‑off point toward source, reducing effective channel length.
o Leads to slight increase in IDS with VDS instead of constant (ideal).
● Ideal: λ = 0 → IDS flat in saturation.
● Practical: small positive λ → IDS slope in saturation region.
Modified Saturation Current Equation:
𝐼𝐷𝑆=𝐼𝐷𝑆𝑜 [ 1 +λ𝑉𝐷𝑆]
where
𝐼𝐷𝑆𝑜=𝐾𝑛(𝑉𝐺𝑆−𝑉𝑡ℎ)^2
● λ: channel‑length modulation parameter (V⁻¹), very small in long‑channel devices.

Key Summary Table
Type Vth Sign At VGS=0 Modes Possible
n‑Enhancement +ve OFF Enhancement only
n‑Depletion −ve ON Depletion & Enhancement
p‑Enhancement −ve OFF Enhancement only
p‑Depletion +ve ON Depletion & Enhancement

1. Channel Length Modulation
    ● InIf weSaturation increase Region:

```
𝑉𝐷𝑆>(𝑉𝐺𝑆−𝑉𝑡ℎ)
the zero‑point (where channel thickness → 0) shifts toward the Source terminal, thus the effective channel length decreases.
● This decrease in effective channel length with increase in VDS (above 𝑉𝐺𝑆−𝑉𝑡ℎ) is called Channel Length Modulation.
```
Ideal vs Practical
● Ideal assumption: In saturation, for 𝑉𝐷𝑆>(𝑉𝐺𝑆−𝑉𝑡ℎ), 𝐼𝐷𝑆 stays constant.
● Practical: With increase in VDS above (𝑉𝐺𝑆−𝑉𝑡ℎ), 𝐼𝐷𝑆 increases slightly → drain characteristics have slope in saturation instead of flat.

```
Equations:
● Ideal saturation current:
```

###### 𝐼𝐷𝑆𝑜=𝐾𝑛 [𝑉𝐺𝑆−𝑉𝑡ℎ]^2

```
● With channel length modulation:
𝐼𝐷𝑆=𝐼𝐷𝑆𝑜 [ 1 +λ ∆𝑉𝐷𝑆]
where:
```
λ∆ (^) 𝑉= channel length modulation parameter (V⁻¹, very small in long-channel MOSFETs)
𝐷𝑆=𝑉𝐷𝑆−(𝑉𝐺𝑆−𝑉𝑡ℎ)
Output Resistance
● Ideal: λ= 0 ⇒𝑟𝑜→∞
● Practical: λ> 0 ⇒ finite but high 𝑟𝑜
𝑟𝑜=λ 𝐼^1 𝐷𝑆𝑜
Modified Current Expression (including λ):
𝐼𝐷𝑆=𝐾𝑛[𝑉𝐺𝑆−𝑉𝑡ℎ]^2 ·[ 1 +λ(𝑉𝐷𝑆−(𝑉𝐺𝑆−𝑉𝑡ℎ))]
Effect on gm:
● Ideal: 𝑔𝑚= 2 𝐾𝑛(𝑉𝐺𝑆−𝑉𝑡ℎ), independent of VDS in saturation.
● Practical: In saturation, as VDS ↑ ⇒ ∆𝑉𝐷𝑆 ↑ ⇒ IDS ↑ ⇒ gm ↑.
Also: Due to channel length modulation, effective Vth decreases slightly with VDS.

**2. Body Effect:**
    ● Normally Body (B) and Source (S) are connected ⇒ 𝑉𝑆𝐵= 0.
    ● When they are not connected ⇒ 𝑉𝑆𝐵≠ 0 ⇒ threshold voltage changes ⇒ Body Effect.
Equation:
𝑉𝑇𝑁=𝑉𝑇𝑁 0 +γ⎡⎢⎣ 𝑉𝑆𝐵+ 2 φ𝑓− 2 φ𝑓⎤⎥⎦
Where:
● 𝑉𝑇𝑁 = threshold voltage with body effect
● 𝑉𝑇𝑁 0 = threshold voltage when 𝑉𝑆𝐵= 0
● γ = body effect parameter
● φ𝑓 = Fermi potential
● Due to body effect, magnitude of Vth increases.


**3. Threshold Voltage Dependence:**
    1. Oxide thickness (𝑡𝑜𝑥):
𝐶𝑜𝑥=ε𝑜𝑡𝑥𝑜·𝑥𝐴
𝑡𝑜𝑥↓⇒𝐶𝑜𝑥↑⇒𝑉𝑡ℎ↓
𝑡𝑜𝑥↑⇒𝐶𝑜𝑥↓⇒𝑉𝑡ℎ↑
2. Substrate doping (𝑁𝑠):
o 𝑁𝑠↑⇒ more charge needed for inversion ⇒ 𝑉𝑡ℎ↑
𝑁𝑠↓⇒𝑉𝑡ℎ↓
3. Temperature (T):
𝑇↑⇒𝑉𝑡ℎ↓
𝑇↓⇒𝑉𝑡ℎ↑

Temperature Effect on IDS
𝐼𝐷𝑆=𝐾𝑛(𝑉𝐺𝑆−𝑉𝑡ℎ)^2 with
𝐾𝑛=μ𝑛𝐶 2 𝑜𝐿𝑥𝑊
● As 𝑇↑:
o 𝑉𝑡ℎ↓ ⇒ tends to increase IDS
o μ𝑛↓ ⇒ 𝐾𝑛↓ ⇒ tends to reduce IDS
● Net effect: Reduction in IDS with temperature ⇒ thermal runaway not a problem in MOSFETs.

**4. Subthreshold Conduction:**
    ● Ideal: For 𝑉𝐺𝑆<𝑉𝑡ℎ ⇒ 𝐼𝐷𝑆= 0
    ● Practical: For 𝑉𝐺𝑆<𝑉𝑡ℎ ⇒ a small current (off‑state current) flows.
Graph: √IDS vs VGS
● Ideal: intercept at Vth, zero below
● Practical: slope continues below Vth, nonzero IDS
Equation (ideal strong inversion):
𝐼𝐷𝑆= 𝐾𝑛 (𝑉𝐺𝑆−𝑉𝑡ℎ)

```
Cause: Weak inversion region – small diffusion current between source/drain even when 𝑉𝐺𝑆<𝑉𝑡ℎ.
● Off‑state current increases slightly due to channel length modulation.
```

## Key Points Recap:

```
● Channel Length Modulation ⇒ IDS slope in saturation, finite ro, gm depends slightly on VDS.
● Body Effect ⇒ higher Vth when VSB > 0.
● Threshold Voltage Dependence ⇒ affected by 𝑡𝑜𝑥, doping 𝑁𝑠, temperature T.
● Subthreshold Conduction ⇒ small IDS for VGS < Vth (off‑state current).
```

### Introduction SPICE:

SPICEcircuits (Simulationbehave before Program building with hardware. Integrated It Circuitmodels Emphasis) components is a(resistors, general‑purpose capacitors, electronic inductors, circuit diodes, simulator BJTs, used MOSFETs, to mathematically sources, transmissionpredict how (^)
lines) and solves the circuit’s equations to perform common analyses:
**Why SPICE simulations are needed:**
SPICEprototype predicts spins andcircuit optimizing behavior component mathematically values before and tolerances. hardware SPICE is built, supports enabling DC, early AC, fault and finding,transient faster analyses—as iteration, well and aslower noise, cost distortion, by reducing and (^)
temperature sweeps—so performance and reliability can be verified across operating conditions. It is industry‑standard at both board and transistor
levels to check design integrity and account for parasitics and tolerances that are hard to validate on breadboards.
**What SPICE is used for in CMOS:**
●● VerifyValidate transistor designs‑ levelbefore operation fabrication and where operating breadboarding points in analog/mixed integrated circuits‑signal is CMOS impractical blocks and using mask DC/AC/transient costs are high. analyses.
● Model and analyze subcircuits common in CMOS (switches, current mirrors, references, amplifiers) using MOS device models and
small‑signal parameters.
**Why SPICE is used for in MOSFETs:**
●● EvaluateCapture parasiticsI–V behavior, and switchingtemperature dynamics, effects with and poweradvanced, dissipation temperature using‑ (^) dependentvendor and MOSFET PDK MOSFET models models. for accurate (^) transient and thermal
behavior.
● Acceleratehardware design by simulating MOSFET choices and gate‑drive conditions to optimize efficiency and ensure safe operating area before
(^) **CODE Diagram:**
The snap shot of SPICE netlist of the above NMOS
R1 resistance is added as it is not desired that the current from Vin would be directly fed to the gate of M1.
Definition of nodes and the method to identify them
Abetween node is these can twobe defined terminals. as aBut point most connecting of the times two a nodetermials. connects If two two terminals different of devices. a single device are short circuited then the node is said to be in
Thethem. method to identify nodes is to identify the SPICE netlist for the device and all the wires connecting different components have one node on


#### SPICE syntax:

SPICE netlist code for our NMOS

*Model Description
.param temp=27
*Including sky130 library files
.lib "sky130_fd_pr/models/sky130.lib.spice" tt

##### *Netlist Description

XM1 Vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=5 l=2
R1 n1 in 55
Vdd vdd 0 1.8V
Vin in 0 1.8V
*simulation commands

.op
.dc Vdd 0 1.8 0.1 Vin 0 1.8 0.2

.control

run
display
setplot dc1
.endc

.end

## There are five types of process corners available

## for use:

tt -> Typical corner

sf -> Slow-fast corner

ff -> Fast-fast corner

ss -> Slow-slow corner

fs -> Fast-slow corner

Inwith the any Lab valid activity, process the cornercorner is used. The corner can be changed by changing the word 'tt' in the line .lib "sky130_fd_pr/models/sky130.lib.spice" tt

Method to save SPICE model


#### Method to write code for SPICE simulation

The snap shot of the terminal window of NGSPICE Simulation:


### Velocity Saturation and basics of CMOS inverter VTC:

## ● 1.Velocity Saturation:

(^) andIn short-channel reaches a maximum MOSFETs, (saturation as the electricvelocity). field This in limitsthe channel the drain becomes current, very affects high, transconductance, carrier velocity stops and increasingis a key factor linearly in modern with field

## deep-submicron device behavior.

### ● CMOS Inverter VTC (Voltage Transfer Characteristic):

(^) switchingThe VTC showsthreshold how (Vm), the output noise voltagemargins of (NMH, a CMOS NML), inverter and changes inverter with gain its — inputall critical voltage. for ensuringFrom the robust curve, digitalyou can logic identify
operation.
SPICEand higher simulation electric for fields lower and nodes the velocity and the saturationcharacteristics drain forcurrent long modelchannel were and alsoshort observed. channel devices were observed. The velocity saturation at lower
MOSFET as a switch and the characteristics of the CMOS inverter were taught.
The snap shot of various regions of operation of NMOS on graphs plotted between Ids and Vds.
TheVgs=0V plot theoverlapping nmos is not with turned the 'x''ON' axis so, is there at Vgs=0V is no channel and that present. is because there is 0 drain current at that point of time and the reason is that when
The theory about the cut-off region of NMOS.
When Vgs<Vt the region of operation of the NMOS is said to be the cut-off region
Cut-off region is a region where the device has been cut-off or it is 'OFF'
Short channel effect


Velocity Saturation effect

Forjust thesaturates. lower Thisvalues point of the of saturationelectric field, is represented the velocity by tends εc (critical to be a electriclinear function field) of the electric field. But, after a certain point (cut-off) the velocity

Vn(m/S) = linear for ε<=εc

Vn(m/S) = constant for ε>=εc

The snap shot of the graph of velocity saturation effect

The modes of operation for long channel (>250nm) devices and short channel (<250nm) devices.

**The modes of operation for long channel devices are:**

Cut-off region

Resistive region

Saturation region

### The modes of operation for short channel devices are:

Cut-off region

Resistive region

Velocity Saturation region

Saturation region

Idsat is a technology parameter saturation voltage i.e voltage at which device velocity saturates and is independent of Vgs or Vds


**The various modes when the value of Vmin is different:**

When Vgt is the minimum of Vgt, Vds, Vdsat the device is in the saturation region.

When Vds is the minimum of Vgt, Vds, Vdsat the device is in the resistive region.

When Vdsat is the minimum of Vgt, Vds, Vdsat the device is in the velocity saturation region.

It looks like current should increase at lower nodes.

Velocity Saturation causes device to saturate early

For plotting the graph between Ids and Vds for short channel devices we need to write the following

### SPICE code To Drain Characteristics:

*Model Description

.param temp=27

*Including sky130 library files

.lib "sky130_fd_pr/models/sky130.lib.spice" tt

*Netlist Description

XM1 Vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=0.39 l=0.15

R1 n1 in 55

Vdd vdd 0 1.8V

Vin in 0 1.8V

*simulation commands

.op

.dc Vdd 0 1.8 0.1 Vin 0 1.8 0.2

.control

run

display

setplot dc1

.endc

.end


Drain Characteristics of MOSFET on NGSPICE

The snap shot of output window for plot between Ids and Vds for short channel device

To observe the value of Id at any point on the curve, then left click on the point on the curve to be observed.

Now on the terminal window, some values of x0 and y0 should appear.

The value of Id corresponds to the value of y0 in ampere.

To calculate Threshold voltage for Id versus Vgs curve, the following SPICE code is required:

### SPICE code For Trandsfer Characteristics:

*Model Description

.param temp=27

*Including sky130 library files

.lib "sky130_fd_pr/models/sky130.lib.spice" tt

*Netlist Description

XM1 Vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=0.39 l=0.15

R1 n1 in 55

Vdd vdd 0 1.8V

Vin in 0 1.8V

*simulation commands

.op


.dc Vin 0 1.8 0.1

.control

run

display

setplot dc1

.endc

.end

The snap shot of terminal window for plot between Ids and Vds for short channel device without the sweep for vdd

Transfer Characteristics of MOSFET ON NGSPICE


#### 2.CMOS voltage transfer characteristics (VTC):

What was learnt:

**CMOS WORKING:**

Transistor as a switch

With infinite 'Off' resistance when |Vgs|<|Vt|

With finite 'On' resistance when |Vgs|>|Vt|

The working of CMOS inverter

What happens when Vin is ‘high’ and equal to ‘vdd’

PMOS turns 'OFF'

NMOS turns 'ON'

What happens when Vin is ‘low’ and equal to ‘0V’

PMOS turns 'ON'

NMOS turns 'OFF'

The flow of current when Vin is ‘high’ and when Vin is ‘low’

When Vin=Vdd

Direct path exists between Vout and Vss resulting in Vout=0V

When Vin=0V

Direct path exists between Vdd and Vout, resulting in Vout=Vdd

Defined terminologies in CMOS inverter

Circuit Diagram of CMOS Inverter


**Derivation CMOS voltage transfer characteristics (VTC):**

For the NMOS voltage equations

For the PMOS voltage equations

For the relationship between the currents

Load curve for PMOS transistor in CMOS inverter

The snap shot of load curve for PMOS transistor in CMOS inverter


Load curve for NMOS transistor in CMOS inverter

The snap shot of load curve for NMOS transistor in CMOS inverter

Superimposing the load curve of NMOS on the load curve of PMOS and plotting Vin vs Vout from the graph obtained

The snap shot of superimposed load curve of NMOS and load curve of PMOS


**Voltage transfer characteristics and SPICE simulations:**

The various components of a SPICE deck:

Component connectivity

Component values

Identification of 'nodes'

Naming 'nodes'

The snap shot of the SPICE netlist considered

**The SPICE code for the above netlist looks something like following:**

***MODEL Description***

***NETLIST Description***

M1 out in vdd vdd pmos W=0.375u L=0.25u

M2 out in 0 0 nmos W=0.375u L=0.25u

cload out 0 10f

Vdd vdd 0 2.5

Vin in 0 2.5

***SIMULATION Commands***

.op


.dc Vin 0 2.5 0.05

***.include tsmc_025um_model.mod***

.LIB "tsmc_025um_model.mod" CMOS_MODELS

.end

Lab Activity:

For plotting the Vtc characteristics of CMOS inverter, the following code is needed:

*Model Description

.param temp=27

*Including sky130 library files

.lib "sky130_fd_pr/models/sky130.lib.spice" tt

*Netlist Description

XM1 out in vdd vdd sky130_fd_pr__pfet_01v8 w=0.84 l=0.15

XM2 out in 0 0 sky130_fd_pr__nfet_01v8 w=0.36 l=0.15

Cload out 0 50fF

Vdd vdd 0 1.8V

Vin in 0 1.8V

*simulation commands

.op

.dc Vin 0 1.8 0.01

.control

run

setplot dc1

display

.endc

.end


The snap shot of the terminal window for plotting the Vtc characteristics of CMOS inverter

### output window for plotting the Vtc characteristics of CMOS inverter on NGSPICE

To find the switching threshold voltage (Vm), it is known that Vout = Vin so zoom in on the plot where roughly Vout = Vin by selecting the area of
the plot by right clicking on the screen and dragging it to select the area.

Zoom twice or thrice until the point where Vm lies becomes almost certain.

Left click roughly on the point on the curve where Vm should approximately lie.

Values of x0 and y0 will now appear on the terminal window.

Since we are finding Vm, therefore x0 ~ y0 and hence x0=y0=Vm.

### For performing the transient analysis, the following code is required:

*Model Description

.param temp=27

*Including sky130 library files

.lib "sky130_fd_pr/models/sky130.lib.spice" tt

*Netlist Description

XM1 out in vdd vdd sky130_fd_pr__pfet_01v8 w=0.84 l=0.15

XM2 out in 0 0 sky130_fd_pr__nfet_01v8 w=0.36 l=0.15

Cload out 0 50fF

Vdd vdd 0 1.8V

Vin in 0 PULSE(0V 1.8V 0 0.1ns 0.1ns 2ns 4ns)

*simulation commands


.tran 1n 10n

.control

run

.endc

.end

The snap shot of the terminal window for performing the transient analysis

**The snap shot of the output window for performing the transient analysis on NGSPICE**

To calculate the rise delay:

Zoomand dragging on the itpart to selectof the the curve area. having fall of the input pulse and rise of the output pulse around voltage of (Vdd/2) by right clicking on the screen

Now, left click on the rising edge of the output curve at (Vdd/2) to get a point x0,y0 on the terminal.

Similarly, get the point at (Vdd/2) for falling edge of the input curve.

The difference between the x-coordinate of the rising edge of the output curve and the falling edge of the input curve is the rise delay.

To calculate the falling delay:

Zoomand dragging on the itpart to selectof the the curve area. having rise of the input pulse and fall of the output pulse around voltage of (Vdd/2) by right clicking on the screen

Now, left click on the falling edge of the output curve at (Vdd/2) to get a point x0,y0 on the terminal.

Similarly, get the point at (Vdd/2) for rising edge of the input curve.

The difference between the x-coordinate of the falling edge of the output curve and the rising edge of the input curve is the fall delay.


### Static Behavior Evaluation - CMOS Inverter Robustness:

### Switching threshold

A CMOS inverter is a robust device because the shape of its input versus output curve remains the same for all different values of (W/L) ratios.

```
1.2. StaticSwitching Behavior Threshold Evaluation: CMOS Inverter Robustness
```
3.4. NoisePower Margin Supply (^) Variation

5. Device Variation

#### 1.CMOS Inverter Robustness:

CMOSKey factors inverter include: robustness refers to its ability to operate correctly under **real-world variations and disturbances** without producing logic errors.

```
● Noise Margins (NMH/NML) – Measure tolerance to unwanted voltage noise at logic levels.
● PVT Variations – Process, Voltage, and Temperature changes can shift switching thresholds and delay.
● Glitch Immunity – Ability to reject short transient pulses on the input.
● Load Variations – Stable operation despite changes in capacitive or resistive loading.
● Supply Scaling – Maintaining functionality when VDD changes, especially for low-power design.
```
Ain robustlarge digital inverter systems. maintains correct logic levels, adequate noise margins, and predictable timing **across all operating conditions** , ensuring reliability

## 2.Switching Threshold (Vm)

The **switching threshold** of a CMOS inverter is the **input voltage** at which the inverter’s **output voltage equals its input voltage**.

```
● At Vm , both the PMOS and NMOS transistors conduct significant current.
● It’s the point where the inverter transitions from output HIGH to output LOW.
● Ideally, Vm is set near VDD/2 for balanced noise margins and symmetrical switching speed.
● In the VTC (Voltage Transfer Characteristic) curve, it’s the midpoint of the steep transition region.
```
**Formula** For matched **:** (^) NMOS/PMOS parameters:
Vm≈VDD2V_m \approx \frac{V_{DD}}{2}Vm ≈2VDD
but in real designs, Vm is influenced by **W/L ratios** , threshold voltages (Vt), and mobility differences between electrons and holes.
**Derivation FOR CMOS SWITCHING THRESHOLD(VM):**
Vm when (Wp/Lp) is 1.5 is approximately equal to 0.98V and when (Wp/Lp) is 3.75 it is approximately equal to 1.2V
Wp and Lp in the above section are Width of PMOS channel and Length of PMOS channel
At Vm, both PMOS and NMOS are turned 'ON' because Vgs almost crossed the threshold region for both of them.
A few observations can be made from the information stated above,


Therefore, Vgs = Vds

IdsP = - IdsN which means that IdsP + IdsN = 0

We know the equations for IdsN and IdsP which are as stated below:

We ignore the 1+λVds because the term is very small and it makes the equations very difficult for hand calculations.

Since, IdsP + IdsN = 0

Therefore, the equations can be re-written as:

Here,

Wp is the width of the channel in PMOS

Lp is the length of the channel in PMOS

Wn is the width of the channel in NMOS

Ln is the length of the channel in NMOS


kn' is the process transconductance of the NMOS

kp' is the process transconductance of the PMOS

Vdsatn is the Vdsat of the NMOS

Vdsatp is the Vdsat of the PMOS

Vm is the switching threshold voltage

Vt is the threshold voltage

Vdd is the supply voltage

**Weconclusions experimented with the sizes of the PMOS with respect to the sizes of NMOS and came up with the following**

(Wp/Lp) x.(Wn/Ln) Rise Delay Fall Delay

(Wp/Lp) 1.(Wn/Ln) 148pS 71pS 0.99V

(Wp/Lp) 2.(Wn/Ln) 80pS 76pS 1.2V

(Wp/Lp) 3.(Wn/Ln) 57pS 80pS 1.25V

(Wp/Lp) 4.(Wn/Ln) 45pS 84pS 1.35V

(Wp/Lp) 5.(Wn/Ln) 37pS 88pS 1.4V

We can make some conclusions from the above table:

When (Wp/Lp) = 2.(Wn/Ln), there is an approximately equal rise-fall delay

Due to the equal rise-fall delay, (Wp/Lp) = 2.(Wn/Ln) create typical characteristics for a clock inverter/buffer

The conditions other than (Wp/Lp) = 2.(Wn/Ln) can still be used as regular inverters/buffers and these can be preferred for data path

Switching(Wp/Lp) = threshold 5.(Wn/Ln) for is (Wp/Lp) also very = small 2.(Wn/Ln) and (Wp/Lp) = 3.(Wn/Ln) is very small. Similarly, switching threshold for (Wp/Lp) = 4.(Wn/Ln) and

Whenthe reason Wp/Lp is the is increased,availability the of rise a bigger delay area is significantly to charge the reduced capacitor. because time required for the output capacitor to charge decreases significantly and

Ron(PMOS) ~ 2.5*Ron(NMOS)


## 3.CMOS Noise Margin Robustness:

**CMOS Noise Margin Robustness :**

Noiselogic levels. margin robustness is the CMOS inverter’s **ability to tolerate unwanted voltage noise** on its input without misinterpreting

```
● NMH (Noise Margin High) → Max noise voltage a HIGH input can withstand before being seen as LOW.
● NML (Noise Margin Low) → Max noise voltage a LOW input can withstand before being seen as HIGH.
● Larger NMH/NML = more robust against interference, supply ripple, and crosstalk.
● Achieved by balancing switching threshold and designing for steep VTC slope.
```
Static Behavior Evaluation - CMOS Inverter Robustness: Noise Margin

The ideal and actual Input-Output characteristics of an inverter were observed

### ideal Input-Output characteristics of an Inverter

### actual Input-Output characteristics of an Inverter with finite slope


In the above diagram, the terms stated are explained as follows:

Vil is Input Low Voltage (Vil could be Vdd/4)

Any input voltage level between 0 and Vil will be treated as logic '0'

Voh is Output High Voltage (Vih < Voh <= Vdd)

Any output voltage level between Voh and Vdd will be treated as logic '1'

Vih is Input High Voltage (Vih could be 3.Vdd/4)

Any input voltage level between Vih and Vdd will be treated as logic '1'

Vol is Output Low Voltage (0 <= Vol < Vil)

Any output voltage level between 0 and Vol will be treated as logic '0'

Actual Input-Output characteristics on an inverter were observed and they were plotted on a scale

### Actual Input-Output characteristics of an Inverter

### Noise induced bump characteristics at different noise margin levels

Forbetween any signalVol and to Vil be thenconsidered it's not (^) hazardousas logic '0' because and logic it still '1', (^) liesit should in the berange in theof logicNMl '0'.and Any NMh glitch ranges, that respectively.occurs in this - regionIf the height is a safe of glitchthe bump because lies in it (^)
will still be considered as logic '0'. - If the height of the bump lies in the "undefined region" then it is potentially hazardous because it can acquire


logicbump '1'lies which in between can be Vih fatal. and Any Voh glitch then it in will this definitely region is be unsafe considered because as logicit is unclear'1'. These if (^) kindsit will of go glitches to logic are '1' orthe fall glitches to logic that '0'. need - If tothe be height fixed. of the
**Conclusions of noise margins of the inverter at different values of Wp/Lp were observed and they were as follows:**
(Wp/Lp) x.(Wn/Ln) NMh NMl Vm
(Wp/Lp) 1.(Wn/Ln) 0.3 0.3 0.99V
(Wp/Lp) 2.(Wn/Ln) 0.35 0.3 1.2V
(Wp/Lp) 3.(Wn/Ln) 0.4 0.3 1.25V
(Wp/Lp) 4.(Wn/Ln) 0.42 0.27 1.35V
(Wp/Lp) 5.(Wn/Ln) 0.42 0.27 1.4V
A few conclusions can be inferred from the above table: - When (Wp/Lp) = 2.(Wn/Ln) there is a rise at the NMh because PMOS is responsible for
holdinga result theof that, charges the capacitance on the capacitance. is able to When retain thethe sizecharge of PMOSfor a longer is increased, amount aof low-resistance time resulting path in an from increased supply NMh. to the - capacitanceWhen (Wp/Lp) is formed = 4.(Wn/Ln) and as (^)
therestatic ispoint. a drop - In at the the above NMl becausetable, NMl the isNMOS not affected has now much become but NMhweaker has than increased the PMOS by 120mV - When but (Wp/Lp) this range = 5.(Wn/Ln) is still acceptable the NMh and almost this comesproves tothe a (^)
CMOS inverter robustness with respect to the Noise Margin. - Finally, the areas that can be used for digital and analog applications are stated in the
figure below:
**GRAPH Areas Fitted for digital and analog Designs:**
Vout versus Vin curve showing the areas that can be used for digital and analog applications


Lab Activity:

For performing the Day 4 Lab Activity we need the following code

*Model Description

.param temp=27

*Including sky130 library files

.lib "sky130_fd_pr/models/sky130.lib.spice" tt

*Netlist Description

XM1 out in vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.15

XM2 out in 0 0 sky130_fd_pr__nfet_01v8 w=0.36 l=0.15

Cload out 0 50fF

Vdd vdd 0 1.8V

Vin in 0 1.8V

*simulation commands

.op

.dc Vin 0 1.8 0.01

.control

run

setplot dc1

display

.endc

.end

The snap shot of the output window for calculating the Noise Margins


Method to calculate the Noise Margins from the plot:

Run the ngspice command and open the plot

left click on the point towards the top of the graph where the curvature seems to be '-1'

In this case it was x0 = 0.766667, y0 = 1.71351

Now, left click on the point towards the bottom of the graph where the curvature seems to be '-1'

In0.110811 this case it was x0 = 0.977333, y0 = 0.110811. Let's consider these points as x1 and y1 thus making the coordinates x1 = 0.977333, y1 =

For noise margin high we need Voh-Vih and in this case Voh=y0 and Vih=x1

For noise margin low we need Vil-Vol and in this case Vil=x0 and Vol=y1

Therefore, we get NMh = 0.736177 and NMl = 0.655856


## 4.CMOS Power supply:

```
● Power-Supply Variations (VDD changes)
○ Fluctuations in supply voltage (e.g., from 1.8 V down to 0.6 V in low-power designs).
○ Can affect switching threshold, noise margins, delay, and power consumption.
○ A robust design ensures functionality across the expected VDD range.
```
Wheneverat 1V sometime we move back, from now 250nm they will nodes be operatingto lower nodes at 0.7V like 20nm or so on, we scale our supply voltage as well. For example, if things were working

A CMOS inverter can be operated at 0.5V as well and it has it's own advantages and disadvantages:

**Advantages of using 0.5V supply:**

There is a significant increase in gain (close to 50% improvement)

There is a significant reduction in energy consumption (close to 90% improvement)

**Disadvantages of using 0.5V supply:**

Performance impact (0.5V supply rising and falling edge is insufficient to completely charge or discharge the load capacitance)

Lab Activity:

To perform the lab activity for power supply scaling, we need the following code:

*Model Description

.param temp=27

*Including sky130 library files

.lib "sky130_fd_pr/models/sky130.lib.spice" tt

*Netlist Description

XM1 out in vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.15

XM2 out in 0 0 sky130_fd_pr__nfet_01v8 w=0.36 l=0.15

Cload out 0 50fF

Vdd vdd 0 1.8V

Vin in 0 1.8V

.control

let powersupply = 1.8

alter Vdd = powersupply

let voltagesupplyvariation = 0

dowhile voltagesupplyvariation < 6

dc Vin 0 1.8 0.01

let powersupply = powersupply - 0.2


alter Vdd = powersupply

let voltagesupplyvariation = voltagesupplyvariation + 1

end

plot dc1.out vs in dc2.out vs in dc3.out vs in dc4.out vs in dc5.out vs in dc6.out vs in xlabel "input voltage(V)" ylabel "output voltage(V)" title
"Inveter dc characteristics as a function of supply voltage"

.endc

.end

### The snap shot of the output window to observe the power supply variation

To calculate the gain for the given plot:

Select the curve for which the gain is to be calculated (In this case, we chose the plot for 1.8V Vdd)

Left click on the point where the slope of the curve is almost changing toward the top of the plot

The point obtained was x0 = 0.766667, y0 = 1.71351

Now, left click on the point where the slope of the curve is almost changing toward the bottom of the plot

The point obtained was x0 = 0.982667, y0 = 0.1 but for our convenience let us consider the coordinates of the point to be x1, y1

Therefore, the point becomes x1 = 0.982667, y1 = 0.1

Subtract y1 from y0. So, y0 - y1 = 1.61351

Subtract x1 from x0. So, x0 - x1 = -0.216

Now, gain = (y0-y1)/(x0-x1)

Hence, Gain(g) = |(1.61351)/(-0.216)| = |-7.46995| = 7.46995


#### 5.Device Variation:

What was learnt:

**There are two sources for device variation:**

**1.Etching Process Variation:**

The etching process will define the structures in the layout of the CMOS inverter.

Etching is a very important fabrication step

It is the process that defines the structure (width and the height)

Based on the structures that get defined by the process, it directly impacts the delay

In layout of the CMOS inverter we have:

P-diffusion region which is indicated by green color.

Poly-silicon area which is indicated by red color.

Metal layer which is indicated by blue color.

N-diffusion region indicated by yellow color.

Contacts between two layers indicated by black crosses.

The thickness of the poly-silicon layer is the gate length and it defines at which node we are (20nm, 30nm, 45nm, etc.).

TheNMOS. thickness of the P-diffusion layer is the width of the gate of the PMOS and the thickness of the N-diffusion layer is the width of the gate of the

Width identifies the overlap area between the diffusion layer and the poly-silicon layer.

Fabrication is basically a lab where we have a lot of things like chemicals, water, gases, etc. running and due to these the ideal structure is distorted.

. The snap shot of the inverter chain


**Inverter Chain:**

When inverters are connected back-to-back they are collectively called the "Inverter Chain".

Inrepeated an inverter distortion chain, because the gates they in are the exposed middle tohave the (^) samethe same kind structures of structures. on both sides. So, it's very likely that this particular gate structure will have a
Indifferent an inverter devices chain, that willgates impact in the the middle gates will have a structure which is different from the gates at the ends because they might be connected to
**2.Oxide Thickness:**
In an ideal oxidation process, the gate oxide thickness will be constant throughout the process.
In the real oxidation process, the gate oxide thickness will not be constant along the gate length.
In an inverter chain, the gate oxide thickness can vary for each transistor.
Oxide thickness directly affects the Id equation because Cox is dependent on it.
Strong PMOS:
PMOS with less resistance (possibly least resistance if the size chosen is the greatest size possible)
PMOS is wider in size (possibly widest PMOS available)
Weak NMOS:
NMOS with high resistance (possibly highest resistance if the size chosen is the least size possible)
NMOS is small in size (possibly smallest NMOS available)
Strong NMOS:
NMOS with less resistance (possibly least resistance if the size chosen is the greatest size possible)
NMOS is wider in size (possibly widest NMOS available)
Weak PMOS:
PMOS with high resistance (possibly highest resistance if the size chosen is the least size possible)


PMOS is small in size (possibly smallest PMOS available)

Withwhich the is fairlyvariation acceptable from Weak because PMOS behavior - Strong of the NMOS inverter to (^) isStrong intact PMOS - Weak NMOS, the switching threshold varies from roughly 0.7V to 1.4V
We can plot the variation if we move from Weak PMOS - Strong NMOS to Strong PMOS - Weak NMOS using SPICE simulation and the plot is
given below:
From the plot given above, we can make the following conclusions:
Variationvariations in Noise Margin high (NMh) is roughly from 2.5V to 2.1V which is a variation of 400mV which is good enough to filter out high voltage
Variation in Noise Margin low (NMl) is roughly from 0V to 0.3V which is a variation of 300mV which is good enough to filter out low voltage
variations
Overall, variation in the Noise margins is low and this leaves the operation of the gate intact.
Lab Activity:
To perform the lab activity for device variation, we need the following code:
*Model Description
.param temp=27
*Including sky130 library files
.lib "sky130_fd_pr/models/sky130.lib.spice" tt
*Netlist Description
XM1 out in vdd vdd sky130_fd_pr__pfet_01v8 w=7 l=0.15
XM2 out in 0 0 sky130_fd_pr__nfet_01v8 w=0.42 l=0.15
Cload out 0 50fF
Vdd vdd 0 1.8V
Vin in 0 1.8V
*simulation commands
.op
.dc Vin 0 1.8 0.01
.control
run
setplot dc1
display
.endc
.end


### The snap shot of output window to observe device variation

Since the pfet width is very huge as compared to the nfet width, the plot is shifted towards right

To find the value of the switching threshold:

Zoom in on the plot where Vin ~ Vout by right clicking and dragging the cursor to select the area

Zoom until the value of switching threshold becomes almost certain

Left click on the point where Vin is roughly equal to Vout

A point x0 = 0.988209, y0 = 0.988191 is obtained

Since x0 ~ y0. Therefore, Switching Threshold Voltage = Vm = x0 = y0 = 0.988V


### Conclusion:

Duringcharacteristics. this course, I learned I gained how toin-depth create aknowledge **SPICE deck** of (^) from **MOSFETs** a netlist, and run the simulations, **CMOS inverter** and analyze, exploring results variouseffectively. techniques Understanding to modify the inverter **CMOS
voltage** sub-categories **transfer** such **characteristics** as noise margins, and switching the factors threshold, influencing and robustness them greatly analysis. improved my grasp of static behavior evaluation, including all its
The **Lab Activities** were especially valuable, allowing me to experiment with parameter variations in SPICE and observe their direct impact on
performanceto practical circuit plots. design. This hands-on approach not only solidified my theoretical understanding but also built my confidence in applying these concepts
Overall,sparked athis deeper workshop interest significantly to further masterstrengthened device-level my fundamentals design and in analysis. MOSFET My operation, experience CMOS with design, **VLSI System** and SPICE **Design** simulation was exceptional, workflows. thanks It also to (^)
their continuous guidance, quick doubt-resolution, and practical learning approach.

### References:

https://github.com/kunalg123/sky130CircuitDesignWorkshop

https://www.vsdiat.com/

https://www.vlsisystemdesign.com/

https://en.wikipedia.org/wiki/MOSFET

https://en.wikipedia.org/wiki/Power_MOSFET

https://www.electronicsforu.com/technology-trends/learn-electronics/mosfet-basics-working-applications

https://en.wikipedia.org/wiki/Depletion_and_enhancement_modes

https://en.wikipedia.org/wiki/CMOS

https://www.allaboutcircuits.com/technical-articles/understanding-mosfet-on-state-drain-to-source-resistance/

https://physicswallah.onelink.me/ZAZB/PWAppWEb





