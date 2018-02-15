# Equations from CEE 4540 slides
This file is a temporary storage place for the LaTeX equations used in 4540 slides. Once some progress is made and the equations can be divided into groups, a well-designed file structure will be made.

**Notes for LaTeX math in Atom text editor**
1. Differentiating velocity ($V$) from volume ($\rlap{-} V$) is done with the `rlap{-}` function before the `V`. Using two dashes inside `\rlap{}`, which is how MathType translates volume,  results in the text losing
2. Using an asterisk (I will refrain from using one here) in LaTeX equations causes the text coloring to become a bit wonky and quite purple. Instead, use `\ast` when working within the dollar signs that denote math equations.


# **Flocculation Design**
### Floc model for viscous dominated collisions
$$v_r \approx \Lambda G$$

$$pC^\ast = \frac{3}{2}\log \left( \frac{2}{3} \pi k\frac{d_{Clay}^2}{\Lambda_0^2} \bar Gt \alpha + 1 \right)$$

$$\bar Gt = \frac{3}{2} \frac{\left( \Lambda^2 - \Lambda_0^2 \right)}{k \pi d_{Clay}^2 \alpha }$$

$$\left( \frac{\varepsilon}{\nu} \right)^\frac{1}{2}$$


### Head Loss coefficient for a Baffle
$$h_e = \frac{V_{out}^2}{2g} \left( \frac{A_{out}}{A_{in}} - 1 \right)^2$$

$$K_e = \left( \frac{A_{out}}{A_{in}} - 1 \right)^2$$

$$K_e = \left( \frac{1}{\Pi_{VCBaffle}} - 1 \right)^2 = 2.56$$


### Simplify flocculator design by designing for high efficiency
$$\Pi_{\bar \epsilon}^{\epsilon_{Max}}  = \frac{\varepsilon_{Max}}{\bar \varepsilon}$$

$$\Pi_{\bar{\epsilon}}^{\epsilon_{Max}}$$
