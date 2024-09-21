# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Name : Divakar
### Register number : 212222240026
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
from statsmodels.datasets import get_rdataset

# Synthetic Monthly Temperature Data (Additive)
date_rng = pd.date_range(start='2010-01-01', end='2020-12-01', freq='MS')
temperature_data = np.sin(np.linspace(0, 24*np.pi, len(date_rng))) * 10 + 20 + np.random.normal(0, 2, len(date_rng))
df_temp = pd.DataFrame(date_rng, columns=['date'])
df_temp['temperature'] = temperature_data
df_temp.set_index('date', inplace=True)

# Decompose Temperature Data (Additive Model)
decomposition_temp = seasonal_decompose(df_temp['temperature'], model='additive')
decomposition_temp.plot()
plt.show()

# Airline Passengers Data (Multiplicative)
air_passengers = get_rdataset('AirPassengers').data
air_passengers['date'] = pd.date_range(start='1949-01', periods=len(air_passengers), freq='M')
air_passengers.set_index('date', inplace=True)

# Decompose Airline Passengers Data (Multiplicative Model)
decomposition_passengers = seasonal_decompose(air_passengers['value'], model='multiplicative')
decomposition_passengers.plot()
plt.show()
```



### OUTPUT:

PLOTTING THE DATA:

![download](https://github.com/user-attachments/assets/83c92519-7f23-4790-9364-6802d9bc9e78)
![download](https://github.com/user-attachments/assets/f8527c47-ddfd-4b79-8640-0eab406be911)




### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
