

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import os
```


```python
csvpath1 = os.path.join("raw_data","clinicaltrial_data.csv")
csvpath2 = os.path.join("raw_data","mouse_drug_data.csv")

trial_df = pd.read_csv(csvpath1)
drug_df = pd.read_csv(csvpath2)
```


```python
trial_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Mouse ID</th>
      <th>Timepoint</th>
      <th>Tumor Volume (mm3)</th>
      <th>Metastatic Sites</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>b128</td>
      <td>0</td>
      <td>45.0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>f932</td>
      <td>0</td>
      <td>45.0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>g107</td>
      <td>0</td>
      <td>45.0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>a457</td>
      <td>0</td>
      <td>45.0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>c819</td>
      <td>0</td>
      <td>45.0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
drug_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Mouse ID</th>
      <th>Drug</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>f234</td>
      <td>Stelasyn</td>
    </tr>
    <tr>
      <th>1</th>
      <td>x402</td>
      <td>Stelasyn</td>
    </tr>
    <tr>
      <th>2</th>
      <td>a492</td>
      <td>Stelasyn</td>
    </tr>
    <tr>
      <th>3</th>
      <td>w540</td>
      <td>Stelasyn</td>
    </tr>
    <tr>
      <th>4</th>
      <td>v764</td>
      <td>Stelasyn</td>
    </tr>
  </tbody>
</table>
</div>




```python
drug_df["Drug"].value_counts()
len(trial_df)
```




    1893




```python
#Merge tables to add Drug column
mice_df = trial_df.merge(drug_df, on="Mouse ID", how="outer")
mice_df.head(15)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Mouse ID</th>
      <th>Timepoint</th>
      <th>Tumor Volume (mm3)</th>
      <th>Metastatic Sites</th>
      <th>Drug</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>b128</td>
      <td>0</td>
      <td>45.000000</td>
      <td>0</td>
      <td>Capomulin</td>
    </tr>
    <tr>
      <th>1</th>
      <td>b128</td>
      <td>5</td>
      <td>45.651331</td>
      <td>0</td>
      <td>Capomulin</td>
    </tr>
    <tr>
      <th>2</th>
      <td>b128</td>
      <td>10</td>
      <td>43.270852</td>
      <td>0</td>
      <td>Capomulin</td>
    </tr>
    <tr>
      <th>3</th>
      <td>b128</td>
      <td>15</td>
      <td>43.784893</td>
      <td>0</td>
      <td>Capomulin</td>
    </tr>
    <tr>
      <th>4</th>
      <td>b128</td>
      <td>20</td>
      <td>42.731552</td>
      <td>0</td>
      <td>Capomulin</td>
    </tr>
    <tr>
      <th>5</th>
      <td>b128</td>
      <td>25</td>
      <td>43.262145</td>
      <td>1</td>
      <td>Capomulin</td>
    </tr>
    <tr>
      <th>6</th>
      <td>b128</td>
      <td>30</td>
      <td>40.605335</td>
      <td>1</td>
      <td>Capomulin</td>
    </tr>
    <tr>
      <th>7</th>
      <td>b128</td>
      <td>35</td>
      <td>37.967644</td>
      <td>1</td>
      <td>Capomulin</td>
    </tr>
    <tr>
      <th>8</th>
      <td>b128</td>
      <td>40</td>
      <td>38.379726</td>
      <td>2</td>
      <td>Capomulin</td>
    </tr>
    <tr>
      <th>9</th>
      <td>b128</td>
      <td>45</td>
      <td>38.982878</td>
      <td>2</td>
      <td>Capomulin</td>
    </tr>
    <tr>
      <th>10</th>
      <td>f932</td>
      <td>0</td>
      <td>45.000000</td>
      <td>0</td>
      <td>Ketapril</td>
    </tr>
    <tr>
      <th>11</th>
      <td>g107</td>
      <td>0</td>
      <td>45.000000</td>
      <td>0</td>
      <td>Ketapril</td>
    </tr>
    <tr>
      <th>12</th>
      <td>g107</td>
      <td>5</td>
      <td>48.791665</td>
      <td>0</td>
      <td>Ketapril</td>
    </tr>
    <tr>
      <th>13</th>
      <td>g107</td>
      <td>10</td>
      <td>53.435987</td>
      <td>0</td>
      <td>Ketapril</td>
    </tr>
    <tr>
      <th>14</th>
      <td>g107</td>
      <td>15</td>
      <td>58.135545</td>
      <td>0</td>
      <td>Ketapril</td>
    </tr>
  </tbody>
</table>
</div>



### Tumor Volume Over Time


```python
#Group by Drug and Timepoint to get Mean and Std. Error
mice_drug_group = mice_df.groupby(["Drug","Timepoint"])
mice_drug_avg = mice_drug_group.mean().reset_index()
mice_drug_se = mice_drug_group.sem().reset_index()
mice_drug_avg.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Drug</th>
      <th>Timepoint</th>
      <th>Tumor Volume (mm3)</th>
      <th>Metastatic Sites</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Capomulin</td>
      <td>0</td>
      <td>45.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Capomulin</td>
      <td>5</td>
      <td>44.266086</td>
      <td>0.160000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Capomulin</td>
      <td>10</td>
      <td>43.084291</td>
      <td>0.320000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Capomulin</td>
      <td>15</td>
      <td>42.064317</td>
      <td>0.375000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Capomulin</td>
      <td>20</td>
      <td>40.716325</td>
      <td>0.652174</td>
    </tr>
  </tbody>
</table>
</div>




```python
drug_list = list(set(mice_df["Drug"].values))
drug_list
```




    ['Propriva',
     'Capomulin',
     'Infubinol',
     'Stelasyn',
     'Ramicane',
     'Naftisol',
     'Ketapril',
     'Placebo',
     'Zoniferol',
     'Ceftamin']




```python
#Plot a line graph, scatter plot, and error bars for each drug
#Graph average tumor volume per timepoint
#Unique colors and markers per drug
plt.figure(figsize=[10,7])
markers=["o","x","+","*","d","s","v","^",(3,2,0),"p"]
for drug in drug_list:
    mice_drug_df = mice_drug_avg.loc[mice_drug_avg["Drug"]==drug]
    mice_drug_error = mice_drug_se.loc[mice_drug_avg["Drug"]==drug]
    plt.scatter(mice_drug_df["Timepoint"], mice_drug_df["Tumor Volume (mm3)"],label=drug,marker=markers.pop())
    a,=plt.plot(mice_drug_df["Timepoint"], mice_drug_df["Tumor Volume (mm3)"], ls="dashed",lw=1,alpha=0.5,label="")
    plt.errorbar(mice_drug_df["Timepoint"], mice_drug_df["Tumor Volume (mm3)"],
                 yerr=mice_drug_error["Tumor Volume (mm3)"],label=None,fmt=" ", elinewidth=1,alpha=0.6,
                capsize=2, ecolor=a.get_c())
    
plt.legend(loc="best",ncol=2,columnspacing=1,title="Drug",fontsize=12).get_title().set_fontsize(13)
plt.title("Tumor Growth During Treatment",fontsize=15)
plt.xlabel("Time (days)",fontsize=12)
plt.ylabel("Tumor Volume (mm3)",fontsize=12)
plt.grid(alpha=0.3)
plt.show()
```


![png](Pymaceuticals_files/Pymaceuticals_9_0.png)


### Metastatic Sites Over Time


```python
#Graph average Metstatic Sites per timepoint, same as above
plt.figure(figsize=[10,7])
markers=["o","x","+","*","d","s","v","^",(3,2,0),"p"]
for drug in drug_list:
    mice_drug_df = mice_drug_avg.loc[mice_drug_avg["Drug"]==drug]
    mice_drug_error = mice_drug_se.loc[mice_drug_avg["Drug"]==drug]
    plt.scatter(mice_drug_df["Timepoint"], mice_drug_df["Metastatic Sites"],label=drug,marker=markers.pop())
    a,=plt.plot(mice_drug_df["Timepoint"], mice_drug_df["Metastatic Sites"], ls="dashed",lw=1,alpha=0.5,label="")
    plt.errorbar(mice_drug_df["Timepoint"], mice_drug_df["Metastatic Sites"],
                 yerr=mice_drug_error["Metastatic Sites"],label=None,fmt=" ", elinewidth=1,alpha=0.6,
                capsize=2, ecolor=a.get_c())
    
plt.legend(loc="best",ncol=2,columnspacing=1,title="Drug",fontsize=12).get_title().set_fontsize(13)
plt.title("Metastatic Spread During Treatment",fontsize=15)
plt.xlabel("Time (days)",fontsize=12)
plt.ylabel("Number of Metastatic Sites",fontsize=12)
plt.grid(alpha=0.3)
plt.show()
```


![png](Pymaceuticals_files/Pymaceuticals_11_0.png)


### Survival Rates


```python
mice_drug_count = mice_drug_group.count()["Mouse ID"].reset_index()
mice_drug_count.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Drug</th>
      <th>Timepoint</th>
      <th>Mouse ID</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Capomulin</td>
      <td>0</td>
      <td>25</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Capomulin</td>
      <td>5</td>
      <td>25</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Capomulin</td>
      <td>10</td>
      <td>25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Capomulin</td>
      <td>15</td>
      <td>24</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Capomulin</td>
      <td>20</td>
      <td>23</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Plot count of mice per timepoint, same as above without error bars
plt.figure(figsize=[10,7])
markers=["o","x","+","*","d","s","v","^",(3,2,0),"p"]
for drug in drug_list:
    mice_drug_df = mice_drug_count.loc[mice_drug_avg["Drug"]==drug]
    plt.scatter(mice_drug_df["Timepoint"], mice_drug_df["Mouse ID"],label=drug,marker=markers.pop())
    plt.plot(mice_drug_df["Timepoint"], mice_drug_df["Mouse ID"], ls="dashed",lw=1,alpha=0.5,label="")

    
plt.legend(loc="best",ncol=2,columnspacing=1,title="Drug",fontsize=12).get_title().set_fontsize(13)
plt.title("Survival During Treatment",fontsize=15)
plt.xlabel("Time (days)",fontsize=12)
plt.ylabel("Number of Surviving Mice",fontsize=12)
plt.grid(alpha=0.3)
plt.yticks(np.arange(7,26,3))
plt.show()
```


![png](Pymaceuticals_files/Pymaceuticals_14_0.png)


### Summary


```python
#Calculate % Change in tumor (vol at 45 days/vol at 0 days)
changes = []
for drug in drug_list:
    mice_drug_df = mice_drug_avg.loc[mice_drug_avg["Drug"]==drug].reset_index()
    perc = (mice_drug_df["Tumor Volume (mm3)"][9]/mice_drug_df["Tumor Volume (mm3)"][0]-1)*100
    changes.append(perc)
x_axis = np.arange(len(changes))
```


```python
#Red or green based on + or - growth
def colorize(x):
    if x<0:
        return 'g'
    return 'r'

#Colors, value label positions, and values as percents
plt.figure(figsize=[12,6])
colors=[colorize(n) for n in changes]
valuepos=[n/abs(n)*4 for n in changes]
percs=['{:1.1f}%'.format(n) for n in changes]

#Bar graph, with value labels
plt.bar(x_axis,changes,color=colors,)
plt.xticks(x_axis, drug_list,fontsize=11)
plt.axhline(c="k",linewidth=1,alpha=0.2)
plt.grid(alpha=0.4)
for i in range(len(changes)):
    plt.text(i,valuepos[i],percs[i],color='white',horizontalalignment="center",verticalalignment="center",fontsize=11)

plt.title("Tumor Volume Change Over 45-Day Treatment", fontsize=15)
plt.ylabel("% Tumor Volume Change", fontsize=12)

plt.show()
```


![png](Pymaceuticals_files/Pymaceuticals_17_0.png)


### Three observable trends:

1) Capomulin and Ramicane are both highly effective in reducing tumor size and prolonging survival, while the other meds fare comparably with the placebo. We can say this in high confidence due to the very low error rates in our tumor growth data.

2) Metastatic spread rates were much more varied among the meds, with significant error rates, though Ramicane and Capomulin still performed best.

3) Propriva had even more deaths than the placebo. Ouch.

4) The generator gave us two g989's. This is pretty likely to happen by virtue of the birthday paradox, so you might want to throw in a cautionary "while" loop when populating mice_array.
