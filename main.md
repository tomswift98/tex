
# **ELEMENTARY ORIFICE FLOW MEASUREMENT**
  \
  a broad generalization of ISO 5167, API 2540\...\
  \...with applications to petroleum refining
\
*L. Bennett*
Winter 2023

## Forward

Generally, the subject matter of this document will flow in reverse, with practical and usable results toward the beginning, and theory, arguments and conditions toward the end.

## Table of Symbols

Note: Base conditions are standard conditions.
$q_{v, base} = q_{v, standard}$. Similarly, flowing conditions are actual conditions. $\rho_{flowing} = \rho_{actual}$

::: description
$q_m$ is mass flow across the orifice

$C_d$ is the discharge coefficient, a function of meter geometry and Reynold's number

$d$ is the internal orifice diameter under operating conditions

$\beta$ is the inner diameter ratio of the orifice to the pipe,
$\beta = \frac{d}{D_{pipe}}$

$\Delta P$ is the difference between upstream pressure $p_1$ and
downstream pressure $p_2$

$\epsilon$ is the expansibility factor

-   1 for non-compressible liquids

-   a function of $\beta$, $\Delta p$, and the isentropic exponent
    $\kappa$ for gasses

    Note:

    :   $\kappa = \frac{C_p}{C_v}$ for ideal gasses

$\rho_1$ is upstream flowing fluid density

$T_b$ is base temperature, usually 60F, or more specifically 60.0068749F
for API 2540
:::

# Correction of Orifice Flow Meters

## Generalized Equations

The orifice calculations stored on orifice datasheets are a record of
how flow through an orifice is expected to behave under design
conditions. However, accurate flow measurement is often required outside
of design conditions. A meter correction factor, $MCF$, can be used to
correct a raw (indicated) flow for operating conditions. As orifice
meters are sized at maximum flow, a working range of approximately 4:1
flow turndown from calibration conditions is generally acceptable and is
accurate with appropriate meter correction.

The Meter Correction Factor, $MCF$, is the ratio of the corrected flow
at standard conditions to the raw flow at standard conditions.

$$MCF = \frac{q_{v, corr, base}}{q_{v, base}}$$

The primary terms that change with operating conditions in the orifice
equation are flowing and base fluid density ($\rho_1$ and $\rho_{base}$)
and orifice diameter. Orifice diameter changes are due to thermal
expansion of the metal.

Generalized Equation for Orifice Meter Correction
$$q_{v, corr, std} = q_{v, base} * MCF = \frac{q_{v, base}}{F_{\rho} * F_{E} * ...}$$

where,

$F_{\rho}$ is a factor to correct for the difference in fluid density
from calibration conditions to operating conditions

$F_{E}$ is a factor to correct for the thermal expansion of the pipe and
orifice plate from calibration conditions to operating conditions

This is not an exhaustive list of correction factors applicable to
orifice flow meters.

The inverse of the product of the correction factors is equal to the
MCF.
:::

$$MCF = \frac{1}{F_{\rho} * F_{E} * ...}$$
:::

## Liquid Density Correction

The liquid density correction factor corrects the raw flow rate for two
terms, the difference in specific gravity at calibration flowing and
actual flowing conditions, and the difference in base specific gravity
at calibration and operating compositions. This factor accounts for any
changes in density due to composition, as well as differences in flowing
gravity due to thermal expansion of the liquid.

::: proposition
Liquid density correction factor

$$F_{\rho} = \sqrt{\frac{\rho_{flowing}}{\rho_{flowing, cal}}}\frac{\rho_{base, cal}}{\rho_{base}}$$
:::

Flowing gravity, $\rho_{flowing}$, is generally calculated using the
method outlined in API 2540, summarized below. Flowing gravity can also
be determined graphically, using a graph such as appears in Appendix A-8
of Technical Paper 410 (Crane Manual) \[citeme\].

### API 2540 Method for Hydrocarbon 

API 2540 is used to correct hydrocarbon densities from flowing
conditions to base conditions. The method classifies hydrocarbon liquids
into broad categories for its correlation, including crude oil,
gasoline/naphtha, jet fuel/kerosene, diesel/fuel oil, and lubricating
oils. Units for the API correlation are: Fahrenheit (F) for temperature,
pounds per square inch (psia) for pressure, and kilograms per cubic
meter (kg/m\*\*3) for density. Hydrocarbon densities are compared to
water density at 60F, which has an accepted density of 999.016 kg/m3.
Temperature and base density should be on an IPTS-68 basis, although
this has a very small effect.
$$\rho_{flowing} = \rho_{base} * C_{TL} * C_{PL}$$

$C_{TL}$ is a temperature correction factor. Note that $T_b$ =
60.0068749 F, and $\delta$ = 0.01374979547.
$$C_{TL} = \exp{\{-\alpha\Delta t [1+0.8\alpha((T_{f}-T_{b}) + 0.01374979547)]\}}$$

$$\alpha = \frac{K_0}{\rho^2} + \frac{K_1}{\rho} + K_2$$

|                  	| Density Range                             	| $K_0$     	| $K_1$   	| $K_2$       	|
|------------------	|-------------------------------------------	|-----------	|---------	|-------------	|
| Crude Oil        	| 610.6 $\leq   \rho_{base} \leq$ 1163.5    	| 341.0957  	| 0       	| 0           	|
| Fuel Oils        	| 838.3127 $\leq \rho_{base} \leq$ 1163.5   	| 103.8720  	| 0.2701  	| 0           	|
| Jet Fuels        	| 787.5195 $\leq \rho_{base} \leq$ 838.3127 	| 330.3010  	| 0       	| 0           	|
| Transition Zone  	| 770.352 $\leq \rho_{base} \leq$ 787.5195  	| 1489.0670 	| 0       	| -0.00186840 	|
| Gasolines        	| 610.6 $\leq \rho_{base} \leq$ 770.352     	| 192.4571  	| 0.2438  	| 0           	|
| Lubricating Oils 	| 800.9 $\leq \rho_{base} \leq$ 1163.5      	| 0         	| 0.34878 	| 0           	|


$C_{PL}$ is a pressure correction factor, which is typically very
near 1.
$$C_{PL} = \frac{1}{1-\left(10^{-5}*\exp{\left(-1.9947 + 0.00013427*T_{f}+\frac{793920+2326*T_{f}}{\rho^2}\right)}*P_f\right)}$$

### LPG

Equation 2\... lol

## Gas Density Correction

Gas density can be corrected with a similar method to liquid density, as
gas density is proportional .

::: proposition
Vapor density correction factor (Ideal Gas)

$$F_{\rho} = \sqrt{\frac{T_{cal}}{T_{f}}}\sqrt{\frac{P_{f}}{P_{cal}}}\sqrt{\frac{SG_{cal}}{SG_{f}}}$$
Note: Temperature and pressure ratios must be on an absolute scale.
:::

## Orifice Thermal Expansion Correction

Orifice diameter measurements are made at 70F per ASME XXXX. For small
changes in temperature, and when orifice design calculations have
accounted appropriately for thermal expansion of the pipe and metal, no
thermal expansion factor needs to be applied.

# A return to first principles and literature

## The orifice flow equation

The general orifice flow equation, given in many texts and readily
available on Wikipedia, is outlined below.

::: principle
Orifice Flow Equation
$$q_m =  \frac{C_d}{\sqrt{1-\beta^4}}\epsilon\frac{\pi}{4}d^2 \sqrt{2 g_c \Delta p * \rho_1}$$
:::

Next, we will put this equation in terms of volumetric flow, which is
more applicable to refining, the $q_m$ must be divided by the flowing
fluid gravity $\rho_1$. We also multiply by
$\frac{\rho_{1}}{\rho_{base}}$ to get $q_v$ at standard conditions.

$$q_{v,std} = \frac{q_m}{\rho_1}$$

Together, this yields the orifice flow equation in volume terms.

::: proposition
Orifice Flow Equation, volume flow at standard conditions
$$q_{v, std} =  \frac{C_d}{\sqrt{1-\beta^4}}\epsilon\frac{\pi}{4}d^2 \sqrt{\frac{2 g_c \Delta p}{\rho_{1}}}*\frac{\rho_{1}}{\rho_{base}}$$
:::

## Discharge and Expansiblity Coefficients

### Discharge coefficient

The discharge coefficient, $C_d$, is given by the empirical
Reader-Harris/Gallager (1998) equation. It is a function of Reynold's
number calculated with respect to pipe inner diameter, D, and the
orifice and pressure tap geometry. Within 4:1 turndown, the coefficient
does not vary significantly, so can be assumed to be constant to
simplify flow correction. See figure 1 below.

![Error at 25% of max instrument range is less than 0.25% deviation from
true discharge coefficient.](img/figure1.png)

::: proposition
This is a proposition.
:::

::: principle
This is a principle.
:::

# Useful Geometry

## Pressure Taps

## Thermal Expansion of Orifice Plates

![Sydney, NSW](img/photo.jpg)

# Citations

This is a citation[@Eg].
<!--stackedit_data:
eyJwcm9wZXJ0aWVzIjoidGl0bGU6IEVMRU1FTlRBUlkgT1JJRk
lDRSBGTE9XIE1FQVNVUkVNRU5UXG5hdXRob3I6IExpYW0gQmVu
bmV0dFxuc3RhdHVzOiBkcmFmdFxuZGF0ZTogJzIwMjMtMTEtMD
cnXG4iLCJoaXN0b3J5IjpbLTE5MTUzNTkyNTEsNTUzNjI3MTA5
XX0=
-->