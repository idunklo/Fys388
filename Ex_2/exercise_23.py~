import numpy as np
import matplotlib.pyplot as plt 

T = 1000. #[ms]
h = 0.1 # timestep 
N = int(T/h+1)

R = 0.04E9 #[Ohm]
theta = 15.E-3 # [V]
tau_m = 10 # [ms] 

def V(I, noise = 0):

    t = np.arange(N)*h
    V = np.zeros(N)

    V[0] = 0 

    counter = 0

    for n in xrange(N-1):

        if V[n] >= theta:
            V[n+1] = 0
            counter += 1
            continue

        I_noise = np.random.ranf()*1E-10

        V[n+1] = V[n] + h/tau_m*(-V[n] + R * (I[n] + I_noise * noise))

    return V, t, counter 

def plotter(x,y):
    plt.plot(x,y)
    #plt.show()

#exercise 2.3

def ex_23():
    I = 400.E-12 # current 
    I = np.zeros(N)+I
    v, t, counter = V(I)
    plotter(t, v)

#ex_23()


#exercise 2.4

def ex_24():
    I = np.linspace(0,1000E-12,101)
    f = np.zeros(len(I))
    f_noise = np.zeros(len(I))
    
    for i in range(len(I)):
        c = np.zeros(N)+I[i]
        v, t, counter = V(c)
        f[i] = counter/T

        v_noise, t_noise, counter_noise = V(c, 1)
        f_noise[i] = counter_noise/T

    plotter(I, f)
    plotter(I, f_noise)
    plt.show()

ex_24()






