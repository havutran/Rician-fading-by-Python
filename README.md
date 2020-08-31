# Rician-fading

Below is the function to generate [Rician fading](https://en.wikipedia.org/wiki/Rician_fading) channels.

```
import numpy as np
```

```
#M is the number of transmitter's antennas
#N is the number of receiver' antennas
#dist is the distance between the transmitter and the receiver
#pl is path-loss exponent
#Kdb is the Rician factor in dB

def Rician_Fading_Channels(M,N,dist,pl, Kdb):  
    K = 10**(Kdb/10) #dB to mW
    mu = np.sqrt( K/((K+1))) #direct path
    s = np.sqrt( 1/(2*(K+1))) #scattered paths
    Hw = mu + s*(np.random.randn(M,N)+1j*np.random.randn(M,N)) #Rician channel
    H = np.sqrt(1/(dist**pl))*Hw  #Rician channel with pathloss  
    return H
```
