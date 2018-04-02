# Flow Control and Measurement Cheat Sheet
Welcome to the first cheat sheet of CEE 4540! These documents will serve as guides and references for you throughout the semester. Since Professor Monroe's class time is limited, so too is the amount of material he can fit on the slides while ensuring that they remain understandable. Thus, these cheat sheets will supplement the powerpoints by going into further detail on the course concepts introduced in the slides.

**WRITE ABOUT THE STRUCTURE OF THE CHEAT SHEETS**   
**BUT FIRST COME UP WITH A STRUCTURE FOR THE CHEAT SHEETS**

---

## Table of contents
Please use this table to control/command find the sections you are looking for.

#### Section 1: Fluids Review
1.1) The Bernoulli and Energy Equations   
1.2) Minor and Major Losses
1.3) The Orifice Equation

---

## Section 1: Fluids Review
This section is meant to be a brief refresher on fluid mechanics. It will only cover the topics of fluids mechanics that will be used heavily in the course, and will not include derivations from first principles. Instead, derivations shown in this section and in all others will simply be manipulation of one or many equations to come up with a critical equation, which is oftentimes the basis for designing an AguaClara treatment process.

If you wish to review fluid mechanics in (much) more detail, please refer to [this guide](https://confluence.cornell.edu/display/cee4540/Fluids+Review+Guide "CEE 4540 Fluids Review"). If you wish to review from the textbook used in  CEE 3310, you can find a pdf [here](https://hellcareers.files.wordpress.com/2016/01/fluid-mechanics-seventh-edition-by-frank-m-white.pdf "CEE 3310 textbook").

### Important Terms
1. **Head**
2. **streamline**

### Important Equations
1. Bernoulli equation
2. Energy equation
3. Orifice equation

### 1.1) The Bernoulli and Energy Equations
#### The Bernoulli Equation
As explained in more detail than most of you wanted to know in CEE 3310, the Bernoulli and energy equations are incredibly useful in understanding the transfer of the fluid's energy across a control volume or throughout a streamline. This energy has three forms: pressure, potential (deriving from elevation), and kinetic (deriving from velocity). These three terms make up **the Bernoulli equation**:

$$\frac{p_1}{\gamma} + {z_1} + \frac{v_1^2}{2g} = \frac{p_2}{\gamma } + {z_2} + \frac{v_2^2}{2g}$$

Such that:  
$p$ = Pressure  
$\gamma = \rho_{fluid} \, g$ = Specific weight of fluid  
$g$ = Acceleration due to gravity  
$z$ = Elevation relative to a reference elevation
$v$ = velocity of water

Notice that each term in this form of the Bernoulli equation has units of length, even though the terms represent the energy of water. The energy of water described in units of length is called **head**. Thus, $\frac{p}{\gamma}$ is the pressure head, $z$ is the elevation head, and $\frac{v^2}{2g}$ is the velocity head. The following diagram shows these various forms of head via a 1 meter deep bucket (left) and a jet of water shooting out of the ground (right).

![Anyone getting this?](https://github.com/AguaClara/CEE4540_DC/blob/Flow_Control_and_Measurement/AguaClara%20Water%20Treatment%20Plant%20Design/Cheat%20Sheets/Images/Different%20forms%20of%20head.jpg)

#### Assumptions behind the Bernoulli equation
Unfortunately, the Bernoulli equation is an approximation and is therefore not applicable in all circumstances. The assumptions and conditions necessary to make the Bernoulli equation applicable are as follows:

1. Steady Flow. Bernoulli should not be used during periods in which the flow condition is changing, such as when turning a pump on or off, before the flow has equilibrated.
2. Incompressible flow. Meaning that the density of the fluid does not change throughout the control volume over which the Bernoulli equation is being applied.
3. Flow along a streamline. The Bernoulli equation applies to two or more varying positions of the *same parcel of water*. It is saying that the energy of this parcel is conserved throughout its flow path, and is simply being transferred between pressure, elevation, and velocity. The flow path of any given parcel of water is called its **streamline**. Since the Bernoulli equation compares two positions of the same parcel of water, it can only be applied at different points across that particle's streamline.
4. No energy gain or loss. The Bernoulli equation assumes that the energy of the parcel of water being followed is not changing. This means that there are negligible losses to friction (due to the assumption that the fluid is non-viscous), negligible changes in temperature, and no work being done on the fluid throughout the streamline.  

#### The Energy Equation
This 4th assumption stated above represents the key difference between the Bernoulli equation and the energy equation *for the purpose of this class*. **The energy equation** accounts for the loss of energy through conveyance of the fluid ($h_L$) and the charging of a turbine ($h_T$) as well as energy gain provided by a pump ($h_P$).

$$\frac{p_{1}}{\gamma} + z_{1} + \alpha_{1} \frac{V_{1}^2}{2g} + h_P = \frac{p_{2}}{\gamma} + z_{2} + {\alpha_{2}} \frac{V_{2}^2}{2g} + h_T + h_L$$

You'll also notice the two $\alpha$ terms attached to the velocity head. These are correction factors for kinetic energy, and will be neglected in this class. If you wish to learn more about the correction factors, [click here to sate your curiosity](http://nptel.ac.in/courses/105106114/pdfs/Unit6/6_1.pdf "Correction factor pdf"). Since AguaClara does not use pumps nor turbines, $h_P = h_T = 0$. With these simplifications, the energy equation can be written as follows:

$$\frac{p_{1}}{\gamma} + z_{1} + \frac{V_{1}^2}{2g} = \frac{p_{2}}{\gamma} + z_{2} + \frac{V_{2}^2}{2g} + h_L$$

This is the form of the energy equation that you will see over and over again in CEE 4540. To summarize, the main difference between the Bernoulli equation and the energy equation for the purposes of this class is energy loss. The energy equation accounts for the fluid's loss of energy over time while the Bernoulli equation does not. So how can the fluid lose energy?

### 1.2) Minor and Major Losses
Oh boy here we go

### 1.3) The Orifice Equation

$$Q = \Pi_{vc} A_{or} \sqrt{2g\Delta h}$$

This equation is one that you'll see again and again throughout this class. Thus, understanding where it comes from early on will be greatly beneficial in aiding your understanding of future concepts, derivations, and equations.

### Purpose
The orifice equation relates the flow out of an orifice, $Q$ to the height of the water above the orifice $\Delta h$.

![What does this text do again?](https://github.com/AguaClara/CEE4540_DC/blob/Flow_Control_and_Measurement/AguaClara%20Water%20Treatment%20Plant%20Design/Cheat%20Sheets/Images/Hole%20in%20a%20bucket.jpg)
