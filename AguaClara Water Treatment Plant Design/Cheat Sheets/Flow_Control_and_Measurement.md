# Flow Control and Measurement Cheat Sheet
Welcome to the first cheat sheet of CEE 4540! These documents will serve as guides and references for you throughout the semester. Since Professor Monroe's class time is limited, so too is the amount of material he can fit on the slides while ensuring that they remain understandable. Thus, these cheat sheets will supplement the powerpoints by going into further detail on the course concepts introduced in the slides.

Equations, universal constants, and other helpful goodies can be found in the [aide_design repository on GitHub](https://github.com/AguaClara/aide_design/tree/master/aide_design "aide_design"). Most equations and constants you find in these cheat sheets will already have been coded into aide_design, and will be shown here in the following format:  
Variable: `pc.gravity`  
Function: `pc.area_circle(DiamCircle)`.

The letters before the dot and actual variable or function call, in this case `pc`, indicate the file within aide_design where the variable or function can be found. Using the example above, `pc.gravity` and `pc.area_circle(DiamCircle)` indicates that the variable `gravity` and function `area_circle(DiamCicle)` are located inside the physchem.py (pc) file.  

**WRITE ABOUT THE STRUCTURE OF THE CHEAT SHEETS**   
**BUT FIRST COME UP WITH A STRUCTURE FOR THE CHEAT SHEETS**

---

## Table of Contents
Please use this table to control/command find the sections you are looking for.

#### Section 1: Fluids Review
1.1) The Bernoulli and Energy Equations   
1.2) Minor and Major Losses  
1.3) The Orifice Equation

---

## Section 1: Fluids Review
This section is meant to be a brief refresher on fluid mechanics. It will only cover the topics of fluids mechanics that will be used heavily in the course, and will not include derivations from first principles. Instead, derivations shown in this section and in all others will simply be manipulation of one or many equations to come up with a critical equation, which is oftentimes the basis for designing an AguaClara treatment process.

If you wish to review fluid mechanics in (much) more detail, please refer to [this guide](https://confluence.cornell.edu/display/cee4540/Fluids+Review+Guide "CEE 4540 Fluids Review"). If you wish to review from the textbook used in  CEE 3310, you can find a pdf of the book [here](https://hellcareers.files.wordpress.com/2016/01/fluid-mechanics-seventh-edition-by-frank-m-white.pdf "CEE 3310 textbook").

### Important Terms
1. Head
2. Streamline
3. Head loss
4. Laminar
5. Turbulent

### Important Equations
1. Bernoulli equation
2. Energy equation
3. Orifice equation
4. Darcy-Weisbach equation
5. Reynolds number

### 1.1) The Bernoulli and Energy Equations
#### The Bernoulli Equation
As explained in more detail than most of you wanted to know in CEE 3310, the Bernoulli and energy equations are incredibly useful in understanding the transfer of the fluid's energy across a control volume or throughout a streamline. This energy has three forms: pressure, potential (deriving from elevation), and kinetic (deriving from velocity). These three terms make up the Bernoulli equation:

$$\frac{P_1}{\rho g} + {z_1} + \frac{V_1^2}{2g} = \frac{P_2}{\rho g} + {z_2} + \frac{V_2^2}{2g}$$

Such that:  
$P$ = pressure,  $\frac{[M]}{[L] \cdot [T]^2}$  
$\rho$ = density of fluid, $\frac{[M]}{[L]^3}$    
$g$ = acceleration due to gravity,  $\frac{[L]}{[T]^2}$  
$z$ = elevation relative to a reference elevation, $[L]$  
$V$ = velocity of the fluid, $\frac{[L]}{[T]}$  

Notice that each term in this form of the Bernoulli equation has units of $[L]$ (length), even though the terms represent the energy of water, which has units of $\frac{[M] \cdot [L]^2}{[T]^2}$. The energy of water described in units of length is called **head**. Thus, $\frac{P}{\rho g}$ is called the pressure head, $z$ the elevation head, and $\frac{V^2}{2g}$ the velocity head. The following diagram shows these various forms of head via a 1 meter deep bucket (left) and a jet of water shooting out of the ground (right).

![Anyone getting this?](https://github.com/AguaClara/CEE4540_DC/blob/Flow_Control_and_Measurement/AguaClara%20Water%20Treatment%20Plant%20Design/Cheat%20Sheets/Images/Different%20forms%20of%20head.jpg)

There are two important distinctions to keep in mind when using head to talk about energy. First is that head is independent of volume. So raising 1 liter of water up by one meter and raising 100 liters of water up by one meter are both equivalent to giving the water 1 meter of head, even though it requires 100 times more energy to raise the hundred liters. Second is that head changes depending on the density of the fluid under consideration. Take mercury, for example, which is 13.6 times more dense than water. 1 meter of mercury head is equivalent to 13.6 meters of water head.

##### Assumptions behind the Bernoulli equation
Unfortunately, the Bernoulli equation is an approximation of reality and is therefore not applicable in all circumstances. The assumptions and conditions necessary to make the Bernoulli equation applicable are as follows:

1. Steady Flow. Bernoulli should not be used during periods in which the flow condition is changing, such as when turning a pump on or off, before the flow has equilibrated.
2. Incompressible flow. Meaning that the density of the fluid does not change throughout the streamline over which the Bernoulli equation is being applied.
3. Flow along a streamline. The Bernoulli equation applies to two or more varying positions of the *same parcel of water*. It is saying that the energy of this parcel is conserved throughout its flow path, and is simply being transferred between pressure, elevation, and velocity. The flow path of any given parcel of water is called its **streamline**. Since the Bernoulli equation compares two positions of the same parcel of water, it can only be applied at different points across that particle's streamline.
4. No energy gain or loss. The Bernoulli equation assumes that the energy of the parcel of water being followed is not changing. This means that there are negligible losses to friction (due to the assumption that viscosity may be ignored), negligible changes in temperature, and no work being done on the fluid throughout the streamline.  

##### Example problems
[Here is a worksheet with very straightforward example problems using the Bernoulli equation.](https://www.teachengineering.org/content/cub_/lessons/cub_bernoulli/cub_bernoulli_lesson01_bepworksheetas_draft4_tedl_dwc.pdf "Bernoulli worksheet") Note that the solutions use the pressure-form of the Bernoulli equation. This form of the equation does not affect the solution it is used for.

#### The Energy Equation
This 4th assumption stated above represents the key difference between the Bernoulli equation and the energy equation for the purpose of this class. The energy equation accounts for the loss of energy as the fluid flows ($h_L$) and the charging of a turbine ($h_T$) as well as energy gain provided by a pump ($h_P$).

$$\frac{P_{1}}{\rho g} + z_{1} + \alpha_{1} \frac{V_{1}^2}{2g} + h_P = \frac{P_{2}}{\rho g} + z_{2} + {\alpha_{2}} \frac{V_{2}^2}{2g} + h_T + h_L$$

You'll also notice the two $\alpha$ terms attached to the velocity head. These are correction factors for kinetic energy, and will be neglected in this class. If you wish to learn more about the correction factors, [click here to sate your curiosity](http://nptel.ac.in/courses/105106114/pdfs/Unit6/6_1.pdf "Correction factor pdf"). Since AguaClara does not use pumps nor turbines, $h_P = h_T = 0$. With these simplifications, the energy equation can be written as follows:

$$\frac{P_{1}}{\rho g} + z_{1} + \frac{V_{1}^2}{2g} = \frac{P_{2}}{\rho g} + z_{2} + \frac{V_{2}^2}{2g} + h_L$$

**This is the form of the energy equation that you will see over and over again in CEE 4540.** To summarize, the main difference between the Bernoulli equation and the energy equation for the purposes of this class is energy loss. The energy equation accounts for the fluid's loss of energy over time while the Bernoulli equation does not. So how can the fluid lose energy?

### 1.2) Head Loss
**Head loss** is a term that is ubiquitous in both this class and fluid mechanics in general. Its definition is exactly as it sounds: it refers to the loss of energy of a fluid as it flows through time and space. There are two head loss terms: major losses and minor losses.

#### Major Losses
These losses are the result of friction between the fluid and the surface over which the fluid is flowing. This surface can be a channel, the inside of a pipe or any surface that is parallel to the direction of flow. For the purposes of this class, we will only consider major losses in piping and tubing systems. Fortunately for us, Henry Darcy and Julius Weisbach came up with a handy equation to determine the major losses in a pipe *under and flow condition*. Their equation is logically but unoriginally named the [**Darcy-Weisbach equation**](https://en.wikipedia.org/wiki/Darcy%E2%80%93Weisbach_equation "Darcy-Weisbach wikipedia"):

$$h_{\rm{f}} \, = \, {\rm{f}} \frac{L}{D} \frac{V^2}{2g}$$

Substituting the continuity equation $Q = VA$ in the form of $V^2 = \frac{16Q^2}{\pi^2 D^4}$ gives another, equivalent form of Darcy-Weisbach:

$$h_{\rm{f}} \, = \,{\rm{f}} \frac{8}{g \pi^2} \frac{LQ^2}{D^5}$$

Such that:  
$h_f$ = major loss, $[L]$  
$\rm{f}$ = Darcy friction factor, dimensionless   
$L$ = length of the pipe, $[L]$  
$Q$ = flow rate through the pipe, $\frac{[L]^3}{[T]}$  
$D$ = diameter of the pipe, $[L]$  

**Function in aide_design:** `pc.headloss_fric(FlowRate, Diam, Length, Nu, PipeRough)` This function is only for major losses. It works for both laminar and turbulent flow.

This equation is wonderful for many reasons; it applies to both [**laminar**](https://en.wikipedia.org/wiki/Laminar_flow "Laminar flow wikipedia") and [**turbulent**](https://en.wikipedia.org/wiki/Turbulence "Turbulent flow wikipedia") flow regimes and contains relatively easy to measure variables. The one caveat is the Darcy friction factor, $\rm{f}$. This parameter is an approximation for the magnitude of friction between the pipe walls and the fluid, and its value changes depending on the whether or not the flow is laminar or turbulent, and varies with the [**Reynolds number**](https://en.wikipedia.org/wiki/Reynolds_number "Reynolds number wikipedia") ($\rm{Re}$) in both cases. Recall that the Reynolds number is a dimensionless value used to quantify and distinguish laminar and turbulent flow. The equation for Reynolds number *in a circular pipe* is as follows (recall that the length dimension used in the equation changes depending on the flow conduit):

$${\rm{Re}}=\frac{4Q}{\pi D\nu} = \frac{\rho VD}{\mu} = \frac{VD}{\nu}$$

Where the three forms simply substitute $Q = V \frac{\pi D^2}{4}$ and $\nu = \frac{\mu}{\rho}$  

Such that:  
$\nu$ = kinematic viscosity of the fluid  
$\mu$ = dynamic viscosity of the fluid  

**Function in aide_design:** `pc.re_pipe(FlowRate, Diam, Nu)` note that this function is only for the Reynolds number *in a pipe*. Functions for finding the Reynolds number through other conduits are also in aide_design.

There is a transition between laminar and turbulent flow which is not yet well understood. To simplify this phenomenon and make it possible to code for laminar or turbulent flow, we will assume that the transition Reynolds occurs at $\rm{Re}$ = 2100. The flow regime is assumed to be laminar below this value and turbulent above it. This variable is coded into aide_design as `pc.RE_TRANSITION_PIPE`.

For laminar flow, the friction factor can be determined from the following equation:

$${\rm{f}} = \frac{64}{\rm{Re}}$$

For turbulent flow, the friction factor is more difficult to determine. In this class, we will use the [Swamee-Jain equation](https://en.wikipedia.org/wiki/Darcy_friction_factor_formulae#Swamee%E2%80%93Jain_equation "Swamee-Jain wikipedia"):

$${\rm{f}} = \frac{0.25} {\left[ \log \left( \frac{\epsilon }{3.7D} + \frac{5.74}{{\rm Re}^{0.9}} \right) \right]^2}$$

Such that:  
$\epsilon$ = pipe roughness

**Function in aide_design:** `pc.fric(FlowRate, Diam, Nu, PipeRough)` returns $\rm{f}$ for laminar *or* turbulent flow. For laminar flow, input '0' for the `PipeRough` input.

#### Minor Losses



### 1.3) The Orifice Equation

$$Q = \Pi_{vc} A_{or} \sqrt{2g\Delta h}$$

This equation is one that you'll see again and again throughout this class. Thus, understanding where it comes from early on will be greatly beneficial in aiding your understanding of future concepts, derivations, and equations.

### Purpose
The orifice equation relates the flow out of an orifice, $Q$ to the height of the water above the orifice $\Delta h$.

![What does this text do again?](https://github.com/AguaClara/CEE4540_DC/blob/Flow_Control_and_Measurement/AguaClara%20Water%20Treatment%20Plant%20Design/Cheat%20Sheets/Images/Hole%20in%20a%20bucket.jpg)
