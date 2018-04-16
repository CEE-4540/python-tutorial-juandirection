
# An Introduction to Coding

This tutorial will review coding basics for people who are new to coding. 


## Assigning Values

You can assign a variable a value or a list of values using the equal = sign. 

For example,


```
x = 9
```

You can make variable names more specific and use underscores _ to do this. This is different from a - sign, which Python recognizes as subtraction. 



```
x_new = 16
```

## Importing Modules
Periods are used to define the package from which you are pulling functions or information from. 

Packages store modules which are files that contain useful functions. 

One such file that we will use often is NumPy. This stands for Numbers in Python and it contains many functions that are helpful in doing math like the square root function, or converting a list of values to an array type. 

To be able to access the functions that are in NumPy, you will need to import numpy. 


```
import numpy as np
```

We import numpy as np so when we want to reference numpy again, we can just type "np" instead of "numpy" when we want to access functions inside numpy. Now, we can access functions within numpy. 

To find the square root of x, we can use the square root function. The square root function takes one input within parenthesis ( ), but other functions may take more inputs. 


```
sqrt_9 = np.sqrt(x)

```

## Printing

Once we set a variable to a certain value, we want to display it so it is useful and not only stored without being shown to the user. 

We can do this with a print function. Print functions can include strings (text) within parenthesis and can also include variable values by using either a comma , or a plus +. Sometimes you will have to convert a varaible to a string by using the str() function. 


```
print('The square root of 9 is '+str(sqrt_9))

print('The square root of 9 is', sqrt_9)
```

    The square root of 9 is 3.0
    The square root of 9 is 3.0
    

## aide_design

aide_design is the name of a package that we use in order to access important files concerning fluids functions and pipe diameters that will prove useful in solving design challenges. 

First, we will need to import aide_design, and from it, import files like physchem and units.


```
from aide_design import physchem as pc

from aide_design.units import unit_registry as u
```

### Units

The units file will allow us to add units to variables we create. You add units by multiplying units, called by u. with the variable or value. Let's use x_new from above. 


```
x_new_units = x_new * u.m

print(x_new_units)
```

    16 meter
    

I can covert these units through the .to function. 


```
x_new_units.to(u.mm)
```




16000.0 millimeter



### Physchem

Physchem contains many useful functions relating to hydraulics and fluids. One such function that is useful is the flow through an orifice, or a small hole. This function is called flow_orifice(Diam, Height, RatioVCOrifice) and it takes three inputs. The three inputs will be diameter, height of water, and a vena contracta ratio. 
- You can run a function using no units. Default SI units will be applied (m, m^3, s,...)
- You can run a function using any units you want. The function will convert the units for you. 
- You can run a function using previously defined variables as well as with direct values. 


```
flow_with_values = pc.flow_orifice(0.01, 1, 0.62)
print(flow_with_values)

flow_with_many_units = pc.flow_orifice (0.1 * u.inch, 0.001 * u.km, 0.62)
print(flow_with_many_units)

Diam = 5 * u.cm
Height = 1/8 * u.feet
flow_with_variables = pc.flow_orifice(Diam, Height, 0.62)
print(flow_with_variables)
```

    0.00021565369636983403 meter ** 3 / second
    1.3913113874996217e-05 meter ** 3 / second
    0.00105234805568273 meter ** 3 / second
    

### Significant Figures

In the last cell, many significant figures were printed out. This is ugly to look at so let's only print 3 significant figures. To do this, we will need one more module, utility, which contains a significant figures function. The significant figures function takes two inputs, the variable or value, and the number of significant figures to be displayed. 


```
from aide_design import utility as ut
```


```
print('The flow with 3 significant figures is '+ut.sig(flow_with_many_units,3))
```

    The flow with 3 significant figures is 1.39e-5 m³/s
    
