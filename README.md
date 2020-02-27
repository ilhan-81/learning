# learning
# My python trials
import pandas as pd
import matplotlib.pyplot as plt
import random
H0 = 0
H1 = 0
H2 = 0
table=pd.DataFrame(columns=['Trial','HH', 'HT or TH', 'TT'])
print("Let us observe how the percentages of possible outcomes change, when the number of trials increases!")
NumberOfTrials = int(input("How many trials do you want to run: "))
for x in range (1, NumberOfTrials):
  num1 =  random.random()
  num2 =  random.random()
  heads = 0
  if num1<0.5:
    heads = 1
  if num2<0.5:
    heads = heads+1
  if heads == 2:
    H2 = H2 + 1
  elif heads == 1:
    H1 = H1 + 1
  elif heads == 0:
    H0 = H0 + 1
  if num1<0.5 and num2<0.5:
    print('HH')
  elif num1<0.5:
    print('HT')
  elif num2<0.5:
    print('TH')
  else:
    print('TT')
  table.loc[x] = [x,H2/(H2+H1+H0),H1/(H2+H1+H0),H0/(H2+H1+H0)]
plt.plot(table['Trial'],table['HH'],c="#00441b",label='% HH')
plt.plot(table['Trial'],table['TT'],c="#cb181d",label='% TT')
plt.plot(table['Trial'],table['HT or TH'],c="#fd8d3c",label='% HT or TH')
plt.xlabel('Number of Trials')
plt.ylabel('Percentage of Outcomes')
plt.legend()
plt.show()
