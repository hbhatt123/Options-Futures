# Options-Futures
Options Futures and Other Derivatives 8th eDITION

hello

# chapter 13.Wiener Process and Ito Lemma


 13.1 the markov property
___
a type of stochastic process,only time

 13.2 CONTINUOUS-TIME STOCHASTIC PROCESSES
___
Wiener Process(Brownian Motion)  
  u=0,v=1  
  one type of markov 
```python
import pandas as pd
import numpy as np
import statsmodels.api as sm
import scipy.stats as sci
import matplotlib.pyplot as plt

# dz = e * (dt**0.5)
T = 1000
dT = 1
k = dT**0.5
N = T/dT
port_er = []
port_dT = []
cer = 0
cdT = 0
for p in range(T):
    er = np.random.randn(1) # sigma*np.random.randn()+mu产生sigma&mu的分布
    cer = cer + er*k
    cdT = cdT + dT
    port_er.append(cer)
    port_dT.append(cdT)
port_er = np.array(port_er)
port_dT = np.array(port_dT)

plt.figure(figsize=(8, 4))  # 整体区域大小
plt.scatter(port_dT, port_er, c=port_er, marker='o')  # 按c分成不同的颜色，五颜六色；marker是点的类型，o是小圆圈
plt.grid(True)  # 网格
plt.xlabel('dT')  #累积时间,dT
plt.ylabel('Z') #累积Z,port_e
plt.colorbar(label='Z')
```
Generalized Wiener Process

dx = a*dt + b*dz
```python
T = 1000
dT = 1
k = dT**0.5
N = T/dT
port_er = []
port_dT = []
port_x =[]
port_y = []
cer = 0
cdT = 0
a = 0.03
b = 1.5
cx = 0
cy = 0
for p in range(T):
    er = np.random.randn(1) # sigma*np.random.randn()+mu产生sigma&mu的分布
    cer = cer + er*k
    cdT = cdT + dT
    cx = cx + a*dT + b*er*k
    cy = cy + a*dT
    port_er.append(cer)
    port_dT.append(cdT)
    port_x.append(cx)
    port_y.append(cy)

port_er = np.array(port_er)
port_dT = np.array(port_dT)
port_x = np.array(port_x)
port_y = np.array(port_y)

plt.figure(figsize=(8, 4))  # 整体区域大小
plt.scatter(port_dT, port_er, c=port_er, marker='o')  # 按c分成不同的颜色，五颜六色；marker是点的类型，o是小圆圈
plt.scatter(port_dT, port_x, c=port_er, marker='o')
plt.scatter(port_dT, port_y, c=port_er, marker='o')
plt.grid(True)  # 网格
plt.xlabel('dT')  #累积时间,dT
plt.ylabel('Z') #累积Z,port_e
plt.colorbar(label='Z')
```



ps.
1.
2.q world vs. p world
