# Flow Control and Measurement Summary Sheet
Welcome to the first summary sheet of CEE 4540! These documents will serve as guides and references for you throughout the semester. Since Professor Monroe's class time is limited, so too is the amount of material he can fit on the slides while ensuring that they remain understandable. Thus, these summary sheets will supplement the powerpoints by going into further detail on the course concepts introduced in the slides.

Equations, universal constants, and other helpful goodies can be found in the [aide_design repository on GitHub](https://github.com/AguaClara/aide_design/tree/master/aide_design "aide_design"). Most equations and constants you find in these summary sheets will already have been coded into aide_design, and will be shown here in the following format:  

Variable: `pc.gravity`  
Function: `pc.area_circle(DiamCircle)`.

The letters before the `.` and actual variable or function call, in this case `pc`, indicate the file within aide_design where the variable or function can be found. In the examples above, `pc.gravity` and `pc.area_circle(DiamCircle)` show that the variable `gravity` and function `area_circle(DiamCicle)` are located inside the physchem.py (pc) file.  

Unless otherwise specified, [hyperlinks in these documents will be supplementary](http://likethis.com/ "This link does not go anywhere"). The information contained in the linked external sites is there in case you don't feel completely comfortable with a concept, but is not necessary to learn thoroughly and will not be tested.

**SHOULD I WRITE SOMETHING ABOUT THE STRUCTURE OF THE SUMMARY  SHEETS HERE? I'M STILL NOT EXACTLY SURE WHAT THE STRUCTURE SHOULD BE**

---

## Table of Contents
Please use this table to control/command find the sections you are looking for.

#### Section 1: Fluids Review
1.1) The Bernoulli and Energy Equations   
1.2) Minor and Major Losses  
1.3) The Orifice Equation

---

## Section 1: Fluids Review
This section is meant to be a brief refresher on fluid mechanics. It will only cover the topics of fluids mechanics that will be used heavily in the course, and will only include one derivation from first principles. Instead, derivations shown in this section and in all others will simply be algebraic manipulation of one or many equations to come up with a critical equation, which is oftentimes the basis for designing an AguaClara treatment process.

If you wish to review fluid mechanics in (much) more detail, please refer to [this guide](https://confluence.cornell.edu/display/cee4540/Fluids+Review+Guide "CEE 4540 Fluids Review"). If you wish to review from the textbook used in  CEE 3310, you can find a pdf of the book [here](https://hellcareers.files.wordpress.com/2016/01/fluid-mechanics-seventh-edition-by-frank-m-white.pdf "CEE 3310 textbook").

### Important Terms
1. Head
2. Streamline
3. Head loss
4. Laminar
5. Turbulent
6. Moody Diagram
7. Viscosity

### Important Equations
1. Bernoulli equation
2. Energy equation
3. Orifice equation
4. Darcy-Weisbach equation
5. Reynolds number
6. Swamee-Jain equation

### 1.1) The Bernoulli and Energy Equations
#### The Bernoulli Equation
As explained in CEE 3310 with more details than most of you wanted to know, the Bernoulli and energy equations are incredibly useful in understanding the transfer of the fluid's energy throughout a streamline or through a control volume. This energy has three forms: pressure, potential (deriving from elevation), and kinetic (deriving from velocity). These three forms make up the Bernoulli equation:

$$\frac{p_1}{\rho g} + {z_1} + \frac{V_1^2}{2g} = \frac{p_2}{\rho g} + {z_2} + \frac{V_2^2}{2g}$$

Such that:  
$p$ = pressure,  $\frac{[M]}{[L] \cdot [T]^2}$  
$\rho$ = fluid density, $\frac{[M]}{[L]^3}$    
$g$ = acceleration due to gravity,  $\frac{[L]}{[T]^2}$, in aide_design as `pc.gravity`  
$z$ = elevation relative to a reference, $[L]$  
$V$ = fluid velocity, $\frac{[L]}{[T]}$  

Notice that each term in this form of the Bernoulli equation has units of $[L]$ (length), even though the terms represent the energy of water, which has units of $\frac{[M] \cdot [L]^2}{[T]^2}$. When energy of water is described in units of length, the term used is called **head**.

There are two important distinctions to keep in mind when using head to talk about energy. First is that head is dependent on the density of the fluid under consideration. Take mercury, for example, which is around 13.6 times more dense than water. 1 meter of mercury head is therefore equivalent to around 13.6 meters of water head. Second is that head is independent of the amount of fluid being considered, *as long as all the fluid is the same density*. Thus, raising 1 liter of water up by one meter and raising 100 liters of water up by one meter are both equivalent to giving the water 1 meter of water head, even though it requires 100 times more energy to raise the hundred liters. Raising 50 liters of water mixed with 50 liters of mercury up by one meter is *not* equivalent to giving the fluid mixture 1 meter of water head, since mercury is more dense than water. Since we are concerned mainly with water in this class, we will refer to 'water head' simply as 'head'.

Going back to the Bernoulli equation, the $\frac{p}{\rho g}$ term is called the pressure head, $z$ the elevation head, and $\frac{V^2}{2g}$ the velocity head. The following diagram shows these various forms of head via a 1 meter deep bucket (left) and a jet of water shooting out of the ground (right).


![Anyone getting this?](https://github.com/AguaClara/CEE4540_DC/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Summary%20Sheets/Images/Different%20forms%20of%20head.jpg?raw=true)


##### **Assumptions behind the Bernoulli equation**
Unfortunately, the Bernoulli equation is an approximation of reality and is therefore not applicable in all circumstances. The assumptions and conditions necessary to make the Bernoulli equation applicable are as follows:

1. Steady Flow. Bernoulli should not be used during periods in which the flow condition is changing, such as when turning a pump on or off, before the flow has equilibrated.
2. Incompressible flow. Meaning that the density of the fluid does not change throughout the streamline over which the Bernoulli equation is being applied.
3. Flow along a streamline. The Bernoulli equation applies to two or more varying positions of the *same parcel of water*. It is saying that the energy of this parcel is conserved throughout its flow path, and is simply being transferred between pressure, elevation, and velocity. The flow path of any given parcel of water is called its [**streamline**](https://en.wikipedia.org/wiki/Streamlines,_streaklines,_and_pathlines "Streamline wikipedia"). Since the Bernoulli equation compares two positions of the same parcel of water, it can only be applied at different points across that particle's streamline.
4. No energy gain or loss. The Bernoulli equation assumes that the energy of the parcel of water being followed is not changing. This means that there are negligible losses to friction (due to the assumption that viscosity may be ignored), negligible changes in temperature, and no work being done on the fluid throughout the streamline.  

##### **Example problems**
[Here is a worksheet with very straightforward example problems using the Bernoulli equation.](https://www.teachengineering.org/content/cub_/lessons/cub_bernoulli/cub_bernoulli_lesson01_bepworksheetas_draft4_tedl_dwc.pdf "Bernoulli worksheet") Note that the solutions use the pressure-form of the Bernoulli equation. This form of the equation does not affect the solution it is used for.

#### The Energy Equation
This 4th assumption stated above represents the key difference between the Bernoulli equation and the energy equation for the purpose of this class. The energy equation accounts for the (L)oss of energy from both the fluid flowing, $h_L$, and the charging of a (T)urbine, $h_T$, as well as energy gain provided by a (P\)ump, $h_P$.

$$\frac{p_{1}}{\rho g} + z_{1} + \alpha_{1} \frac{V_{1}^2}{2g} + h_P = \frac{p_{2}}{\rho g} + z_{2} + {\alpha_{2}} \frac{V_{2}^2}{2g} + h_T + h_L$$

You'll also notice the two $\alpha$ terms attached to the velocity head. These are correction factors for kinetic energy, and will be neglected in this class. If you wish to learn more about the correction factors, [click here to sate your curiosity](http://nptel.ac.in/courses/105106114/pdfs/Unit6/6_1.pdf "Correction factor pdf"). Since AguaClara does not use pumps nor turbines, $h_P = h_T = 0$. With these simplifications, the energy equation can be written as follows:

$$\frac{p_{1}}{\rho g} + z_{1} + \frac{V_{1}^2}{2g} = \frac{p_{2}}{\rho g} + z_{2} + \frac{V_{2}^2}{2g} + h_L$$

**This is the form of the energy equation that you will see over and over again in CEE 4540.** To summarize, the main difference between the Bernoulli equation and the energy equation for the purposes of this class is energy loss. The energy equation accounts for the fluid's loss of energy over time while the Bernoulli equation does not. So how can the fluid lose energy?

### 1.2) Head Loss
**Head (L)oss**, $h_L$ is a term that is ubiquitous in both this class and fluid mechanics in general. Its definition is exactly as it sounds: it refers to the loss of energy of a fluid as it flows through time and space. There are two components to head loss: major losses caused by pipe-fluid (f)riction, $h_f$, and minor losses caused by flow (e)xpansions, $h_e$, such that $h_L = h_f + h_e$.

#### Major Losses
These losses are the result of friction between the fluid and the surface over which the fluid is flowing, defined as [shear](https://en.wikipedia.org/wiki/Shear_force "Shear wikipedia"). For the purposes of this class, we will only deal with major losses in pipes. However, it is helpful to consider the following example when trying to understand major losses: imagine, as you have so often in physics class, pushing a large box across the ground. Friction is what resists your efforts to push the box. The farther you push the box, the more energy you expend pushing against friction. The same is true for water moving through a pipe, where water is analogous to the box to be moved, the pipe is the floor that provides the friction, and the major losses of the water is analogous to the energy you expend pushing the box.

Fortunately for us, Henry Darcy and Julius Weisbach came up with a handy equation to determine the major losses in a pipe _under both [**laminar**](https://en.wikipedia.org/wiki/Laminar_flow "Laminar flow wikipedia") and [**turbulent**](https://en.wikipedia.org/wiki/Turbulence "Turbulent flow wikipedia") flow_. Their equation is logically but unoriginally named the [**Darcy-Weisbach equation**](https://en.wikipedia.org/wiki/Darcy%E2%80%93Weisbach_equation "Darcy-Weisbach wikipedia"):

$$h_{\rm{f}} \, = \, {\rm{f}} \frac{L}{D} \frac{V^2}{2g}$$

Going back to the example of pushing a box, $\rm{f}$ is analogous to the force of friction from the ground, $\frac{L}{D}$ is analogous to how far you push the box, and $\frac{V^2}{2g}$ is analogous to how fast you push the box.

Substituting the continuity equation $Q = VA$ in the form of $V^2 = \frac{16Q^2}{\pi^2 D^4}$ gives another, equivalent form of Darcy-Weisbach which uses flow, $Q$, instead of velocity, $V$:

$$h_{\rm{f}} \, = \,{\rm{f}} \frac{8}{g \pi^2} \frac{LQ^2}{D^5}$$

Such that:  
$h_f$ = major loss, $[L]$  
$\rm{f}$ = Darcy friction factor, dimensionless   
$L$ = pipe length, $[L]$  
$Q$ = pipe flow rate, $\frac{[L]^3}{[T]}$  
$D$ = pipe diameter, $[L]$  


**Function in aide_design:** `pc.headloss_fric(FlowRate, Diam, Length, Nu, PipeRough)` Returns only major losses. It works for both laminar and turbulent flow.

Darcy-Weisbach is wonderful because it applies to both laminar and turbulent flow regimes and contains relatively easy to measure variables. The one caveat is the Darcy friction factor, $\rm{f}$. This parameter is an approximation for the magnitude of friction between the pipe walls and the fluid, and its value changes depending on the whether or not the flow is laminar or turbulent, and varies with the [**Reynolds number**](https://en.wikipedia.org/wiki/Reynolds_number "Reynolds number wikipedia"), $\rm{Re}$, in both regimes of flow. Recall that the Reynolds number is a dimensionless value used to quantify and distinguish laminar and turbulent flow. The equation for Reynolds number *in a circular pipe* is as follows (recall that the length dimension used in the equation changes depending on the cross sectional area that the water is flowing through):

$${\rm{Re}}=\frac{4Q}{\pi D\nu} = \frac{\rho VD}{\mu} = \frac{VD}{\nu}$$

Where the three forms simply substitute $Q = V \frac{\pi D^2}{4}$ and $\nu = \frac{\mu}{\rho}$  

Such that:  
$Q$ = pipe flow rate, $\frac{[L]^3}{[T]}$  
$D$ = pipe diameter, $[L]$    
$V$ = fluid velocity $\frac{[L]}{[T]}$  
$\nu$ = fluid kinematic viscosity, $\frac{[L]^2}{[T]}$    
$\mu$ = fluid dynamic viscosity, $\frac{[M]}{[L][T]}$  

**Function in aide_design:** `pc.re_pipe(FlowRate, Diam, Nu)` Returns the Reynolds number *in a circular pipe*. Functions for finding the Reynolds number through other conduits and geometries can also be found in physchem.py within aide_design.

[There is a transition between laminar and turbulent flow which is not yet well understood](https://en.wikipedia.org/wiki/Laminar%E2%80%93turbulent_transition "Transitional flow wikipedia"). To simplify this phenomenon and make it possible to code for laminar or turbulent flow, we will assume that the transition Reynolds occurs at $\rm{Re}$ = 2100. The flow regime is assumed to be laminar below this value and turbulent above it. This variable is coded into aide_design as `pc.RE_TRANSITION_PIPE`.

For laminar flow, the friction factor can be determined from the following equation:

$${\rm{f}} = \frac{64}{\rm{Re}}$$

For turbulent flow, the friction factor is more difficult to determine. In this class, we will use the [Swamee-Jain equation](https://en.wikipedia.org/wiki/Darcy_friction_factor_formulae#Swamee%E2%80%93Jain_equation "Swamee-Jain wikipedia"):

$${\rm{f}} = \frac{0.25} {\left[ \log \left( \frac{\epsilon }{3.7D} + \frac{5.74}{{\rm Re}^{0.9}} \right) \right]^2}$$

Such that:  
$\epsilon$ = pipe roughness  
$D$ = pipe diameter

**Function in aide_design:** `pc.fric(FlowRate, Diam, Nu, PipeRough)` Returns $\rm{f}$ for laminar *or* turbulent flow. For laminar flow, use '0' for the `PipeRough` input.

In 1944, Lewis Ferry Moody plotted a ridiculous amount of experimental data, gathered by many people, on the Darcy-Weisbach friction factor to create what we now call the [**Moody diagram**](https://en.wikipedia.org/wiki/Moody_chart "Moody wikipedia"). This diagram has the friction factor $\rm{f}$ on the left-hand y-axis, relative pipe roughness $\frac{\epsilon}{D}$ on the right-hand y-axis, and Reynolds number $\rm{Re}$ on the x-axis. The Moody diagram is an alternative to computational methods for finding $\rm{f}$.


![Moody doody](https://github.com/AguaClara/CEE4540_DC/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Summary%20Sheets/Images/Moody.jpg?raw=true)


#### Minor Losses

Unfortunately, there is no simple 'box across the ground' example to explain minor losses. So instead, consider certain components of a [hydraulic jump](https://www.youtube.com/watch?v=5spXXZX55C8 "What an amazingly made video, but sorry for the 3310 PTSD"). In the video, you can see a great deal of turbulence and eddies in the transition region between the fast, shallow flow and the slow, deep flow. The vigorous mixing of the water in the transition region of the hydraulic jump results in a great deal of friction *between water and water* (the measure of a fluid's resistance to internal friction is called [**viscosity**](https://en.wikipedia.org/wiki/Viscosity "Viscosity wikipedia")). This turbulent eddy-induced internal friction results in minor losses, much like fluid-pipe friction results in major losses.

As is the case in a hydraulic jump, a flow expansion (from shallow flow to deep flow) creates the turbulent eddies that result in minor losses. This will be a recurring theme in throughout the course: _**minor losses are caused by flow expansions**_. Imagine a pipe fitting that connects a small diameter pipe to a large one. The flow must expand to fill up the entire large diameter pipe. This expansion creates turbulent eddies near the union between the small and large pipes, and these eddies cause minor losses. You may already know the equation for minor losses, but understanding its derivation is very important to correct AguaClara plant design. Thus, it will be derived again here with the energy equation, using the following image as reference.


![I really don't think anyone can read this](https://github.com/AguaClara/CEE4540_DC/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Summary%20Sheets/Images/Minor%20loss%20pipe.jpg?raw=true)


$$\frac{p_{in}}{\rho g} + {z_{in}} + \frac{V_{in}^2}{2g} = \frac{p_{out}}{\rho g} + z_{out} + \frac{V_{out}^2}{2g} + h_L$$

Since the elevations of the 'in' and 'out' references are the same, we can eliminate $z_{in}$ and $z_{out}$. As we are considering such a small length of pipe, we will neglect the major losses component of head loss. As such, $h_L = h_e$. The following three equations are all the same, simply rearranged to solve for $h_e$.

$$\frac{p_{in}}{\rho g} + \frac{V_{in}^2}{2g} = \frac{p_{out}}{\rho g} + \frac{V_{out}^2}{2g} + h_e$$

$$\frac{p_{in} - p_{out}}{\rho g} = \frac{V_{out}^2 - V_{in}^2}{2g} + h_e$$

$$h_e = \frac{p_{in} - p_{out}}{\rho g} + \frac{V_{in}^2 - V_{out}^2}{2g}$$

This last equation to determine $h_e$ has four variables, and we would like it to have as few as possible. Thus, we will invoke conservation of momentum in the horizontal direction across our control volume to remove some variables. The difference in momentum from the 'in' point to the 'out' point is result of the pressure difference between each end of the control volume. Note that we will be considering the pressure at the centroid of our control surfaces. We will neglect shear along the pipe walls.

$$M_{in \, x} + M_{out \, x} = F_{p_{in \, x}} + F_{p_{out \, x}}$$

Such that:  
$M_{in \, x}$ =

Recall that momentum, $M$, is mass times velocity, $m \, V$, for solid bodies. Since we consider water flowing through a pipe, there is not one singular mass. Instead, there is a mass flow rate, or a mass per time indicated by $\rho \, Q$. Applying the continuity equation $Q = V \, A$, we obtain the following equation for the momentum of a fluid flowing through a pipe, $M = \rho V^2 A$.





### 1.3) The Orifice Equation

$$Q = \Pi_{vc} A_{or} \sqrt{2g\Delta h}$$

This equation is one that you'll see again and again throughout this class. Thus, understanding where it comes from early on will be greatly beneficial in aiding your understanding of future concepts, derivations, and equations.

### Purpose
The orifice equation relates the flow out of an orifice, $Q$ to the height of the water above the orifice $\Delta h$.

![What does this text do again?](https://github.com/AguaClara/CEE4540_DC/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Summary%20Sheets/Images/Hole%20in%20a%20bucket.jpg?raw=true)
