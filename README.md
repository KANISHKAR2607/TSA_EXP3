### Developed by : KANISHKAR M
### Register No.: 212222240044
### Date :

# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the pH level in Water quality

### ALGORITHM:

1. Import the necessary packages

2. Find the mean, variance and then implement normalization for the data.

3. Implement the correlation using necessary logic and obtain the results

4. Store the results in an array

5. Represent the result in graphical representation as given below.

### PROGRAM:

```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load the CSV file
file_path = '/content/waterquality.csv'
data = pd.read_csv(file_path)

# Extract the 'pH' data
pH_data = data['pH'].dropna().values

# Mean
data_mean = np.mean(pH_data)
print("Mean:", data_mean)

# Variance
data_var = np.var(pH_data)
print("Variance:", data_var)

# Normalized data
normalized_data = (pH_data - data_mean) / np.sqrt(data_var)

# Compute the autocorrelation function (ACF)
acf_result = np.correlate(normalized_data, normalized_data, mode='full')

# Take only the positive lags
acf_result = acf_result[len(acf_result)//2:]

# Plot the ACF
plt.figure(figsize=(10, 5))
plt.stem(acf_result[:36], use_line_collection=True)
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.title('Autocorrelation Function (ACF) of pH level')
plt.show()


```
### OUTPUT:

![image](https://github.com/user-attachments/assets/5f48cc0e-d715-45ae-bb22-076256d63d2f)

#### Autocorrelation Function (ACF) of Tank Losses

![image](https://github.com/user-attachments/assets/cf091e07-c35f-4501-abe9-f2f869c64d4e)

### RESULT:

#### Thus, The AutoCorrelation Function (ACF) of the data for the pH level in Water quality data is successfully executed.




