in Two-layer network step

**output:**

    Testing initialization ... 
    Testing test-time forward pass ... 
    Testing training loss (no regularization)
    Running numeric gradient check with reg =  0.0
    W1 relative error: 1.22e-08
    W2 relative error: 3.17e-10
    b1 relative error: 6.19e-09
    b2 relative error: 4.33e-10
    Running numeric gradient check with reg =  0.7
    W1 relative error: 1.00e+00
    W2 relative error: 1.00e+00
    b1 relative error: 1.09e-09
    b2 relative error: 7.76e-10

**analysis:**

when reg is not equal to 0, dw1 and dw2 is computed incorrectly. the error is dependent on reg.

**reason:**

when computing loss , add L2 regularization.  as for dw2's and dw1's derivative, ignore it
