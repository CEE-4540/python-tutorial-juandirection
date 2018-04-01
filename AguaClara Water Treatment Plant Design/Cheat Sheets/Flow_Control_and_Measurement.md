# Flow Control and Measurement Cheat Sheet
Welcome to the first cheat sheet of CEE 4540! These documents will serve as guides and references for you throughout the semester. Since Professor Monroe's class time is limited, so too is the amount of material he can fit on the slides while ensuring that they remain understandable. Thus, these cheat sheets will supplement the powerpoints by going into further detail on the course concepts introduced in the slides.

**WRITE ABOUT THE STRUCTURE OF THE CHEAT SHEETS**   
**BUT FIRST COME UP WITH A STRUCTURE FOR THE CHEAT SHEETS**

---

## Table of contents
Please use this table to control/command find the sections you are looking for.

#### Section 1: Fluids Review
1.1) The Bernoulli and Energy Equations   
1.2) The Orifice Equation

---

## Section 1: Fluids Review
This section is meant to be a brief refresher on fluid mechanics. It will only cover the topics of fluids mechanics that will be used heavily in the course, and will not include derivations from first principles. Instead, derivations shown in this section and in all others will simply be manipulation of one or many equations to come up with a critical equation, which is oftentimes the basis for designing an AguaClara treatment process.

If you wish to review fluid mechanics in more detail, please refer to [this guide](https://confluence.cornell.edu/display/cee4540/Fluids+Review+Guide "CEE 4540 Fluids Review"). If you wish to review from the fluids textbook from CEE 3310, you can find a pdf [here](https://hellcareers.files.wordpress.com/2016/01/fluid-mechanics-seventh-edition-by-frank-m-white.pdf "CEE 3310 textbook").

### 1.1) The Bernoulli and Energy Equations
As explained in more detail than most of you wanted to know in CEE 3310, the Bernoulli and energy equations are incredibly useful in understanding the transfer of the fluid's energy across a control volume. This energy has three forms: pressure, potential (deriving from elevation), and kinetic (deriving from velocity). These three terms make up the Bernoulli equation:

$$\frac{p_1}{\gamma} + {z_1} + \frac{v_1^2}{2g} = \frac{p_2}{\gamma } + {z_2} + \frac{v_2^2}{2g}$$

Such that:  
$p$ = Pressure  
$\gamma = \rho_{fluid} \, g$ = Specific weight of fluid  
$g$ = Acceleration due to gravity  
$z$ = Elevation relative to a reference elevation
$v$ = velocity of water

Notice that each term in this form of the Bernoulli equation has units of length, even though the terms represent the energy of water. The energy of water described in units of length is called **head**. Thus, $\frac{p}{\gamma}$ is the pressure head, $z$ is the elevation head, and $\frac{v^2}{2g}$ is the velocity head. The following diagram shows these various forms of head via a 1 meter deep bucket (left) and a jet of water shooting out of the ground (right).

![Anyone getting this?](https://github.com/AguaClara/CEE4540_DC/blob/Flow_Control_and_Measurement/AguaClara%20Water%20Treatment%20Plant%20Design/Cheat%20Sheets/Images/Different%20forms%20of%20head.jpg)

### 1.2) The Orifice Equation

$$Q = \Pi_{vc} A_{or} \sqrt{2g\Delta h}$$

This equation is one that you'll see again and again throughout this class. Thus, understanding where it comes from early on will be greatly beneficial in aiding your understanding of future concepts, derivations, and equations.

### Purpose
The orifice equation relates the flow out of an orifice, $Q$ to the height of the water above the orifice $\Delta h$.

![What does this text do again?](https://github.com/AguaClara/CEE4540_DC/blob/Flow_Control_and_Measurement/AguaClara%20Water%20Treatment%20Plant%20Design/Cheat%20Sheets/Images/Hole%20in%20a%20bucket.jpg)
