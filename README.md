EXP NO 2 : Fitting Poisson distribution
Aim :
To fit poisson distribution for the arrival of objects per minute from the feeder

Software required :
Python and Visual component tool

Theory:
The Poisson distribution is the discrete probability distribution of the number of events occurring in a given time period, given the average number of times the event occurs over that time period.

image

Conditions for Poisson Distribution:

An event can occur any number of times during a time period.
Events occur independently. I
The rate of occurrence is constant.
The probability of an event occurring is proportional to the length of the time period.
Procedure :
image

Experiment :
image

Program :
DEVELOPED BY : SREE NIVEDITAA SARAVANAN
REGISTER NO  : 212223230213
import numpy as np
import math
import scipy.stats
##### Constructing frequency distribution
L=[int(i) for i in input(). split()]
N=len(L);M=max(L)
X=list();f=list()
for i in range (M+1):
    c=0
    for j in range(N):
        if L[j]==i:
            c=c+1
    f.append(c)
    X.append(i)
print(X)
print(f)
#### Finding Probability distribution and Mean
sf=np.sum(f)
p=list()
for i in range(M+1):
    p.append(f[i]/sf)
mean=np.inner(X,p)
#### Fitting Poissson distribution
P=list();E=list(); xi=list()
print(" X P(X=x) Obs.Fr Exp.Fr xi")
print("------------------------")
for x in range(M+1):
    P.append(math.exp(-mean)*mean**x/math.factorial(x))

    E.append(P[x]*sf)
    xi.append((f[x]-E[x])**2/E[x])
    print("%2.2f %2.3f %4.2f %3.2f %3.2f"%
(x,P[x], f[x], E[x], xi[x]))
print("-----------------------")
####   Chi square test to test the Fit
cal_chi2_sq=np.sum(xi)
print("Calculated value of Chi square is %4.2f"%cal_chi2_sq)
table_chi2=scipy.stats.chi2.ppf(1-.01, df=M)
print("Table value of Chi square at 1  level is %4.2f"%table_chi2)
if cal_chi2_sq<table_chi2:
    print("The given data can be fitted in Poissson distribution at 1% LOS")
else:
    print("The given data cannot be fitted in Poisson distribution at 1% LOS")
Output :
image

Results
The Poisson distribution is fitted for the objects arrived from feeder per minute and the data is tested using Chi-square test.
