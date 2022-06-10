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

Using 'lambda_n.spice' and 'lambda_p.spice', we found
$$ \lambda_n = 0.038052 \ \frac{1}{V}$$
$$ \lambda_p = 0.069696 \ \frac{1}{V}$$

## Math
Now, in order to find the output resistance that meet the frequency response requirements, we can use $f_{pole} = \frac{f_u}{A_v}$, where $f_u$ is the unity gain bandwidth. So,

$$ R_o = \frac{1}{2\pi \cdot f_{pole} \cdot C_L} = 28.421 \ k\Omega$$

With this, we can find $I_{bias}$,

$$ I_{bias} = \frac{1}{(\lambda_n + \lambda_p)R_o} = 326.557 \ \mu A $$

And to satisfy the $V_{outmax}$ of the project parameters, the drain-source voltage of $M_2$ ($V_{DS2}$) must be 0.2 V ($V_{DD} - V_{outmax}$). Thus, the aspect ratio of $M_2$ ($M_3$ will have the same) is 

$$ \left(\frac{W}{L}\right)\_2 = \frac{2 \cdot I_{bias}}{\mu_{0p} \cdot C_{oxp} \cdot V_{DS2}^2} = 818.923 $$

Lastly, the aspect ratio of $M_1$ is calculated to provide the desired gain and minimum output voltage. Note that $g_m = \frac{A_v}{R_o}$.

$$\left(\frac{W}{L}\right)\_1 = \frac{gm_1}{\mu_{0n} \cdot C_{oxn} \cdot (V_{GS1} - V_{thn})} = 69.985 $$

## SPICE Simulation

The DC simulation is used to find the operation voltage of the circuit.

<p align="center">
<img src = "https://user-images.githubusercontent.com/69206952/172963391-7f1fa9d3-7cbb-4545-9130-38494fd04cde.PNG" width = "500" height = "500">
</p>

We found 0.713 V. Using that voltage in the AC simulation we obtained the following plot.

<p align="center">
<img src = "https://user-images.githubusercontent.com/69206952/172963493-7623e706-131e-4791-a472-d12a980b497f.PNG" width = "500" height = "500">
</p>

The gain observed is 36.3636 dB, close to 40dB, in frequencies lower than 129.6 kHz. The cutoff frequency is about 1MHz and $f_u$ is 67.153 MHz, far from the 80 MHz wanted. 

Finally, the transient analysis to see the behaviour of the amplifier with a small-signal input.

<p align="center">
<img src = "https://user-images.githubusercontent.com/69206952/172964310-aa62e3c3-a9b6-4b87-82ec-00117cc7332d.PNG" width = "500" height = "500">
</p>


<p align="center">
<img src = "https://user-images.githubusercontent.com/69206952/172964350-71734930-486e-40a3-b2f8-2ed5c96ea85f.PNG" width = "500" height = "500">
</p>


