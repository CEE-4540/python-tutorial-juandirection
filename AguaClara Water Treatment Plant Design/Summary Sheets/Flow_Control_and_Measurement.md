# Flow Control and Measurement Summary Sheet
Welcome to the first summary sheet of CEE 4540! These documents will be guides and references for you throughout the semester. Since Professor Monroe's class time is limited, so too is the amount of material he can fit on the slides while ensuring that they remain understandable. Thus, these summary sheets will supplement the powerpoints by going into further detail on the course concepts introduced in the slides.

Equations, universal constants, and other helpful goodies can be found in the [aide_design repository on GitHub](https://github.com/AguaClara/aide_design/tree/master/aide_design "aide_design"). Most equations and constants you find in these summary sheets will already have been coded into aide_design, and will be shown here in the following format:  

Variable: `pc.gravity`  
Function: `pc.area_circle(DiamCircle)`.

The letters before the `.`, in this case `pc`, indicate the file within aide_design where the variable or function can be found. In the examples above, `pc.gravity` and `pc.area_circle(DiamCircle)` show that the variable `gravity` and function `area_circle(DiamCicle)` are located inside the physchem.py (`pc`) file. You are heavily, strongly, *tremendously* recommended to look up any aide_design equations you plan to use within in their aide_design file before using them. Each equation has comments describing what the specific conditions are to using it.

For the most part, [hyperlinks in these documents will contain supplementary information](http://likethis.com/ "This link does not go anywhere"). The information contained in the linked external sites is there in case you don't feel completely comfortable with a concept, but is not necessary to learn thoroughly and will not be tested.

<br>
<br>


---

<br>
<br>

## Table of Contents
Please use this table to control/command find the sections you are looking for.

#### **Section 1: Fluids Review**
**1.1)** The Bernoulli and Energy Equations  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - &nbsp;The Bernoulli Equation  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - &nbsp;The Energy Equation  
**1.2)** Head Loss  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - &nbsp;Minor losses  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - &nbsp;Major losses  
**1.3)** The Orifice Equation  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - &nbsp;Vena Contracta    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - &nbsp;Origin  
**1.4)** Section Review

#### **Section 2: Introduction to Flow Control: The Search for Constant Head**  
**2.1)** Tank with a valve  
**2.2)** Conventional Flow Control Devices  
**2.3)**


<br>
<br>


---

<br>
<br>

## Section 1: Fluids Review
This section is meant to be a brief refresher on fluid mechanics. It will only cover the topics of fluids mechanics that will be used heavily in the course.

If you wish to review fluid mechanics in (much) more detail, please refer to [this guide](https://confluence.cornell.edu/display/cee4540/Fluids+Review+Guide "CEE 4540 Fluids Review"). If you wish to review from the textbook used in  CEE 3310 the intro to fluid mechanics course at Cornell, you can find a pdf of the book [here](https://hellcareers.files.wordpress.com/2016/01/fluid-mechanics-seventh-edition-by-frank-m-white.pdf "CEE 3310 textbook").

### Important Terms
1. Head
2. Streamline
3. Head loss
4. Laminar
5. Turbulent
6. Moody Diagram
7. Viscosity
8. Vena Contracta/Coefficient of Contraction

### Important Equations
1. Bernoulli equation
2. Energy equation
3. Darcy-Weisbach equation
4. Reynolds number
5. Swamee-Jain equation
6. Hagen-Poiseuille equation
7. Orifice equation

## 1.1) The Bernoulli and Energy Equations
### The Bernoulli Equation
As explained in CEE 3310 with more details than most of you wanted to know, the Bernoulli and energy equations are incredibly useful in understanding the transfer of the fluid's energy throughout a [streamline](https://en.wikipedia.org/wiki/Streamlines,_streaklines,_and_pathlines "Streamline wikipedia") or through a control volume. This energy has three forms: pressure, potential (deriving from elevation), and kinetic (deriving from velocity). These three forms make up the Bernoulli equation:

$$\frac{p_1}{\rho g} + {z_1} + \frac{V_1^2}{2g} = \frac{p_2}{\rho g} + {z_2} + \frac{V_2^2}{2g}$$

Such that:  
$p$ = pressure,  $\frac{[M]}{[L] \cdot [T]^2}$  
$\rho$ = fluid density, $\frac{[M]}{[L]^3}$    
$g$ = acceleration due to gravity,  $\frac{[L]}{[T]^2}$, in aide_design as `pc.gravity`  
$z$ = elevation relative to a reference, $[L]$  
$V$ = fluid velocity, $\frac{[L]}{[T]}$  

Notice that each term in this form of the Bernoulli equation has units of $[L]$ (length), even though the terms represent the energy of water, which has units of $\frac{[M] \cdot [L]^2}{[T]^2}$. When energy of water is described in units of length, the term used is called **head**.

There are two important distinctions to keep in mind when using head to talk about energy. First is that head is dependent on the density of the fluid under consideration. Take mercury, for example, which is around 13.6 times more dense than water. 1 meter of mercury head is therefore equivalent to around 13.6 meters of water head. Second is that head is independent of the amount of fluid being considered, *as long as all the fluid is the same density*. Thus, raising 1 liter of water up by one meter and raising 100 liters of water up by one meter are both equivalent to giving the water 1 meter of water head, even though it requires 100 times more energy to raise the hundred liters than to raise the single liter. Since we are concerned mainly with water in this class, we will refer to 'water head' simply as 'head'.

Going back to the Bernoulli equation, the $\frac{p}{\rho g}$ term is called the pressure head, $z$ the elevation head, and $\frac{V^2}{2g}$ the velocity head. The following diagram shows these various forms of head via a 1 meter deep bucket (left) and a jet of water shooting out of the ground (right).


![Anyone getting this?](https://github.com/AguaClara/CEE4540_DC/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Summary%20Sheets/Images/Different%20forms%20of%20head.jpg?raw=true)


#### Assumption in using the Bernoulli equation  
Though there are [many assumptions needed to confirm that the Bernoulli equation can be used](https://en.wikipedia.org/wiki/Bernoulli%27s_principle#Incompressible_flow_equation "Bernoulli wikipedia"), the main one for the purpose of this class is that energy is not gained or lost through the streamline or control volume being considered. If we consider more precise fluid mechanics terminology, then "friction by viscous forces must be negligible." Energy can only be transferred among its three forms if this equation is to be used.

#### Example problems

[Here is a worksheet with very straightforward example problems using the Bernoulli equation.](https://www.teachengineering.org/content/cub_/lessons/cub_bernoulli/cub_bernoulli_lesson01_bepworksheetas_draft4_tedl_dwc.pdf "Bernoulli worksheet") Note that the solutions use the pressure-form of the Bernoulli equation. This form of the equation does not affect the solution it is used for.

### The Energy Equation
The assumption necessary to use the Bernoulli equation, which is stated above, represents the key difference between the Bernoulli equation and the energy equation for the purpose of this class. The energy equation accounts for the (L)oss of energy from both the fluid flowing, $h_L$, and the charging of a (T)urbine, $h_T$, as well as energy gain provided by a (P\)ump, $h_P$.

$$\frac{p_{1}}{\rho g} + z_{1} + \alpha_{1} \frac{V_{1}^2}{2g} + h_P = \frac{p_{2}}{\rho g} + z_{2} + {\alpha_{2}} \frac{V_{2}^2}{2g} + h_T + h_L$$

You'll also notice the two $\alpha$ terms attached to the velocity head. These are correction factors for kinetic energy, and will be neglected in this class. If you wish to learn more about the correction factors, [click here to sate your curiosity](http://nptel.ac.in/courses/105106114/pdfs/Unit6/6_1.pdf "Correction factor pdf"). Since AguaClara does not use pumps nor turbines, $h_P = h_T = 0$. With these simplifications, the energy equation can be written as follows:

$$\frac{p_{1}}{\rho g} + z_{1} + \frac{V_{1}^2}{2g} = \frac{p_{2}}{\rho g} + z_{2} + \frac{V_{2}^2}{2g} + h_L$$  

**This is the form of the energy equation that you will see over and over again in CEE 4540.** To summarize, the main difference between the Bernoulli equation and the energy equation for the purposes of this class is energy loss. The energy equation accounts for the fluid's loss of energy over time while the Bernoulli equation does not. So how can the fluid lose energy?

## 1.2) Head Loss
**Head (L)oss**, $h_L$ is a term that is ubiquitous in both this class and fluid mechanics in general. Its definition is exactly as it sounds: it refers to the loss of energy of a fluid as it flows through space. There are two components to head loss: major losses caused by pipe-fluid (f)riction, $h_{\rm{f}}$, and minor losses caused by fluid-fluid friction resulting from flow (e)xpansions, $h_e$, such that $h_L = h_{\rm{f}} + h_e$.

### Major Losses
These losses are the result of friction between the fluid and the surface over which the fluid is flowing. A force acting parallel to a surface is referred to as [shear](https://en.wikipedia.org/wiki/Shear_force "Shear wikipedia"). It can therefore be said that major losses are the result of shear between the fluid and the surface it's flowing over. To help in understanding  major losses, consider the following example: imagine, as you have so often in physics class, pushing a large box across the ground. Friction is what resists your efforts to push the box. The farther you push the box, the more energy you expend pushing against friction. The same is true for water moving through a pipe, where water is analogous to the box you want to move, the pipe is similar to the floor that provides the friction, and the major losses of the water through the pipe is analogous to the energy _**you**_ expend by pushing the box.

In this class, we will be dealing primarily with major losses in circular pipes, as opposed to channels or pipes with other geometries. Fortunately for us, Henry Darcy and Julius Weisbach came up with a handy equation to determine the major losses in a circular pipe _under both [**laminar**](https://en.wikipedia.org/wiki/Laminar_flow "Laminar flow wikipedia") and [**turbulent**](https://en.wikipedia.org/wiki/Turbulence "Turbulent flow wikipedia") flow conditions_. Their equation is logically but unoriginally named the [**Darcy-Weisbach equation**](https://en.wikipedia.org/wiki/Darcy%E2%80%93Weisbach_equation "Darcy-Weisbach wikipedia"):

$$h_{\rm{f}} \, = \, {\rm{f}} \frac{L}{D} \frac{V^2}{2g}$$

Substituting the continuity equation $Q = VA$ in the form of $V^2 = \frac{16Q^2}{\pi^2 D^4}$ gives another, equivalent form of Darcy-Weisbach which uses flow, $Q$, instead of velocity, $V$:

$$h_{\rm{f}} \, = \,{\rm{f}} \frac{8}{g \pi^2} \frac{LQ^2}{D^5}$$

Such that:  
$h_{\rm{f}}$ = major loss, $[L]$  
$\rm{f}$ = Darcy friction factor, dimensionless   
$L$ = pipe length, $[L]$  
$Q$ = pipe flow rate, $\frac{[L]^3}{[T]}$  
$D$ = pipe diameter, $[L]$  


**Function in aide_design:** `pc.headloss_fric(FlowRate, Diam, Length, Nu, PipeRough)` Returns only major losses. Works for both laminar and turbulent flow.

Darcy-Weisbach is wonderful because it applies to both laminar and turbulent flow regimes and contains relatively easy to measure variables. The one exception is the Darcy friction factor, $\rm{f}$. This parameter is an approximation for the magnitude of friction between the pipe walls and the fluid, and its value changes depending on the whether or not the flow is laminar or turbulent, and varies with the [**Reynolds number**](https://en.wikipedia.org/wiki/Reynolds_number "Reynolds number wikipedia"), $\rm{Re}$, in both regimes of flow. Recall that the Reynolds number is a dimensionless value used to quantify and distinguish laminar and turbulent flow. The equation for Reynolds number *in a circular pipe* is as follows (note that the length dimension used in the equation changes depending on the cross sectional area that the water is flowing through):

$${\rm{Re}}=\frac{4Q}{\pi D\nu} = \frac{\rho VD}{\mu} = \frac{VD}{\nu}$$

Where the three forms simply substitute $Q = V \frac{\pi D^2}{4}$ and $\nu = \frac{\mu}{\rho}$  

Such that:  
$Q$ = pipe flow rate, $\frac{[L]^3}{[T]}$  
$D$ = pipe diameter, $[L]$    
$V$ = fluid velocity $\frac{[L]}{[T]}$  
$\nu$ = fluid kinematic viscosity, $\frac{[L]^2}{[T]}$    
$\mu$ = fluid dynamic viscosity, $\frac{[M]}{[L][T]}$  

**Function in aide_design:** `pc.re_pipe(FlowRate, Diam, Nu)` Returns the Reynolds number *in a circular pipe*. Functions for finding the Reynolds number through other conduits and geometries can also be found in [physchem.py](https://github.com/AguaClara/aide_design/blob/master/aide_design/physchem.py) within aide_design.

[There is a transition between laminar and turbulent flow which is not yet well understood](https://en.wikipedia.org/wiki/Laminar%E2%80%93turbulent_transition "Transitional flow wikipedia"). To simplify this phenomenon and make it possible to code for laminar or turbulent flow, we will assume that the transition occurs at $\rm{Re}$ = 2100. The flow regime is assumed to be laminar below this value and turbulent above it. This variable is coded into aide_design as `pc.RE_TRANSITION_PIPE`.

For laminar flow, the friction factor can be determined from the following equation:

$${\rm{f}} = \frac{64}{\rm{Re}}$$

For turbulent flow, the friction factor is more difficult to determine. In this class, we will use the [Swamee-Jain equation](https://en.wikipedia.org/wiki/Darcy_friction_factor_formulae#Swamee%E2%80%93Jain_equation "Swamee-Jain wikipedia"):

$${\rm{f}} = \frac{0.25} {\left[ \log \left( \frac{\epsilon }{3.7D} + \frac{5.74}{{\rm Re}^{0.9}} \right) \right]^2}$$

Such that:  
$\epsilon$ = pipe roughness, $[L]$  
$D$ = pipe diameter, $[L]$

**Function in aide_design:** `pc.fric(FlowRate, Diam, Nu, PipeRough)` Returns $\rm{f}$ for laminar *or* turbulent flow. For laminar flow, use '0' for the `PipeRough` input.

The simplicity of the equation for $\rm{f}$ during laminar flow allows for substitutions to create a very useful, simplified equation for major losses during laminar flow. This simplification combines the Darcy-Weisbach equation, the equation for the Darcy friction factor during laminar flow, and the Reynold's number formula:

$$h_{\rm{f}} \, = \,{\rm{f}} \frac{8}{g \pi^2} \frac{LQ^2}{D^5}$$

$${\rm{f}} = \frac{64}{\rm{Re}}$$

$${\rm{Re}}=\frac{4Q}{\pi D\nu}$$

To form the **Hagen-Poiseuille equation** for major losses during laminar flow, and *only* during laminar flow:

$$h_{\rm{f}} = \frac{128\mu Q}{\rho g\pi D^4}$$

The significance of this equation lies in its relationship between $h_{\rm{f}}$ and $Q$. Hagen-Poiseuille shows that the terms are directly proportional ($h_{\rm{f}} \propto Q$) during laminar flow, while Darcy-Weisbach shows that $h_{\rm{f}}$ grows with the square of $Q$ during turbulent flow ($h_{\rm{f}} \propto Q^2$). As you will soon see, minor losses, $h_e$, will grow with the square of $Q$ in both laminar and turbulent flow. This has implications that will be discussed later, in the flow control section.

In 1944, Lewis Ferry Moody plotted a ridiculous amount of experimental data, gathered by many people, on the Darcy-Weisbach friction factor to create what we now call the [**Moody diagram**](https://en.wikipedia.org/wiki/Moody_chart "Moody wikipedia"). This diagram has the friction factor $\rm{f}$ on the left-hand y-axis, relative pipe roughness $\frac{\epsilon}{D}$ on the right-hand y-axis, and Reynolds number $\rm{Re}$ on the x-axis. The Moody diagram is an alternative to computational methods for finding $\rm{f}$.


![Moody doody](https://github.com/AguaClara/CEE4540_DC/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Summary%20Sheets/Images/Moody.jpg?raw=true)


### Minor Losses

Unfortunately, there is no simple 'pushing a box across the ground' example to explain minor losses. So instead, consider a [hydraulic jump](https://www.youtube.com/watch?v=5spXXZX55C8 "What an amazingly made video, but sorry for the 3310 PTSD"). In the video, you can see lots of turbulence and eddies in the transition region between the fast, shallow flow and the slow, deep flow. The high amount of mixing of the water in the transition region of the hydraulic jump results in significant friction *between water and water* (the measure of a fluid's resistance to internal, fluid-fluid friction is called [**viscosity**](https://en.wikipedia.org/wiki/Viscosity "Viscosity wikipedia")). This turbulent, eddy-induced, fluid-fluid friction results in minor losses, much like fluid-pipe friction results in major losses.

As is the case in a hydraulic jump, a flow expansion (from shallow flow to deep flow) creates the turbulent eddies that result in minor losses. This will be a recurring theme in throughout the course: _**minor losses are caused by flow expansions**_. Imagine a pipe fitting that connects a small diameter pipe to a large diameter one, as shown in the image below. The flow must expand to fill up the entire large diameter pipe. This expansion creates turbulent eddies near the union between the small and large pipes, and these eddies cause minor losses. You may already know the equation for minor losses, but understanding where it comes from is very important for effective AguaClara plant design. For this reason, you are strongly recommended to read through the full derivation, which can be found [here](https://github.com/AguaClara/CEE4540_DC/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Summary%20Sheets/Derivation_minor_loss_equation.md "Remember to check this link").

There are three forms of the minor loss equation that you will see in this class:

$$ {\rm{ \mathbf{First \, form:} }} \,\,\, h_e = \frac{\left( V_{in}  - V_{out} \right)^2}{2g}$$

$$ {\rm{ \mathbf{Second \, form:} }} \,\,\, h_e = \frac{V_{in}^2}{2g}{\left( {1 - \frac{A_{in}}{A_{out}}} \right)^2} = \,\,\, \frac{V_{in}^2}{2g} \mathbf{K_e}$$

$$ {\rm{ \mathbf{Third \, form:} }} \,\,\, h_e = \frac{V_{out}^2}{2g}{\left( {\frac{A_{out}}{A_{in}}} -1 \right)^2} = \,\,\,\, \frac{V_{out}^2}{2g} \mathbf{K_e^{'}}$$

Such that:  
$K_e, \,\, K_e^{'}$ = minor loss coefficients, dimensionless

**Function in aide_design:**    
`pc.headloss_exp_general(Vel, KMinor)` Returns $h_e$. Can be either the second or third form due to user input of both velocity and minor loss coefficient. It is up to the user to use consistent $V$ and $K_e$.    
`pc.headloss_exp(FlowRate, Diam, KMinor)` Returns $h_e$. Uses third form, $K_e^{'}$.  

The $in$ and $out$ subscripts in each of the three forms refer to the diagram that was used for the derivation:

![I really don't think anyone can read this](https://github.com/AguaClara/CEE4540_DC/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Summary%20Sheets/Images/Minor%20loss%20pipe.jpg?raw=true)

The second and third forms are the ones which you are probably most familiar with. The distinction between them, however, is critical. First, consider the magnitudes of $A_{in}$ and $A_{out}$. $A_{in}$ can never be larger than $A_{out}$, because the flow is expanding. When flow expands, the cross-sectional area it flows through must increase. As a result, both $\frac{A_{out}}{A_{in}} > 1$ and $\frac{A_{in}}{A_{out}} < 1$ must always be true. This means that $K_e$ can never be greater than 1, while $K_e^{'}$ technically has no upper limit.

If you have taken CEE 3310, you have seen tables of minor loss coefficients [like this one](https://www.engineeringtoolbox.com/minor-loss-coefficients-pipes-d_626.html "engineeringtoolbox is the best site ever"), and they almost all have coefficients greater than 1. This implies that these tables use the third form of the minor loss equation as we have defined it, where the velocity is $V_{out}$. There is a good reason for using the third form over the second one: $V_{out}$ is far easier to determine than $V_{in}$. Consider flow through a pipe elbow, as shown in the image below.

![What does this text do again?](https://github.com/AguaClara/CEE4540_DC/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Summary%20Sheets/Images/Minor%20loss%20elbow.jpg?raw=true)

In order to find $V_{out}$, we first need to know which point is $out$ and which point is $in$. A simple way to distinguish the two points is that $in$ occurs when the flow is most contracted, and $out$ occurs when the flow has fully expanded after that maximal contraction. Going on these guidelines, point 'B' above would be $in$, since it represents the most contracted flow in the elbow-pipe system. Therefore point 'C' would be $out$, as it is the point where the flow has fully expanded after its compression in 'B.'

$V_{out}$ is easy to determine because it is the velocity of the fluid as it flows through the entire area of the pipe. Thus, $V_{out}$ can be found with the continuity equation, since the flow through the pipe and its diameter are easy to measure, $V_{out} = \frac{4 Q}{\pi D^2}$. On the other hand, $V_{in}$ is difficult to find, as the area of the contracted flow is dependent on the exact geometry of the elbow. This is why the third form of the minor loss equation, as we have defined it, is the most common.

## 1.3) The Orifice Equation

This equation is one that you'll see again and again throughout this class. Understanding it now will be invaluable, as future concepts will use and build on this equation.

### Vena Contracta

Before describing the equation, we must first understand the concept of a [**vena contracta**](https://en.wikipedia.org/wiki/Vena_contracta "Vena Contracta wikipedia"). Refer to the image of flow through a pipe elbow above. The flow contracts as the fluid moves from point 'A' to point 'B.' This happens because the fluid can't make a sharp turn at the corner of the elbow. Instead, the streamline closest to the sharp turn makes a slow, gradual change in direction, as shown in the image. As a result of this gradual turn, the cross-sectional area the fluid is flowing through at point 'B' is less than the cross-sectional area it flows through at points 'A' and 'C'. Written as an equation, $A_{point \, B} < A_{point \, A} = A_{point \, C}$. The term 'vena contracta' describes the phenomenon of contracting flow due to streamlines being unable to make sharp turns. $\Pi_{vc}$ is a ratio between the flow area at the vena contracta, $A_{point \, B}$, which is when the flow is *maximally* contracted, and the flow area *before* the contraction, $A_{point \, A}$. In the image above, the equation for the vena contracta coefficient would be:

$$\Pi_{vc} = \frac{A_{point \, B}}{A_{point \, A}}$$  

Note that what this class calls $\Pi_{vc}$ is often referred to as a 'Coefficient of Contraction,' $C_c$, in other engineering courses and settings. When the most extreme turn a streamline must make is 90°, the value of the vena contracta coefficient is close to 0.62. This parameter is in aide_design as `pc.RATIO_VC_ORIFICE`. Though there are many vena contracta coefficient values for different geometries like different turn angles, or sharp vs smooth turns, we will only consider a sharp, 90° turn in this class.

_**A vena contracta coefficient is not a minor loss coefficient.**_ Though the equations for the two both involve contracted and non-contracted areas, these coefficients are not the same. Refer to the flow through a pipe elbow image above. The minor loss coefficient equation uses the areas of points 'B' and 'C,' while the vena contracta coefficient uses the areas of points 'A' and 'B.' Additionally, the equations to calculate the coefficients themselves are not the same. Confusing the two coefficients is common mistake that this paragraph will hopefully help you to avoid.


### Origin
The orifice equation is derived from the Bernoulli equation as applied to the red points in the following image:

![What does this text do again?](https://github.com/AguaClara/CEE4540_DC/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Summary%20Sheets/Images/Hole%20in%20a%20bucket.jpg?raw=true)

At point A, the pressure is atmospheric and the instantaneous velocity is negligible as the water level in the bucket drops slowly. At point B, the pressure is also atmospheric. We define the difference in elevations between the two points, $z_A - z_B$, to be $\Delta h$. With these simplifications ($p_A = V_A = p_B = 0$) and assumptions ($z_A - z_B = \Delta h$), the Bernoulli equation becomes:

$$\Delta h = \frac{V_B^2}{2g}$$

Substituting the continuity equation $Q = V A$ in the form of $V_B^2 = \frac{Q^2}{A_{vc}^2}$, the vena contracta coefficient in the form of $A_{vc} = \Pi_{vc} A_{or}$ yields:

$$\Delta h = \frac{Q^2}{2g \Pi_{vc}^2 A_{or}^2}$$

Which, rearranged to solve for Q gives **The Orifice Equation:**

$$Q = \Pi_{vc} A_{or} \sqrt{2g\Delta h}$$

Such that:  
$\Pi_{vc}$ = 0.62 = vena contracta coefficient, in aide_design as `pc.RATIO_VC_ORIFICE`  
$A_{or}$ = orifice area- NOT contracted flow area  
$\Delta h$ = elevation difference between orifice and water level

**Equations in aide_design:**  
`pc.flow_orifice(Diam, Height, RatioVCOrifice)` Returns flow through a horizontal orifice.  
`pc.flow_orifice_vert(Diam, Height, RatioVCOrifice)` Returns flow through a vertical orifice. The height parameter refers to height above the center of the orifice.

![What does this text do again?](https://github.com/AguaClara/CEE4540_DC/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Summary%20Sheets/Images/Vertical%20and%20Horizontal%20Orifices.jpg?raw=true)

There are two configurations for an orifice in the wall of a reservoir of water, horizontal and vertical, as the image above shows. The orifice equation shown in the previous section is for a horizontal orifice, but for a vertical orifice the equation requires integration to return the correct flow. You will explore this in the Flow Control and Measurement Design Challenge.

## 1.4) Section Summary
1. **Bernoulli vs energy equations:** The Bernoulli equation assumes that energy is conserved throughout a streamline or control volume. The Energy equation assumes that there is energy loss, or head loss $h_L$. This head loss is composed of major losses, $h_{\rm{f}}$, and minor losses, $h_e$.

2. **Major losses:** Defined as the energy loss due to shear between the walls of the pipe/flow conduit and the fluid. The Darcy-Weisbach equation is used to find major losses in both laminar and turbulent flow regimes. The equation for finding the Darcy friction factor, $\rm{f}$, changes depending on whether the flow is laminar or turbulent. The Moody diagram is a common graphical method for finding $\rm{f}$.

3. **Minor losses:** Defined as the energy loss due to the generation of turbulent eddies when flow expands. Once more: minor losses are caused by flow expansions. There are three forms of the minor loss equation, two of which look the same but use different coefficients ($K_e$ vs $K_e^{'}$) and velocities ($V_{in}$ vs $V_{out}$). Make sure the coefficient you select is consistent with the velocity you use.

4. **Major and minor losses vary with flow:** While it is generally important to know how increasing or decreasing flow will affect head loss, it is even more important for this class to understand exactly how flow will affect head loss. As the table below shows, head loss will always be proportional to flow squared during turbulent flow. During laminar flow, however, the exponent on $Q$ will be between 1 and 2 depending on the proportion of major to minor losses.

| Head loss scales with: | Major Losses | Minor Losses |
|:----------------------:|:------------:|:------------:|
|        Laminar         |     $Q$      |    $Q^2$     |
|       Turbulent        |    $Q^2$     |    $Q^2$     |

5. **Orifice equation and vena contractas:** The orifice equation is used to determine the flow out of an orifice given the elevation of water above the orifice. This equation introduces the concept of a vena contracta, which describes flow contraction due to the inability of streamlines to make sharp turns. The equation shows that the flow out of an orifice is proportional to the square root of the driving head, $Q \propto \sqrt{\Delta h}$

<br>
<br>


---

<br>
<br>

## Section 2: Introduction to Flow Control: The Search for Constant Head   

**Constant head** implies constant flow. It means that water is flowing, but the driving head of the system is not changing. In other words, imagine a bucket, full of water, with a hole in the bottom. The water will leave through the hole with a certain flow rate, and, as the water level in the bucket falls, that flow rate will decrease. Constant head means that the bucket is s


Scientists and fluid mechanicians have been searching for devices to provide a constant, continuous flow rate for most of history. Nowadays, programming and pumps have established an easy way to solve this age-old problem, as long as electricity is available. As a seasoned traveler or any humanitarian may tell you, however, consistent electricity is not available to a large portion of the world population. Those same people could also tell you that areas lacking consistent electricity also tend to lack other essential human resources, like consistent access to clean drinking water. A difficult, somewhat perverse challenge arises. The conventional solution to chlorinating and disinfecting incoming water involves programming and pumps, and therefore electricity. However, the places that most need their water disinfected don't have consistent access to electricity.

But what does constant flow rate have to do with [**chlorination**](https://en.wikipedia.org/wiki/Water_chlorination "Chlorination wikipedia")? The answer lies in the dose of chlorine, its ideal concentration in the water. Too much chlorine leads to unpleasant odor, taste, and is a skin irritant **WHAT ELSE DOES TOO MUCH CHLORINE DOO????**. Too little chlorine is ineffective in neutralizing harmful bacteria in the water supply, and may lead to increased levels of disease in the population served by the water supply. Finding the right dose is the key to chlorination, and maintaining that dose is critical to effective chlorination. Therefore, finding a way to consistently administer the ideal dose becomes incredibly important.

This section introduces the problem of creating constant flow rate without electricity and presents some historical solutions.

### Important Terms

1. Constant Head
2. Chlorination
3.

### Important Equations
1. s
2.

## 2.1) Tank with a Valve  
As evidenced by the orifice equation, a tank of water with a hole poked in the bottom or side does not provide constant flow. Why not? In the orifice equation, $Q = \Pi_{vc} A_{or} \sqrt{2g \Delta h}$, flow $Q$ is a function of the height of water above the orifice, $\Delta h$. Since the water drains from the hole over time, the height of water above the orifice necessarily changes. The first approach in the search for a constant flow rate is understanding the 'hole-in-a-bucket' system, as it is the most simple way to provide a flow of water. Our goal is to see if we can alter a component of the system to produce either constant or essentially constant head.

The system we are using to gain an understanding of this 'hole-in-a-bucket' scenario is shown below. In the image, a hypochlorite solution is slowly dripping and mixing with piped source water, thereby disinfecting it. The valve is almost closed to make sure that the hypochlorite solution drips instead of flows.

![What does this text do again?](https://github.com/AguaClara/CEE4540_DC/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Summary%20Sheets/Images/complete%20hypochlorinator.jpg?raw=true)

Shown  [here](https://github.com/AguaClara/CEE4540_DC/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Summary%20Sheets/Derivation_flow_through_simple_hypoclorinator.md "Hypochlorinator derivation"), the derivation yields the following equation:

$$ \frac{Q}{Q_0} = 1 - \frac{1}{2} \frac{t}{t_{Design}} \frac{h_{Tank}}{h_0}$$

Such that:  
$Q = Q(t)$ = flow of hypochlorite through valve at time $t$   
$t$ = elapsed time  
$t_{Design}$ = time it would take for tank to empty if flow stayed constant at $Q_0$, which it does not  
$h_{Tank}$ = elevation of water level with reference to tank bottom  
$h_0$ = elevation of water level with reference to the valve  
**Note:** While the derivation uses a hypochlorinator as an example, we will just consider a bucket of water from now on to avoid saying 'hypochlorite solution' instead of 'water'.

This equation has consistently been a source of confusion for students, and its nuances are thoroughly explained in the derivation. These nuances will be quickly summarized below:

- $t_{Design}$ is **NOT** the time it takes to drain the tank. It is the time that it _would_ take to drain the tank _if_ the flow rate at time $t = 0$, $Q_0$, were the flow rate for the entire time. $t_{Design}$ was used in the derivation to simplify the equation, which is why it exists. The actual time it takes to drain the tank lies somewhere between $t_{Design}$ and $2 \cdot t_{Design}$.
- $h_{Tank}$ is not the same as $h_{0}$. $h_{Tank}$ is the height of water level in the tank with reference to the tank bottom. $h_{0}$ is the water level in the tank with reference to the valve. Therefore, $h_{0} \geq h_{Tank}$ is true if the valve is located at or below the bottom of the tank. If the tank is elevated far above the valve, then the $h_{0} > > h_{Tank}$. If the valve is at the same elevation as the bottom of the tank, then $h_{0} = h_{Tank}$. Please refer to the image above to clarify $h_{0}$ and $h_{Tank}$. Also note that both $h_{Tank}$ and $h_{0}$ are not variables, they are constants which are defined by the initial state of the system, when the water just begins to flow.

You may have noticed that this is not a hole-in-a-bucket scenario, as there is a valve involved and therefore there are minor losses. If you would like, you may go through the derivation on your own, using the orifice equation instead of the minor loss equation for the first step. If you do so, you'll find that the equation remains almost the same, the only difference is that the $\frac{h_{Tank}}{h_0}$ term drops out for an orifice, as $h_{Tank} = h_0$.

Thanks to the derivation, we have an expression of flow out of the system as a function of time. To complete our understanding, we need another expression for water/solution level as a function of time. Fortunately, this is very easy to find. Both the orifice equation for the hole-in-a-bucket scenario and the minor loss equation for the hypochlorinator-valve scenario have flow that is proportional to the square root of the driving head, $Q \propto h$. We can use this proportionality to come up with an equation relating the height of the water to the flow of water:

$$\frac{Q}{Q_0} = \sqrt{\frac{h}{h_0}}$$

Substituting this equation back into $\frac{Q}{Q_0} = 1 - \frac{1}{2} \frac{t}{t_{Design}} \frac{h_{Tank}}{h_0}$, we obtain an equation relating height of water as a function of time.  

$$\frac{h}{h_0} = \left( 1 - \frac{1}{2} \frac{t}{t_{Design}} \frac{h_{Tank}}{h_0} \right)^2$$

Such that:  
$h$ = $h(t)$ elevation of water level with reference to the the valve.


```python
# import necessary items
from aide_design.play import*
import pandas as pd

#define constants
# h_0 being equal to h_Tank implies that the valve is on the same elevation as the bottom of the tank
points_time = 100
h_0 = 1 * u.m
h_Tank = 1 * u.m
time_design = 4 * u.day

time_vector = np.linspace(0,8,points_time) * u.day

def hypo_flow_normalized(time, time_design, h_Tank, h_0):
  Q_norm = 1 - 0.5 * (time/time_design) * (h_Tank/h_0)
  return Q_norm

def hypo_h_normalized(time, time_design):
  h_norm = (1 - 0.5 * (time/time_design))**2
  return h_norm


Q_norm = hypo_flow_normalized(time_vector, time_design, h_Tank, h_0)

h_norm = hypo_h_normalized(time_vector, time_design)

plt.plot(time_vector,Q_norm)
plt.plot(time_vector,h_norm)

plt.legend(['Normalized flow', 'Normalized water depth'])
plt.xlabel("Time (days)")
plt.ylabel("Normalized Ratio")
plt.show()


```

###
