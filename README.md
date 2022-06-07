# cs-amp-sky130

Design of a common source amplifier with active load using the skywater 130nm technology.

The following figure shows the schematic of the circuit.
![image](https://user-images.githubusercontent.com/69206952/171064487-d78850cd-36fb-489b-a805-8b6f81ff6feb.png)

The design process will be as follows:

1. List project requirements;
2. List technology parameters given on https://skywater-pdk.readthedocs.io/en/main/index.html;
3. Find necessary parameters, such as $\lambda$ for the MOSFETs through graph analysis;
4. SPICE simulation of the circuit;
5. Check if it meets specifications;
6. Layout using MAGIC VSLI;
7. SPICE simulation post layout.

## Project Requirements

| Parameter | Value |
| --- | --- |
| DC Gain | $\geq 40$ dB ($\geq 100$)|
| Output voltage swing | 0.2 to 1.6 V |
| Load capacitance | 7 pF |
| Unity gain bandwidth | 80 MHz |

## Technology parameters

| Parameter | nMOS | pMOS |
| --- | --- | --- |
| $V_{th}$ (V) | 0.49439 | -1.0652 |
| $\mu_0 (\frac{cm^2}{V\cdot s})$ | 301.97 | 24.424 |
| $t_{ox}$ (nm)| 4.148 | 4.23 |

where
$V_{th}$ is the threshold voltage, $\mu_0$ is the carrier mobility and $t_{ox}$ is the oxide thickness.

We also have $\epsilon_{rox} = 3.9$ and the vacuum electrical permitivitty is $\epsilon_0 = 8.8541 \cdot 10^{-12} \frac{F}{m}$. With that we can find $C_{ox}$,

For the pMOS:
$$C_{ox} = \epsilon_0 \cdot \frac{\epsilon_{rox}}{t_{ox}} = 8.163\cdot 10^{-3} \frac{F}{m^2}$$
For the nMOS:
$$C_{ox} = 8.325\cdot 10^{-3} \frac{F}{m^2} $$
