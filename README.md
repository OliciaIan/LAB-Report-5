# LAB-Report-5
# Experiment 1: Full Demodulation of a QPSK Signal

## 1. Introduction
Quadrature Phase Shift Keying (QPSK) is a bandwidth-efficient modulation technique that transmits two bits per symbol by varying the phase of a carrier wave. This experiment utilizes the **Emona Telecoms-Trainer 101** to implement a complete QPSK communication link, focusing on the hardware-level complexity of signal generation, phase-coherent demodulation, and signal integrity under noisy conditions.

---

## 2. Technical Objectives
* Implement a functional QPSK modulator and demodulator using hardware modules.
* Achieve phase synchronization using the **Phase Shifter** module to ensure correct data recovery.
* Analyze the **QPSK Constellation Diagram** using XY-mode to visualize the four phase states.
* Evaluate the impact of channel noise and phase error on signal recovery.

---

## 3. System Architecture & Methodology

### 3.1 QPSK Modulator & Demodulation
The system splits a serial bitstream into two parallel streams ($I$ and $Q$). These are multiplied by orthogonal $100\text{ kHz}$ carriers (Sine and Cosine) and summed. At the receiver, product detectors and Low Pass Filters (LPF) extract the baseband components.

### 3.2 Phase Synchronization & Constellation Analysis
As shown in **Figure 31**, the final stage of the experiment involves visualizing the constellation in **XY-mode**. 
* **The XY Display:** By connecting the recovered $I$ signal to Channel 1 (X) and the recovered $Q$ signal to Channel 2 (Y), the oscilloscope displays four distinct points representing the four possible bit pairs (00, 01, 10, 11).
* **Phase Adjustment:** The **Phase Shifter** is adjusted to rotate these points into their correct quadrants. A phase error causes the constellation to rotate, which leads to bit errors as the points cross the decision boundaries.

---

## 4. Hardware Configuration
* **Master Signals:** $100\text{ kHz}$ carriers and $2\text{ kHz}$ digital clock.
* **Phase Shifter Module:** Used to compensate for phase shifts introduced by the channel and to align the constellation.
* **Tuneable LPF:** Set to remove high-frequency mixing products while preserving the $2\text{ kHz}$ baseband pulses.
* **Noise Generator:** Simulates channel interference to observe "clouding" in the constellation.

---

## 5. Analysis & Observations

### Constellation Observations (Question 12 & 13)
**Observation:** When the phase is correctly adjusted, the four points of the constellation are stable and reside in the center of each quadrant.
* **Phase Rotation:** Adjusting the Phase Shifter control rotates the constellation. If rotated by 45°, the points sit on the axes, making it impossible for the receiver to distinguish between bit states.
* **Noise Impact:** As noise increases (transitioning to -6dB), the points spread out into "clouds." When these clouds overlap the X or Y axes, bit errors occur in the recovered data stream.

### OQPSK vs. Standard QPSK
The implementation acts as **Offset QPSK (OQPSK)**. Because the $I$ and $Q$ bits are offset in time, the signal phase never shifts by 180° instantaneously. This prevents the signal envelope from dropping to zero, which is a major advantage for maintaining signal power in real-world satellite and mobile transmitters.

---

## 6. Conclusion
The experiment successfully demonstrated the end-to-end implementation and recovery of a QPSK signal. The use of the **XY-mode constellation diagram** provided a clear visual representation of how phase and amplitude determine digital data states. The project highlighted that successful communication depends not just on signal strength, but on precise **phase synchronization**. The observations made regarding phase rotation and noise-induced "clouding" effectively illustrate the real-world challenges faced by Electronics and Communications Engineers in designing robust digital links.

---
