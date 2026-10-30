**$$S_i = \left(W_Q \cdot Q_i\right) + \left(W_L \cdot \frac{L_{min}}{L_i}\right) + \left(W_C \cdot \frac{C_{min}}{C_i}\right)$$

where $W_Q, W_L, W_C$ represent configurable organizational weights for Quality, Latency, and Cost respectively ($\sum W = 1.0$), $Q_i$ is the empirical benchmark quality index of model $i$, $L_i$ is its rolling P95 latency, and $C_i$ is its blended cost per token.
    
